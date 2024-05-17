# CLPR - Projet Site Web client 'district-empowerment'
**Administrateur** : egrange - estelle.grange@hotmail.fr

## Ordre de mission
Votre mission est de préparer un machine virtuelle destinée à l'entreprise 'district-empowerment'

Cette machine doit servir à présenter deux sites web :

* <http://district-empowerment.web.cfai24.ajformation.fr> : Site de présentation de l'entreprise
* <http://district-empowerment.admin.cfai24.ajformation.fr> : site de gestion de l'entreprise

## Caractéristiques
Vous créerez la VM vous-mêmes dans le proxmox : https://cfai2024.ajformation.fr:8006 avec votre compte préalablement créé,

Cette VM doit donc avoir les caractéristiques suivantes (cochez la case advanced) :

* Name: district-empowerment-egrange
* Ressource Pool: egrange
* Start at boot : yes
* ISO : Rocky (latest)
* Disk Size : 15Go
* VCPU : 2
* RAM : 2Go
* Network : 1 interface

* La distribution linux choisie est : **Rocky (latest)**

* Doit être installé en mode terminal et dans sa version "Serveur"

* Avoir comme FQDN : **district-empowerment.vm.cfai24.ajformation.fr**

Le partitionnement de la machine doit être le suivant :

* 1 partition primaire de taille 1GB de type ext4 montée sur / et labellisé root
* 1 partition lvm taille 10GB de type ext4 montée sur / et labellisé root
* 1 partition lvm taille 2GB de type swap montée sur swap et labellisé swap
* 1 partition lvm taille reste de type xfs montée sur /websites et labellisé websites

## Réseaux

La machine doit avoir au moins deux adresses IPv6 fixe:

* Une automatique (SLAAC), pour le FQDN VM
* et une manuelle personnalisée (choix à votre convenance) pour les sites web

Vous vérifierez que votre connectivité est fonctionnelle, et que l'adresse IPv6 choisie n'est pas déjà utilisé par une autre machine (avec nmap par exemple, ou tout simplement en vous coordonnant avec vos collègues).

Vous enregistrerez dans le DNS **cfai24.ajformation.fr** les FQDN suivants dans l'outil http://ns1.cfai2024.ajformation.fr:5000/

* district-empowerment.vm.cfai24.ajformation.fr : pour l'accès SSH
* district-empowerment.web.cfai24.ajformation.fr : pour le site web vitrine
* district-empowerment.admin.cfai24.ajformation.fr : pour le site web de gestion

## Hiérarchie des dossiers

Il faudra également créer la hiérarchie de dossier suivantes :

- **/websites/**
  - owner : Compte Serveur Web (dépend du serveur et de la distribution)
  - group : clpr
  - droits : u=rwx,g=rwx,o=r-x

- **/websites/vitrine**
  - owner : webmaster
  - group : vitrine
  - droits : u=rwx,g=rwx,o=r-x

- **/websites/gestion**
  -owner : webmaster
  -group : gestion
  -droits : u=rwx,g=rwx,o=r-x

## Utilisateurs et Administration

En tant qu'administrateur de la machine vous créerez votre compte **egrange**, et aurez l'entière responsabilité de l'administration de la machine (compte root).

* Vous fournirez néamoins le mot de passe du compte root dans votre rapport !

* Vous garderez votre mot de passe personnel SECRET !

Vous créerez les comptes suivants :

* webmaster : compte service
* lberube - Lori Berube : Utilisateur, gestion du site vitrine
* jjackson - John Jackson : Utilisateur, gestion du site de gestion

Vous créerez les groupes suivants :

- Groupe: vitrine
  - utilisateurs:
    - webmaster
    - egrange
    - lberube - Lori Berube
- Groupe: gestion
  - utilisateurs:
   - webmaster
   - egrange
   - jjackson - John Jackson

## Logiciels et services

La machine doit disposer des logiciels suivants :

* serveur ssh
* outils de compilation (gcc,make...)
* snmp server
* **apache**
* **mysql**
* php (dernière version, fonctionne avec apache)

### Les sites web

Pour les sites web vous installerez les outils suivants :

* site vitrine : https://picocms.org/
* site gestion : https://www.espocrm.com/download/

Dans les dossiers /websites dédiés

## Résultats

### Sites web

à la fin de votre travail,

* les deux sites web doivent être fonctionnels
* on doit pouvoir se connecter facilement en ssh avec chacun des utilisateurs créés

**ATTENTION !** Je ne vous demande pas de FAIRE des sites webs, les sites peuvent être vides !

Ils doivent néanmoins être fonctionnel pour les fournir au client district-empowerment

### Rapport d'activité

Vous fournirez un rapport en 2 documents sur le dépôt git suivant : https://github.com/CFAI2024-CPLR/projet_web

Les détails du rendu sont dans le Readme.md de ce dossier

En vous souhaitant bon courage pour la réalisation de votre mission,

Vous avez jusqu'au **jeudi 16 mai à 23h50** pour fournir votre PULL REQUEST !