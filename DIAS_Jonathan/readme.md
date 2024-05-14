# Documentation pour la Configuration de la Machine Rocky Linux

## Objectifs

1. Configurer deux adresses IPv6 fixes :
   - Une adresse automatique (SLAAC) pour le FQDN de la VM.
   - Une adresse manuelle pour les sites web.
2. Vérifier la connectivité IPv6.
3. Enregistrer les FQDN dans le DNS.
4. Créer la hiérarchie des dossiers avec les permissions appropriées.
5. Créer les utilisateurs et les groupes nécessaires.
6. Attribuer les utilisateurs aux groupes spécifiés.
7. Configurer les permissions des dossiers en fonction des utilisateurs et des groupes.
8. Configurer l'accès root et les privilèges sudo.

## Étapes de Configuration

### 1. Configurer les Adresses IPv6

#### 1.1 Activer IPv6 et Configurer SLAAC

1. Assurez-vous que `NetworkManager` est utilisé et que IPv6 est activé pour SLAAC :

   ```bash
   sudo nmcli connection modify ens18 ipv6.method auto
   ```

#### 1.2 Ajouter une Adresse IPv6 Manuelle

Choisissez une adresse IPv6 manuelle, dans mon cas, l'adresse sera : 2001:db8:1::1/64.

Ajoutez cette adresse IPv6 à la configuration de votre interface réseau :

```bash
sudo nmcli connection modify ens18 +ipv6.addresses 2001:db8:1::1/64
 ```
#### Appliquez les modifications :

```bash
    sudo nmcli connection up ens18
```
### 2. Vérifier la Connectivité IPv6

Vérifiez les adresses IPv6 configurées :

```bash
ip -6 addr show dev ens18
```

Ping une adresse IPv6 externe pour vérifier la connectivité :

```bash
ping6 google.com
```

Ping l'adresse IPv6 manuelle pour vérifier qu'elle est unique :

```bash
ping6 2001:db8:1::1
```

Utilisez nmap pour vérifier l'unicité de l'adresse IPv6 :

```bash
    sudo nmap -6 -sP 2001:db8:1::1
```

### 3. Configuration DNS

 Accédez à l'outil DNS à l'adresse http://ns1.cfai2024.ajformation.fr:5000/.
Créez les enregistrements suivants :
        customer-resource.vm.cfai24.ajformation.fr : pour l'accès SSH (utilisez l'adresse IPv6 automatique).
        customer-resource.web.cfai24.ajformation.fr : pour le site web vitrine (utilisez l'adresse IPv6 manuelle).
        customer-resource.admin.cfai24.ajformation.fr : pour le site web de gestion (utilisez l'adresse IPv6 manuelle).

### 4. Création de la Hiérarchie des Dossiers

    Créez les dossiers :

```bash
sudo mkdir -p /websites/vitrine
sudo mkdir -p /websites/gestion
```
L'extension "-p" permet de faire de créer le répertoire parent "Websites" puis le répertoire "Vitrine" ainsi que "Gestion".

    Définissez les propriétaires et groupes :

```bash
sudo chown -R nginx:clpr /websites
sudo chown -R webmaster:vitrine /websites/vitrine
sudo chown -R webmaster:gestion /websites/gestion
```
L'extension "-R" permet de faire une attribution de droit récursive .

    Définissez les permissions :

```bash
    sudo chmod -R 775 /websites
    sudo chmod -R 775 /websites/vitrine
    sudo chmod -R 775 /websites/gestion
```
Les chiffres "775" permet eux de définirs les droits ( Read Write Execute ).

### 5. Création des Utilisateurs et des Groupes
 5.1 Créer les Utilisateurs



```bash
sudo adduser webmaster
sudo adduser hrudolph
sudo adduser thall
```
5.2 Définissez les mots de passe pour les utilisateurs :

```bash
    sudo passwd webmaster
    sudo passwd hrudolph
    sudo passwd thall
```
5.3 Créer les Groupes

```bash
    sudo groupadd vitrine
    sudo groupadd gestion
    sudo groupadd clpr
```
5.4 Ajouter les Utilisateurs aux Groupes

Pour le groupe vitrine :

```bash
sudo usermod -aG vitrine webmaster
sudo usermod -aG vitrine jdias
sudo usermod -aG vitrine hrudolph
```

Pour le groupe gestion :

```bash
    sudo usermod -aG gestion webmaster
    sudo usermod -aG gestion jdias
    sudo usermod -aG gestion thall
```
### 6. Configuration des Permissions des Dossiers

    Vérifiez les permissions des dossiers :

```bash
    ls -ld /websites
    ls -ld /websites/vitrine
    ls -ld /websites/gestion
```