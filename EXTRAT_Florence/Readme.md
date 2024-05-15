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
