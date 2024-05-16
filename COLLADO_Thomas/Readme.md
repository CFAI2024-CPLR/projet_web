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
| lobal-vision.vm.cfai24.ajformation.fr  | 2a03:5840:111:1024:be24:11ff:fe21:10df  |SSH|
| global-vision.web.cfai24.ajformation.fr  | 2a03:5840:111:1024::33  |Site vitrine|
|global-vision.admin.cfai24.ajformation.fr|2a03:5840:111:1024::33|Site gestion|

Configuration de SSH pour écouter sur une IP spécifique :

```bash
ListenAddress [2a03:5840:111:1024:be24:11ff:fe21:10df]
```

## Configuration des utilisateurs / groupes 

Temps de réalisation : 10 minutes

Réalisation :

- Création des utilisateurs
- Création des groupes
- Ajouts des utilisateurs dans les bons groupe

## Installation des paquets

Temps de réalisation : 10 minutes

Installations des paquets suivants :

- openssh-server (Durant l'installation de l'OS)
- mariadb (Alternative OpenSource à MySQL)
- snmpd
- nginx (1.22.1)
- php 8.2
- build-essential



