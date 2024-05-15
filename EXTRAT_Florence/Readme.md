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