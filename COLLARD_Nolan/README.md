# Identité
- nom : Collard
- prénom : Nolan

* [administration.yaml](administration.yaml)

# Journal d'activité
## Familiarisation avec le projet demandé
Temps passé : 15 minutes.

## Création de la machine virtuelle
* [Documentation](Rapport/RapportInstallationVM.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/be7994ae6c68ee2efffe2fbf4d9d611f38011d74)

Temps de réalisation : 30 minutes.

Travaux effectués :
- configuration matérielle de la machine

## Installation de l'OS
* [Documentation](Rapport/RapportInstallationOS.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/1d16656827e41eea5ca76f21099c5b47c9e0f804)

Temps de réalisation : 1h30

Travaux effectués :
- configuration langue, clavier
- configuration des utilisateurs
- partionnement/formatage du disque
- selection des logiciels

## Configuration du réseau
* [Documentation](Rapport/ConfigRéseau.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/a404c1afa74dff224afaef07094a626ab9e2a5c1)

Temps de réalisation : 1h

Travaux effectués :
- Déterminer l'IPV6
- Choisir une IPV6 Fixe pour les sites web
- Paramétrage du réseau

## Création des utilisateurs et des groupes
* [Documentation](Rapport/RapportCréationUsers.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/2d615a9e4b58b6fa27c8223b3d4f349759deb300)

Temps de réalisation : 45 minutes

Travaux effectués :
- création des groupes vitrine et gestion
- création des utilisateurs et comptes webmaster, rferretti, cyerger
- attribution des groupes

## Création de la hiérarchie des dossiers
* [Documentation](Rapport/RapportHierarchie.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/73f5ca55016fd8ddf08e87fd92ed2689de831388)

Temps de réalisation : 45 minutes

Travaux effectués :
- création des dossiers
- modification de propriétaire
- attribution des droits

## Création de la configuration SSH
* [Documentation](Rapport/ConfigSSH.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/8e2626b1cd1060d43a5fbb276f44926aa342b3fa)

Temps de réalisation : 30 minutes

Travaux effectués :
- création d'une clé ssh
- ajout de la clé aux autres utilisateurs
- ajout de la clé de Mr Avond aux utilisateurs

## Création des paquets et outils
* [Documentation](Rapport/Paquets%20et%20outils.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/8b1b61b2aef0c250d98da38caf4b65e96d918e24)

Temps de réalisation : 8h

Travaux effectués :
- installation des paquets (php, mysql, apache, make, gcc, snmp serveur, serveur ssh)
- installation des outils ( jekyll, espocrm) FAILS : perte de paquet lors de l'installation + récuperation d'installation sur Github impossible puisque Github n'a pas d'IPV6. De plus, la VM ne cesse de mettre un temps de réponse assez énorme

## Enregistrement des FQDN
* [Documentation](Rapport/EnregistrementsFQDN.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/6ea802140b192d26ed1b61c94c18a7c1a9251cf0)

Temps de réalisation : 1h

accès ssh : national-model.vm.cfai24.ajformation.fr. -> 2a03:5840:111:1024:be24:11ff:fea9:df45

site vitrine : national-model.web.cfai24.ajformation.fr. -> 2a03:5840:111:1024::31

site gestion : national-model.admin.cfai24.ajformation.fr -> 2a03:5840:111:1024::31

## Aborescence des fichiers de configuration

- **network**
<br>└── [/etc/network/interfaces]
- **serveur_ssh**
<br>└── [/etc/ssh/sshd_config]
- **serveur_web**
<br>├── **php-fpm**
<br>│&nbsp;&nbsp;&nbsp;&nbsp;├── [/etc/php/8.2/fpm/php.ini]
<br>│&nbsp;&nbsp;&nbsp;&nbsp;└── [/etc/php/8.2/fpm/pool.d/www.conf]
<br>└── **sites**
<br>&nbsp;&nbsp;&nbsp;&nbsp;├── *gestion*
<br>&nbsp;&nbsp;&nbsp;&nbsp;└── *vitrine*

# Utilisateurs
## Root
- login : root
- mdp : Kbdi4Z3!tShz49m8P

## Webmaster
- login : webmaster
- mdp : Prnd4%vd7

## Rachel Ferretti
- login : rferretti
- mdp : Xv85-Mgm4k

## Corey Yerger
- login : cyerger
- mdp : Zhdf78/S*v
