# Tourier Mathis
__________________

## Introduction 
__________________

Ce compte rendu détail la mise en place de ma VM dans le proxmox : <https://cfai2024.ajformation.fr:8006>. Ma mission était de préparer un machine virtuelle destinée à l'entreprise '**direct-system**'

Cette machine doit servir à présenter deux sites web :

- <http://direct-system.web.cfai24.ajformation.fr> : Site de présentation de l'entreprise
- <http://direct-system.admin.cfai24.ajformation.fr> : site de gestion de l'entreprise
_________________

## Mise en place de la VM : 1H30 

* Name: direct-system-mtourier
* Ressource Pool: mtourier
* Start at boot : yes
* ISO : **Debian (latest)**
* Disk Size : 15Go
* VCPU : 2
* RAM : 2Go
* Network : 1 interface

* La distribution linux choisie est : **Debian (latest)**
* Installé en mode terminal et dans sa version "Serveur"

### Le partitionnement est le suivant : 
* 1 partition primaire de taille 1GB de type     ext4 montée sur / et labellisé root
* 1 partition lvm taille         10GB de type    ext4 montée sur / et labellisé root
* 1 partition lvm taille         2GB de type     swap montée sur swap et labellisé swap
* 1 partition lvm taille         reste de type   xfs  montée sur /websites et labellisé websites
__________________
## Hiérarchie des dossiers 45min

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
__________________
 ## Administration 30min
* webmaster : compte service
* sdeutsch - Steven Deutsch : Utilisateur, gestion du site vitrine
* rmccarthy - Russell Mccarthy : Utilisateur, gestion du site de gestion
* root password : P@ssword2021
* Groupe: vitrine
    * utilisateurs:
        - webmaster
        - mtourier
        - sdeutsch - Steven Deutsch
* Groupe: gestion
    * utilisateurs:
        - webmaster
        - mtourier
        - rmccarthy - Russell Mccarthy
  __________________
  ## Résultat
  * VM --> opérationnelle
  * Réseau --> IP fixe ok 
  * Partionnement --> Vm bien partitionnée
  * Hiérarchiration --> Les dossiers sont bien hiérarchisé
 __________________
  ## Conclusion

 Suite à ma période de vacances de deux semaines, une connexion au réseau très restreinte (malaisie), pas d'ordinateur seulement un téléphone pour travailler, 
 ainsi que du court laps de temps (seulement trois jours), et ma reprise de travail pour finaliser ce tp, 
 je n'ai malheureusement pas eu l'opportunité de tester toutes les connexions aux sites. 
 Cependant, j'ai fait de mon mieux pour produire quelque chose de présentable. Je vous prie donc de prendre exceptionnelement en considération ces contraintes lors de l'évaluation. 
 Vous en remerciant par avance, avec mes excuses. 
  
  
