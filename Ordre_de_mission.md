# CLPR - Projet Site Web client 'forward-brass'

**Administrateur** : javond - jerome@ajformation.fr

## Ordre de mission 

Votre mission est de préparer un machine virtuelle destinée à l'entreprise '**forward-brass**'

Cette machine doit servir à présenter deux sites web :

- <http://forward-brass.web.cfai24.ajformation.fr> : Site de présentation de l'entreprise
- <http://forward-brass.admin.cfai24.ajformation.fr> : site de gestion de l'entreprise

## Caractéristiques

Vous créerez la VM vous-mêmes dans le proxmox : <https://cfai2024.ajformation.fr:8006> avec votre compte préalablement créé,

Cette VM doit donc avoir les caractéristiques suivantes (cochez la case advanced) :

* Name: forward-brass-javond
* Ressource Pool: javond
* Start at boot : yes
* ISO : **Rocky (latest)**
* Disk Size : 10Go
* VCPU : 1
* RAM : 1Go
* Network : 1 interface

* La distribution linux choisie est : **Rocky (latest)**
* Doit être installé en mode terminal et dans sa version "Serveur"

* Avoir comme FQDN : **forward-brass.vm.cfai24.ajformation.fr**

Le partitionnement de la machine doit être le suivant :

* 1 partition primaire de taille 10GB de type ext4 montée sur / et labellisé root 
* 1 partition primaire de taille 1GB de type swap montée sur swap et labellisé swap 
* 1 partition primaire de taille reste de type ext4 montée sur /websites et labellisé websites

## Réseaux

La machine doit avoir au moins deux adresses IPv6 fixe:

- Une automatique (SLAAC), pour le FQDN VM
- et une manuelle personnalisée (choix à votre convenance) pour les sites web

Vous vérifierez que votre connectivité est fonctionnelle, et que l'adresse IPv6 choisie n'est pas déjà utilisé par une autre machine (avec nmap par exemple, ou tout simplement en vous coordonnant avec vos collègues).

Vous enregistrerez dans le DNS **cfai24.ajformation.fr** les FQDN suivants dans l'outil <http://ns1.cfai2024.ajformation.fr:5000/>

- **forward-brass.vm.cfai24.ajformation.fr** : pour l'accès SSH
- **forward-brass.web.cfai24.ajformation.fr** : pour le site web vitrine
- **forward-brass.admin.cfai24.ajformation.fr** : pour le site web de gestion

## Hiérarchie des dossiers

Il faudra également créer la hiérarchie de dossier suivantes :

* **/websites/**
    * owner : Compte Serveur Web (dépend du serveur et de la distribution)
    * group : clpr
    * droits : u=rwx,g=rwx,o=r-x
* **/websites/vitrine**
    * owner : webmaster
    * group : vitrine
    * droits : u=rwx,g=rwx,o=r-x 
* **/websites/gestion**
    * owner : webmaster
    * group : gestion
    * droits : u=rwx,g=rwx,o=r-x 

---
<div style="page-break-after: always;"></div>

## Utilisateurs et Administration

En tant qu'administrateur de la machine vous créerez votre compte **javond**, et aurez l'entière responsabilité de l'administration de la machine (compte root).

> Vous fournirez néamoins le mot de passe du compte root dans votre rapport !
>
> Vous garderez votre mot de passe personnel SECRET !

Vous créerez les comptes suivants :

* webmaster : compte service
* krumsey <Katherine Rumsey> : Utilisateur, gestion du site vitrine
* jdiga <Judith Diga> : Utilisateur, gestion du site de gestion

Vous créerez les groupes suivants :

* Groupe: vitrine
    * utilisateurs:
        - webmaster
        - javond
        - krumsey <Katherine Rumsey>
* Groupe: gestion
    * utilisateurs:
        - webmaster
        - javond
        - jdiga <Judith Diga>

## Logiciels et services 

La machine doit disposer des logiciels suivants :

* serveur ssh 
* outils de compilation (gcc,make...) 
* snmp server 
* apache 
* sqlite 
* php (dernière version, fonctionne avec apache)

### Les sites web

Pour les sites web vous installerez les outils suivants :

- site vitrine : https://picocms.org/
- site gestion : https://doc.yetiforce.com/introduction/download/

Dans les dossiers /websites dédiés

---
<div style="page-break-after: always;"></div>

## Résultats

### Sites web

à la fin de votre travail, 

    - les deux sites web doivent être fonctionnels
    - on doit pouvoir se connecter facilement en ssh avec chacun des utilisateurs créés

> **ATTENTION !** Je ne vous demande pas de FAIRE des sites webs, les sites peuvent être vides ! 
>
> Ils doivent néanmoins être fonctionnel pour les fournir au client forward-brass

### Rapport d'activité

Vous fournirez un rapport en 2 documents sur le dépôt git suivant : <https://github.com/CFAI2024-CPLR/projet_web>

Les détails du rendu sont dans le Readme.md de ce dossier

En vous souhaitant bon courage pour la réalisation de votre mission,

Vous avez jusqu'au **jeudi 16 mai à 23h50** pour fournir votre PULL REQUEST !

**Votre dévoué formateur,**