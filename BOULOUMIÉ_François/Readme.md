# Rapport d'activité - Mission d'administration de machine virtuelle

## Introduction
Ce rapport détaille les étapes effectuées pour la préparation et l'administration d'une machine virtuelle destinée à l'entreprise "district-alignment". La mission comprenait la mise en place de deux sites web, la configuration réseau, la création d'utilisateurs et de groupes, l'installation de logiciels et de services, ainsi que la rédaction d'un rapport d'activité.

## Préparation de la machine virtuelle : 15 Min

### Caractéristiques de la machine virtuelle
- **Nom:** district-alignment-fbouloumie
- **Ressource Pool:** fbouloumie
- **Démarrage automatique:** Oui
- **ISO:** Rocky (latest)
- **Taille du disque:** 15Go
- **VCPU:** 2
- **RAM:** 2Go
- **Réseau:** 1 interface
- **Distribution Linux:** Rocky (latest) en mode terminal "Serveur"
- **FQDN:** district-alignment.vm.cfai24.ajformation.fr

### Partitionnement
- 1 partition primaire de 1GB montée sur / (ext4)
- 1 partition LVM de 10GB montée sur / (ext4)
- 1 partition LVM de 2GB montée sur swap
- 1 partition LVM restante montée sur /websites (xfs)

## Réseaux : 30 Min
- IPv6 automatique (SLAAC) pour le FQDN VM
- IPv6 manuelle personnalisée pour les sites web

``` 
sudo nmcli con mod ens18 ipv6.addresses "2a03:5840:111:1024:be24:11ff:fe37:9a0f/64, 2a03:5840:111:1024::58/"
``` 
Pour vérifier
```
ip a
``` 

## Hiérarchie des dossiers : 15 Min
- /websites/
- /websites/vitrine (propriétaire: webmaster, groupe: vitrine)
- /websites/gestion (propriétaire: webmaster, groupe: gestion)

## Création des dossiers 
``` 
sudo mkdir -p /websites/vitrine
sudo mkdir -p /websites/gestion 
```

## Création des groupes
```
sudo groupadd clpr
sudo groupadd vitrine
sudo groupadd gestion
```

## Ajout des droits 
```
sudo groupadd gestion
sudo chown apache:clpr /websites
sudo chown webmaster:vitrine /websites/vitrine
sudo chown webmaster:gestion /websites/gestion
```

### Utilisateurs et Administration : 20 Min
- **Compte administrateur:** fbouloumie (mot de passe fourni dans le rapport)
- **Comptes utilisateurs:** 
	- root ( mdp : root)
	- webmaster (mdp : webmaster)
	- sbonham (mdp : sbonham)
	- gcox (mdp : gcox)


## Création des utilisateurs
```
sudo useradd -r webmaster
sudo useradd -m -s /bin/bash sbonham -c "Sue Bonham"
sudo useradd -m -s /bin/bash gcox -c "Gregory Cox"
```

## Changement du mot de passe
```
sudo passwd [Nom d'utilisateur]
```
## Ajout des utilisateurs aux groupes
``` 
sudo usermod -a -G vitrine webmaster
sudo usermod -a -G gestion webmaster
sudo usermod -a -G gestion gcox
sudo usermod -a -G vitrine sbonham
sudo usermod -a -G gestion fbouloumie
sudo usermod -a -G vitrine fbouloumie
```

### Logiciels et services
- Serveur SSH
- Outils de compilation
- SNMP server
- Nginx
- MySQL
- PHP (dernière version)
```
sudo apt update && sudo apt install -y openssh-server build-essential snmpd nginx mysql-server php
```

## Sites web
- Site vitrine: Jekyll
- Site de gestion: YetiForce

## Jekkyl
Fichier de configuration nginx

```
server {
    listen [2a03:5840:111:1024::58]:80;
    server_name district-alignment.web.cfai24.ajformation.fr;

    access_log /var/log/nginx/jekyll-access.log;
    error_log /var/log/nginx/jekyll-error.log;

    root /websites/vitrine/_site/;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

### Sites web
Les deux sites web ont été installés avec succès dans les dossiers dédiés et sont fonctionnels.

## Connexions SSH

### Ajout clé SSH Mr Avond
```
su  [nom_utilisateur]
mkdir -p ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
vi ~/.ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDWsfbTbSlxcvxUL1286nwhwrDPJq6bctkxPpZ+TyujHrDwyymvqEjMJNxiwDPRoomPgOcg+YYUYXbfRiLp0VNlUqA5oG9nhlgtiryZrWY6zrywnsDOk6wJvWA/YNbWLlFN14OiKXOH5KJpgYQh1pLIw1TPeR56vU5wv1Ggb0Jr1sg14TJgm2M4lSmQs1CAY8hBLDj/qQcwVNtuYqTXOulwCPZAzhP6ncHM7lHbwJua/3bGQ8IeFzjRGjL0s2XVECYPufCbM0cX1VtmaSQdVmwqXGW2c+rPAq8cFHecfaw/0fdSMeNV4qSl+VqpCGn/XXnpWAYi0OfifddH80ffdAp5 /home/jerome/.ssh/id_rsa
```
Décommenter la ligne 45 #PubkeyAuthentication ye
```
sudo nano /etc/ssh/sshd_config
```
## Résultats

Les connexions SSH sont opérationnelles pour tous les utilisateurs créés.

Les deux sites web ont été installés avec succès dans les dossiers dédiés et sont fonctionnels.

## Conclusion
La machine virtuelle pour l'entreprise "district-alignment" a été préparée avec succès selon les spécifications fournies. Les sites web sont fonctionnels et les services nécessaires sont installés. Le rapport d'activité a été fourni dans les délais impartis.