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
8. Attribuer un CMS par Site web en utilisant EspoCRM  ainsi que GetSimple

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

#### Ajoutez à présent la clé ssh nécessaire :

Il faut pour commencer se connecter à l'utilisateur concerné :
```bash
su  [nom_utilisateur]
```
Ensuite créer un directory qui va nous permettre de stocker la clé publique :
```bash
mkdir -p ~/.ssh
```
Ensuite donnez les droits nécessaires :
```bash
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```

Puis créer un fichier avec la clé à l'interieur :
```bash
vi ~/.ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDWsfbTbSlxcvxUL1286nwhwrDPJq6bctkxPpZ+TyujHrDwyymvqEjMJNxiwDPRoomPgOcg+YYUYXbfRiLp0VNlUqA5oG9nhlgtiryZrWY6zrywnsDOk6wJvWA/YNbWLlFN14OiKXOH5KJpgYQh1pLIw1TPeR56vU5wv1Ggb0Jr1sg14TJgm2M4lSmQs1CAY8hBLDj/qQcwVNtuYqTXOulwCPZAzhP6ncHM7lHbwJua/3bGQ8IeFzjRGjL0s2XVECYPufCbM0cX1VtmaSQdVmwqXGW2c+rPAq8cFHecfaw/0fdSMeNV4qSl+VqpCGn/XXnpWAYi0OfifddH80ffdAp5 /home/jerome/.ssh/id_rsa
```

### 6. Installation des GetSimple et EspoCMS
#### Téléchargez le paquet GetSimple :

```bash
cd /tmp
wget http://get-simple.info/latest
```

il faut à present unzip le paquet :

```bash
sudo dnf install unzip
unzip latest -d /tmp/get-simple
```

Déplacez le fichier dans votre répertoire vitrine :

```bash
sudo mv /tmp/get-simple/* /websites/vitrine
sudo chown -R apache:vitrine /websites/vitrine
sudo chmod -R 775 /websites/vitrine
```

#### Téléchargez le paquet EspoCRM

Allez dans le fichier /tmp pour une meilleure visibilité
```bash
cd /tmp
wget https://www.espocrm.com/downloads/EspoCRM-7.2.6.zip
unzip EspoCRM-7.2.6.zip -d /tmp/espocrm
```

Déplacez le fichier dans votre répertoire gestion :
```bash
sudo mv /tmp/espocrm/* /websites/gestion
sudo chown -R apache:apache /websites/gestion
sudo chmod -R 755 /websites/gestion
```

### 7. Configuration des Permissions des Dossiers

    Vérifiez les permissions des dossiers :

```bash
    ls -ld /websites
    ls -ld /websites/vitrine
    ls -ld /websites/gestion
```

### 7. Installer et Configurer Apache, PHP, et MySQL
#### 7.1 Installer Apache et PHP

```bash
sudo dnf update -y
sudo dnf install httpd php php-cli php-fpm php-mysqlnd php-pdo php-zip php-gd -y
```

#### 7.2 Configurer PHP-FPM

Ouvrez le fichier de configuration du pool PHP-FPM :

```bash
sudo nano /etc/php-fpm.d/www.conf
```

Ajoutez ou modifiez les lignes suivantes :

```plaintext
listen = /run/php-fpm/www.sock
listen.owner = apache
listen.group = apache
listen.mode = 0660
user = apache
group = apache
```
Redémarrez PHP-FPM et Apache :

```bash
sudo systemctl restart php-fpm
sudo systemctl restart httpd
```

#### 7.3 Configurer Apache pour les Sites Web
Virtual Host pour GetSimple CMS

Créez le fichier de configuration pour GetSimple CMS :

```bash
sudo nano /etc/httpd/conf.d/vitrine.conf
```
Ajoutez le contenu suivant :

### Apache
```bash
<VirtualHost *:80>
    <VirtualHost *:80>
    ServerName customer-resource.web.cfai24.ajformation.fr
    DocumentRoot /websites/vitrine/GetSimpleCMS-3.3.16

    <Directory /websites/vitrine/GetSimpleCMS-3.3.16>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    <FilesMatch \.php$>
        SetHandler "proxy:unix:/run/php-fpm/www.sock|fcgi://localhost"
    </FilesMatch>

    ErrorLog /var/log/httpd/vitrine_error.log
    CustomLog /var/log/httpd/vitrine_access.log combined
</VirtualHost>
```

Virtual Host pour EspoCRM

Créez le fichier de configuration pour EspoCRM :

```bash
sudo nano /etc/httpd/conf.d/gestion.conf
```
Ajoutez le contenu suivant :

```bash
<VirtualHost *:80>
    ServerName customer-resource.admin.cfai24.ajformation.fr
    DocumentRoot /websites/gestion/EspoCRM-7.2.6/

    <Directory /websites/gestion/EspoCRM-7.2.6>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    <FilesMatch \.php$>
        SetHandler "proxy:unix:/run/php-fpm/www.sock|fcgi://localhost"
    </FilesMatch>

    ErrorLog /var/log/httpd/gestion_error.log
    CustomLog /var/log/httpd/gestion_access.log combined
</VirtualHost>
```

Redémarrez Apache pour appliquer les modifications :

```bash
sudo systemctl restart httpd
```
### 8. Installer et Configurer MySQL
#### 8.1 Installer MySQL

```bash
sudo dnf install mysql-server -y
```

#### 8.2 Démarrer et sécuriser MySQL

```bash
sudo systemctl start mysqld
sudo systemctl enable mysqld
sudo mysql_secure_installation
```
#### 8.3 Créer une base de données et un utilisateur pour EspoCRM

Connectez-vous à MySQL en tant que root :

```bash
sudo mysql -u root -p
```
Exécutez les commandes SQL suivantes :

```sql
CREATE DATABASE espocrm;
CREATE USER 'espocrmuser'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON espocrm.* TO 'espocrmuser'@'localhost';
FLUSH PRIVILEGES;
```

### 9.configuration interface Web

Pour configurer l'interface web, vous devrez installer les dépendance php suivantes :

```bash
sudo dnf install php-mysqlnd php-pdo php-zip php-gd -y
```

Suivez les instructions à l'écran pour configurer EspoCRM, en utilisant les informations de la base de données que vous avez créées :

    Database Name: espocrm
    Username: espocrmuser
    Password: le mot de passe que vous avez défini
    Database Host: localhost

Ensuite, choisissez un mot de passe pour votre utilisateurs et tout est OK :)

Pour Get simple, aucun paramétrage n'est à faire, il suffit de faire du suivant suivant et le site est OK :)


### 10. Vérifier l'Installation
Créer un Fichier info.php pour Vérifier les Extensions PHP

Créez un fichier info.php pour vérifier les extensions PHP :

```bash
sudo nano /websites/vitrine/info.php
```
Ajoutez le contenu suivant :

```php
<?php
phpinfo();
?>
```

Puis pour verifier les sites, rendez vous sur les adresses suivantes :

http://customer-resource.admin.cfai24.ajformation.fr/

http://customer-resource.web.cfai24.ajformation.fr/

Si vous arrivez à acceder à vos sites, cela veut dire que tout est terminée !!!