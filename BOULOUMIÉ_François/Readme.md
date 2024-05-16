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
- **Compte administrateur:** fbouloumie (mot de passe fourni dans le administration.yaml)
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
sudo dnf update && sudo dnf install -y openssh-server build-essential snmpd nginx mysql-server php
```

## Sites web
- Site vitrine: Jekyll
- Site de gestion: YetiForce

## Jekkyl : 6H

### Installation de Jekyll sur Rocky Linux avec Nginx comme Serveur Web

Récemment, j'ai mis en place un site Jekyll sur un serveur Rocky Linux, en utilisant Nginx comme serveur web. Voici les étapes que j'ai suivies :

#### Étape 1 : Mise à jour du Système

Tout d'abord, j'ai mis à jour le système pour m'assurer que tous les paquets étaient à jour :

```bash
sudo dnf update -y
```

#### Étape 2 : Installation de Ruby et des Dépendances

Jekyll nécessite Ruby, donc je l'ai installé ainsi que les dépendances nécessaires :

```bash
sudo dnf install -y ruby ruby-devel
```

#### Étape 3 : Installation de Node.js

Node.js est nécessaire pour certaines fonctionnalités de Jekyll, donc je l'ai également installé :

```bash
sudo dnf install -y nodejs
```

#### Étape 4 : Installation de Jekyll et Bundler

Ensuite, j'ai utilisé `gem` pour installer Jekyll et Bundler :

```bash
sudo gem install jekyll bundler
```

#### Étape 5 : Création d'un Nouveau Site Jekyll

J'ai créé un nouveau site Jekyll dans le répertoire souhaité :

```bash
cd /websites/vitrine
jekyll new .
```

#### Étape 6 : Construction du Site Jekyll

J'ai construit le site Jekyll pour générer les fichiers statiques :

```bash
bundle exec jekyll build
```

Les fichiers générés se trouvent dans le répertoire `_site`.

#### Étape 7 : Installation et Configuration de Nginx

J'ai installé Nginx :

```bash
sudo dnf install -y nginx
```

Puis, j'ai démarré et activé Nginx pour qu'il se lance au démarrage :

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

#### Étape 8 : Configuration de Nginx pour Servir le Site Jekyll

J'ai créé un fichier de configuration pour le site Jekyll :

```bash
sudo nano /etc/nginx/conf.d/jekyll.conf
```

J'y ai ajouté la configuration suivante :

```bash
server {
    listen [2a03:5840:111:1024::58]:80;
    server_name district-alignment.web.cfai24.ajformation.fr;

    access_log /var/log/nginx/jekyll-access.log
    error_log /var/log/nginx/jekyll-error.log;

    root /websites/vitrine/_site/;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

J'ai remplacé `/websites/vitrine/_site` par le chemin absolu vers le répertoire `_site`.

#### Étape 9 : Vérification de la Configuration Nginx

J'ai vérifié la syntaxe de la configuration :

```bash
sudo nginx -t
```

Tout était correct, donc j'ai rechargé Nginx :

```bash
sudo systemctl reload nginx
```

#### Étape 10 : Ouverture du Port 80 dans le Pare-feu

J'ai ouvert le port 80 pour permettre l'accès HTTP :

```bash
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload
```

Et ne surtout pas oublier cette commande pour SELinux
```bash
sudo chcon -R -t httpd_sys_content_t /websites/vitrine/_site
```
### Conclusion

Après ces étapes, mon site Jekyll était opérationnel sur Rocky Linux et servi par Nginx. J'ai pu y accéder en naviguant vers mon nom de domaine ou mon adresse IP dans un navigateur. Tout a fonctionné parfaitement.

## YetiForce : 4H

### Installation de YetiForce sur Rocky Linux avec Nginx

Récemment, j'ai entrepris l'installation de YetiForce, un CRM open-source, sur un serveur Rocky Linux avec Nginx. Voici comment j'ai procédé :

#### Étape 1 : Téléchargement de YetiForce

Tout d'abord, j'ai téléchargé le fichier .zip de YetiForce depuis le site officiel en utilisant `wget` :

```bash
wget -O YetiForceCRM.zip https://api.yetiforce.eu/download/crm/www/7.0.0-complete
```

Ensuite, j'ai extrait le contenu du fichier .zip dans le répertoire `/var/www/yetiforce` :

```bash
sudo mkdir -p /websites/gestion/
sudo unzip YetiForceCRM.zip -d /websites/gestion/
```

#### Étape 2 : Installation de MariaDB

Pour stocker les données de YetiForce, j'ai installé MariaDB :

```bash
sudo dnf install -y mariadb-server
sudo systemctl start mariadb
sudo systemctl enable mariadb
```

#### Étape 3 : Configuration de MariaDB

J'ai sécurisé l'installation de MariaDB et créé une base de données pour YetiForce :

```bash
sudo mysql_secure_installation
```

Ensuite, j'ai accédé à MariaDB pour créer la base de données et l'utilisateur :

```bash
sudo mysql -u root -p

CREATE DATABASE yetiforce;
CREATE USER 'yetiforceuser'@'localhost' IDENTIFIED BY 'Y3TIF0rC3';
GRANT ALL PRIVILEGES ON yetiforce.* TO 'yetiforceuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

#### Étape 4 : Installation de PHP et des Extensions Nécessaires

J'ai installé PHP-FPM et les extensions nécessaires pour YetiForce :

```bash
sudo dnf install -y php php-fpm php-mysqlnd php-xml php-mbstring php-zip php-gd php-curl php-soap php-intl
```

#### Étape 5 : Configuration de PHP-FPM

J'ai configuré PHP-FPM pour qu'il fonctionne avec Nginx :

```bash
sudo systemctl start php-fpm
sudo systemctl enable php-fpm
```

#### Étape 6 : Configuration de Nginx pour YetiForce

J'ai créé un fichier de configuration pour Nginx afin de servir YetiForce :

```bash
sudo nano /etc/nginx/conf.d/yetiforce.conf
```

Voici la configuration que j'ai ajoutée :

```bash
server {
    listen [2a03:5840:111:1024::58]:80;
    server_name district-alignment.admin.cfai24.ajformation.fr

    root /websites/gestion/;
    index index.php index.html index.htm;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        include /etc/nginx/fastcgi_params;
        fastcgi_pass unix:/run/php-fpm/www.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }

    location ~ /\.ht {
        deny all;
    }
}
```

#### Étape 7 : Vérification de la Configuration Nginx

J'ai vérifié la syntaxe de la configuration :

```bash
sudo nginx -t
```

#### Problème de Connexion PHP-FPM

Malheureusement, je n'ai pas réussi à connecter PHP-FPM dans le fichier de configuration Nginx. Lorsque j'essayais de recharger Nginx, j'obtenais une erreur indiquant que la connexion à PHP-FPM ne pouvait pas être établie.

Pour résoudre ce problème, j'ai vérifié les permissions et les configurations de socket, mais le problème persiste. Il semble que la configuration de PHP-FPM nécessite des ajustements supplémentaires que je n'ai pas encore identifiés.

### Conclusion

En résumé, j'ai pu télécharger et commencer l'installation de YetiForce, créer la base de données MariaDB, et configurer Nginx. Cependant, j'ai rencontré un problème de connexion avec PHP-FPM que je n'ai pas encore résolu.

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
Décommenter la ligne 45 #PubkeyAuthentication yes
```
sudo nano /etc/ssh/sshd_config
```
## Résultats

Les connexions SSH sont opérationnelles pour tous les utilisateurs créés.

Seul Jekkyl était fonctionnel et j'ai rencontré quelques problèmes avec YetiForce.

## Conclusion
La machine virtuelle pour l'entreprise "district-alignment" a été préparée avec succès selon les spécifications fournies. Seul Jekkyl est fonctionnel et les services nécessaires sont installés. Le rapport d'activité a été fourni dans les délais impartis.