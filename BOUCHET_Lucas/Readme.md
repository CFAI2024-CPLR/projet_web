# Nom Prénom : BOUCHET Lucas

# Journal d'activités


## Caractéristiques

### Création de la VM

Pour créer la machine virtuelle cela a été asse simple. Il suffisait de mettre les caractéristiques demandé dans le sujet.
![Configuration_VM](https://github.com/CFAI2024-CPLR/projet_web/assets/92736112/efb100d0-09c1-4c9f-9a64-2f89793b7262)
* Temps de travail : 20 min
* Travaux réalisés :
    - Création de la machine virtuelle
    - Ajout des ressources demandé

### Installation de l'OS

J'ai recommencé l'installation 4 fois. J'ai eu des problèmes avec l'installation de base à la fin et je me suis trompé plusieurs fois sur les partitions.
J'avais quasiment terminé le TP que je me suis aperçu que mes partitons était mauvaise car je n'avais plus d'espace pour télécharger les logiciels manquants.
J'ai réinstallé l'OS une nouvelle fois avec les bonnes partitions.

![Partition_Disques](https://github.com/CFAI2024-CPLR/projet_web/assets/92736112/92cd31fb-775a-4b53-8a9f-172bdd405157)

* Temps de travail : 2 heures
* Travaux réalisés :
    - intallation de l'OS
    - Renseigment des informations (Login/MDP/...)
    - Choix sur la conception de l'OS (Gnome/Serveur SSH/...)
    - Partitionnement des diques

## Réseaux

Pour le réseau j'ai mis mes 2 adresses IPv6 en static :
* 2a03:5840:111:1024:be24:11ff:fe3a:7980 / Pour le FQDN VM
* 2A03:5840:111:1024::16 / Pour les sites WEB

Tous c'est bien passé de se coté la même si au début j'ai eu des problèmes avec la mise en place des IP et que je n'avais plus de connexion internet.
J'ai résolu le problème à cause d'une phrase que j'avais commenté dans l'interface de la carte réseau.

* Temps de travail : 1 heures
* Travaux réalisés :
    - Choisir l'adresse IPv6 pour les sites WEB
    - Choisir l'adresse IPv6 pour le FQDN
    - Mettre les IPv6 en static

## Hiérarchie des dossiers

La création de l'arborescence à été faite en suivant les demandes dans le sujet.

![arborescence](https://github.com/CFAI2024-CPLR/projet_web/assets/92736112/7809cf9d-1ae8-41be-9598-a6aae2b5e464)

* Temps de travail : 40 min
* Travaux réalisés :
  - Configuration de l'arborescence
  - Création des dossiers (Vitrine/Gestion)
  - Ajout des propriétés
  - attribution des droits

## Utilisateurs et Administration

Les utilisateurs ont été créé avec chaque accès demandé afin qu'il puisse allé dans les dossiers autorisé avec leurs groupes associés.

* Temps de travail : 1 heure et 30 min
* Travaux réalisés :
    - Création des groupes (CLPR/Vitrine/Gestion)
    - Création des comptes utilisateurs (Webmaster/Dherring/Anance)
    - Ajout des groupes
    - Ajout des clé SSH

## Logiciels et services

L'installation des paquets et outils ont été plus compliqué que prévu. Je n'arrivai pas à les intaller car mon debian ne trouvait pas les packets demandé. J'ai du trouver une solution afin de pouvoir les installer. j'avais mal configuré les répository, et donc le gestionaire de packet APT ne trouvais pas les packet car il n'avais pas de répository de configurer.
Je ne suis pas arriver à installer MySQL, j'ai du choisir une autre option. J'ai donc télécharger MariaDB qui fait exactement la même chose que MySQL.

* Temps de travail : 2 heures et 30 min
* Travaux réalisés :
    - Installation Serveur SSH
    - Installation GCC
    - Installation SNMP Serveur
    - Installation NGINX
    - Installation MariaDB
    - Installation PHP

## Sites web



* Temps de travail : 4 heures
* Travaux réalisés :
    - Création du site vitrine
    - Création du site gestion
    - Configuration de nginx

# Utilisateurs

## Root

- **Login** : root
- **MDP** : Nutell@Br3st

## Webmaster

- **Login** : webmaster
- **MDP** : Nutell@Br3st

## Derek Herring

- **Login** : dherring
- **MDP** : Nutell@Br3st

## Amanda Nance

- **Login** : anance
- **MDP** : Nutell@Br3st

**SSH** : La connexion de root n'est pas autorisé
