# Identité

* Nom : EXTRAT
* Prénom : Florence

# Journal d'activité

## Mise en place de la machine virtuelle

* Temps de réalisation : 35 minutes
* Travaux :
    - Configuration physique de la machine
    - Installation de l'OS Rocky Linux 9.3
    - Partitionnement et formattage de la machine

## Configuration réseau IPv6
* Temps de réalisation : 15 minutes
* Travaux :
    - récupération de l'IP SLAAC
    - Test de la seconde IPv6 avec **nmap**
    - Ajout de la seconde IPv6 à la carte réseau
    - Redémarrage du service réseau

## Configuration du serveur SSH
* Temps de réalisation : 15 minutes
* Travaux : 
    - Installation du serveur SSH avec : ```bash dnf install openssl-server```
    - Configuration SSH : [Commit de la configuration SSH](https://github.com/CFAI2024-CPLR/projet_web/commit/cd0113d161b13c601ffe34469f758456fede8d4a)

## Configuration des enregistrements DNS
* Temps de réalisation : 25 minutes
* Travaux :
    - Enregistrement des FQDN dans le DNS
    - Vérification avec la commande **host**

|FQDN| IP|
| :---: | :---: |
|chief-platform.vm.cfai24.ajformation.fr.|2a03:5840:111:1024:be24:11ff:feb9:5e8b|
|chief-platform.web.cfai24.ajformation.fr.|2a03:5840:111:1024::11|
|chief-platform.admin.cfai24.ajformation.fr.|2a03:5840:111:1024::11|

## Création et configuration des utilisateurs et groupes
* Temps de réalisation : 10 minutes
* Travaux : 
    - Création des groupes
    - Création des utilisateurs
    - Affilier les utilisateurs aux groupes correspondants

## Installation des logiciels et services
* Temps de réalisation : 45 minutes
* Travaux réalisés :
    - Installation des paquets suivant avec la commande : ```bash dnf install gcc make net-snmp net-snmp-utils httpd mysql mysql-server```
        - **gcc** : compilateur GNU
        - **make** : utilitaire de build
        - **net-snmp** et **net-snmp-utils** : service SNMP
        - **httpd** : apache
        - **mysql** : client MySQL
        - **mysql-server** : serveur MySQL
    - Installation de PHP 8.1 :
    ```bash
    dnf install epel-release
    dnf install http://rpms.remirepo.net/enterprise/remi-release-9.rpm
    dnf install dnf-utils
    dnf module reset php
    dnf module install php:remi-8.1

    Dnf install php php-cli php-common php-gd php-mbstring php-json php-xml php-mysqlnd php-zip php-intl php-soap php-ldap php-bcmath php-imap
    ```
    - Autorisation de pare feu

* Difficultés rencontrées :
    - Il a fallu chercher comment installer une version de php supérieure à la 8.0 dans le but d'utiliser le CRM Vtiger par la suite.
    - Modifier les règles de pare-feu.

## Configuration des droits des dossiers
* Temps de réalisation : 10 minutes
* Travaux effectués :
    - Accorder les droits adaptés aux dossiers **/websites**, **/websites/vitrine**, **websites/gestion**

## Configuration globale Apache2
* Temps de réalisation : 45 minutes
* Travaux effectués :
    - Dans le fichier de configuration [httpd.conf](https://github.com/CFAI2024-CPLR/projet_web/commit/0097419181de5f40d45e3f0f48df41ad11c63cca)
        - Ecouter sur l'adresse IP fixe
        - Renseigner l'utilisateur et le groupe dédié pour exécuter httpd
    - Changer les droits de [php-fpm](https://github.com/CFAI2024-CPLR/projet_web/commit/f45c9f0ea221e4d6ce7f4f9c3d0c4f34e51e8cb6)
        - ```bash
            listen.owner = webmaster
            listen.group = clpr
            listen.mode = 0660
        - Commenter la ligne concernant les acl
* Difficultés rencontrées :
    - Comprendre comment configurer Apache2. C'était une première et a nécessité du temps et de l'aide.
    - Comprendre pourquoi les acl étaient problématiques.