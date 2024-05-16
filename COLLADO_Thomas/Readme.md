# Auteur : Thomas COLLADO

# Journal d'activités

## Création de la machine virtuelle

Temps de réalisation : 30 minutes

Travaux réalisés :

- Configuration matérielle de la VM
- INstallation de l'OS Debian 12
- Partitionnement et formattage du disque

## Configuration réseau

Temps de réalisation : 15 minutes

Les adresses du serveurs sont :

- **SLAAC** : 2a03:5840:111:1024:be24:11ff:fe21:10df
- **Statique** : 2a03:5840:111:1024::33

## Enregistrement DNS

Voici le tebleau des enregistrements DNS

| DNS  | Ipv6 |Usage|
| ------------- | ------------- |-------------|
| global-vision.vm.cfai24.ajformation.fr  | 2a03:5840:111:1024:be24:11ff:fe21:10df  |SSH|
| global-vision.web.cfai24.ajformation.fr  | 2a03:5840:111:1024::33  |Site vitrine|
|global-vision.admin.cfai24.ajformation.fr|2a03:5840:111:1024::33|Site gestion|


## Configuration des utilisateurs / groupes 

Temps de réalisation : 10 minutes

Réalisation :

- Création des utilisateurs
- Création des groupes
- Ajouts des utilisateurs dans les bons groupe

| utilisateur  | mot de pass |
| ------------- | ------------- |
| webmaster | aiQu5eev | 
| gmitchell  | ohQuah4m |
| gmacpherson | omuof2Cu |

Les groupes suivants ont été crée :

* vitrine
* gestion
* clpr

## Installation des paquets

Temps de réalisation : 10 minutes

Installations des paquets suivants :

- openssh-server (Durant l'installation de l'OS)
- mariadb (Alternative OpenSource à MySQL)
- snmpd
- nginx (1.22.1)
- php 8.2
- build-essential

## Configuration de SSH

Temps de réalisation : 10 minutes

SSH à été configuré de sorte à écouter sur l'adressse IP en SLAC :

* 2a03:5840:111:1024:be24:11ff:fe21:10df

Les clés SSH ont été ajoutées à l'aide de la commande :

```bash
ssh-copy-id user@global-vision.vm.cfai24.ajformation.fr
```
Et ce pour chaque utilisateur, la clé demandé dans le TP à également été ajoutée dans le fichier authorized_keys de chaque utilisateur.

Liens du commit contenant le configuration SSH :

[Configuration SSHD](https://github.com/CFAI2024-CPLR/projet_web/commit/b58d5f72cc1d0e63992a2eb029fb33d521faec5f)

Configuration du config ssh client :

```bash
Host global-vision
	HostName global-vision.vm.cfai24.ajformation.fr
	User gmacpherson
```
La commande de connexion est :

```bash
ssh global-vision
```

## Installation des sites web

Temps de réalisation : 2h40 heure

Les tâches réalisée sont :

* Le changement de l'utilisateur avec lequel s'éxecute nginx. 

[Configuration de nginx](https://github.com/CFAI2024-CPLR/projet_web/commit/d43c66336069430bb91bf927e19fdc907ef9ab9c) 

* Installation de vtiger :

Pour vtiger il faut installer les library php suivantes : 

* php-imap
* php-curl
* php-xml

Il faut également crée une base de donnée pour vtiger :

```bash
sudo mysql -u root -p
CREATE DATABASE vtiger;
GRANT ALL ON vtiger.* TO 'vtiger'@'localhost' IDENTIFIED BY 'eiCoh3sha4';
FLUSH PRIVILEGES;
EXIT;
```
La configuration de nginx pour vtiger : [vtiger nginx](https://github.com/CFAI2024-CPLR/projet_web/commit/2ff38925388afc1a4bcd7af3fbaa4819c733ece3)

Et la configuration de vtiger : [vtiger config](https://github.com/CFAI2024-CPLR/projet_web/commit/842f0e663839bde7cf8f208266eaa91343649272)

id de connexion à vtiger :
user : admin
passwd : Thomas009

* Instllation de PicoCMS :

Voici les commandes utilisées pour l'installation de PicoCMS :

```bash
curl -sSL https://getcomposer.org/installer | php
php composer.phar create-project picocms/pico-composer pico
chown -R webmaster:vitrine /websites/vitrine
```

* [Changement de l'utilisateur exécutant le socker php](https://github.com/CFAI2024-CPLR/projet_web/commit/d735b1cbd9b07d07f17b16b4fc31c4cea164814f)

L'URL des sites web est :

* Gestion : http://global-vision.admin.cfai24.ajformation.fr/
* Vitrine : http://global-vision.web.cfai24.ajformation.fr/