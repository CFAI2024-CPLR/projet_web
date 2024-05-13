# Auteur : CAGNOLATI Solène

# Journal d'activités

## Création de la machine virtuelle

* [Documentation](Documentation/CreationVM.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/ee1f51b4e8120ebf0751ce2b4bdc460b15749143)

- **Temps de réalisation** : 30m
- **Travaux réalisés** : 
    - Paramétrage de la machine virtuelle
    - Création de la machine virtuelle

## Installation du système d'exploitation

* [Documentation](Documentation/InstallationOS.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/7ea530892a364a7fb911b505b9d37874462ee280)

- **Temps de réalisation** : 1h
- **Travaux réalisés** : 
    - Configuration des locales
    - Configuration de la machine
    - Configuration des utilisateurs principaux
    - Partitionnement et formatage du disque
    - Installation des logiciels essentiels
    - Installation du système d'exploitation

## Configuration du réseau

* [Documentation](Documentation/ConfigurationReseau.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/d55b24db605d06f0ba5dc5d9474724dca078134b)
* [/etc/network/interfaces](Configuration/interfaces)

- **Temps de réalisation** : 30m
- **Travaux réalisés** : 
    - Déterminer l'adresse IPv6 SLAAC
    - Choix d'une adresse IPv6 fixe pour les sites web
    - Paramètrage des adresses IPv6 fixes
    - Configuration du réseau
    
## Configuration du SSH

* [Documentation](Documentation/ConfigurationSSH.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/e212cfb81c64bf07cccfba2d2408cb0df28b0c63)
* [/etc/ssh/sshd_config](Configuration/sshd_config)

- **Temps de réalisation** : 1h
- **Travaux réalisés** : 
    - Interdiction de la connexion en SSH via l'utilisateur root
    - Autorisation de la connexion SSH uniquement depuis l'adresse IPv6 **2A03:5840:111:1024:BC26:11FF:FE46:D54D**
    - Création d'une clé SSH pour la connexion
    - Interdiction de se connecter via un mot de passe
    - Configuration du SSH

## Création des utilisateurs et des groupes

* [Documentation](Documentation/CreationUtilisateursGroupes.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/ba336ae28f463c2f3bf835d90100674ed422fb63)

- **Temps de réalisation** : 1h
- **Travaux réalisés** : 
    - Création du groupe **clpr**
    - Création du groupe **vitrine**
    - Création du groupe **gestion**
    - Création des groupes
    - Création du compte **webmaster**
    - Création du compte **amcfarland**
    - Création du compte **mbarr**
    - Création des utilisateurs
    - Attribution des groupes
    - Ajout des clés SSH pour les nouveaux utilisateurs
    - Création des utilisateurs et des groupes

## Configuration de l'arborescence

* [Documentation](Documentation/ConfigurationArborescence.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/55a6cf4d96cbf6f3bd232eb536b996927f30bfc4)

- **Temps de réalisation** : 30m
- **Travaux réalisés** : 
    - Création des dossiers
    - Configuration des propriétés
    - Attribution des droits
    - Configuration de l'arborescence

## Installation des paquets et outils

* [Documentation](Documentation/ConfigurationArborescence.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/727d0becb0a23718826e7468462e7b9acb7ad544)

- **Temps de réalisation** : 2h
- **Travaux réalisés** : 
    - Installation de PHP
    - Installation de Nginx
    - Installation de MySQL
    - Installation de SNMP Serveur
    - Installation de GCC
    - Installation de Make
    - Installation de Jekyll
    - Installation de YetiForce
    - Installation des paquets et outils

## Configuration des sites web

* [Documentation](Documentation/ConfigurationSitesWeb.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/f07ac4de9bbbb8a2dedbf5dad195eb5f3dc1ef9b)
* [/etc/php/8.2/fpm/pool.d/www.conf ](Configuration/www.conf)
* [/etc/nginx/sites-available/vitrine](Configuration/vitrine)
* [/websites/vitrine/_config.yml](Configuration/_config.yml)
* [/etc/nginx/sites-available/gestion](Configuration/gestion)
* [/etc/php/8.2/fpm/php.ini](Configuration/php.ini)
* [/etc/mysql/mysql.d.conf/mysqld.cnf](Configuration/mysqld.cnf)

- **Temps de réalisation** : 6h
- **Travaux réalisés** : 
    - Configuration du site vitrine
    - Configuration du site gestion
    - Configuration des sites web

## Enregistrement des FQDN

* [Documentation](Documentation/EnregistrementFQDN.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/3f8dda76af97a18d3e3e519d334ec9929dbb2c2c)

- **Temps de réalisation** : 30m
- **Travaux réalisés** : 
    - Enregistrement du FQDN pour l'accès SSH
    - Enregistrement du FQDN pour le site vitrine
    - Enregistrement du FQDN pour le site gestion
    - Enregistrement des FQDN

# Utilisateurs

* [~/.ssh/config](Configuration/config)

## Root

- **Login** : root
- **MDP** : \*CuSt0m3r1d34t10N\*
- **SSH** : La connexion de root en SSH n'est pas autorisée

## Webmaster

- **Login** : webmaster
- **MDP** : \*W3bM4st3R\*

## Amy MCFARLAND

- **Login** : amcfarland
- **MDP** : \*4mYMCf4rl4nD\*

## Mavis BARR

- **Login** : mbarr
- **MDP** : \*M4v1SB4rR\*