# Rapport d'activité - Mission d'administration de machine virtuelle

## Introduction
Ce rapport détaille les étapes effectuées pour la préparation et l'administration d'une machine virtuelle destinée à l'entreprise "district-alignment". La mission comprenait la mise en place de deux sites web, la configuration réseau, la création d'utilisateurs et de groupes, l'installation de logiciels et de services, ainsi que la rédaction d'un rapport d'activité.

## Préparation de la machine virtuelle : 15 Min

### Caractéristiques de la machine virtuelle
- **Nom:** district-alignment-fbouloumie
- **Ressource Pool:** fbouloumie
- **Démarrage automatique:** Oui
- **ISO:** Rocky (latest)
- **Taille du disque:** 15Go
- **VCPU:** 2
- **RAM:** 2Go
- **Réseau:** 1 interface
- **Distribution Linux:** Rocky (latest) en mode terminal "Serveur"
- **FQDN:** district-alignment.vm.cfai24.ajformation.fr

### Partitionnement
- 1 partition primaire de 1GB montée sur / (ext4)
- 1 partition LVM de 10GB montée sur / (ext4)
- 1 partition LVM de 2GB montée sur swap
- 1 partition LVM restante montée sur /websites (xfs)

## Réseaux : 30 Min
- IPv6 automatique (SLAAC) pour le FQDN VM
- IPv6 manuelle personnalisée pour les sites web

## Hiérarchie des dossiers : 15 Min
- /websites/
- /websites/vitrine (propriétaire: webmaster, groupe: vitrine)
- /websites/gestion (propriétaire: webmaster, groupe: gestion)

### Utilisateurs et Administration : 20 Min
- **Compte administrateur:** fbouloumie (mot de passe fourni dans le rapport)
- **Comptes utilisateurs:** 
	- root ( mdp : root)
	- webmaster (mdp : webmaster)
	- sbonham (mdp : sbonham)
	- gcox (mdp : gcox)
- **Groupes:** vitrine, gestion

### Logiciels et services
- Serveur SSH
- Outils de compilation
- SNMP server
- Nginx
- MySQL
- PHP (dernière version)

## Sites web
- Site vitrine: Jekyll
- Site de gestion: YetiForce

## Résultats
### Sites web
Les deux sites web ont été installés avec succès dans les dossiers dédiés et sont fonctionnels.

### Connexions SSH
Les connexions SSH sont opérationnelles pour tous les utilisateurs créés.

## Conclusion
La machine virtuelle pour l'entreprise "district-alignment" a été préparée avec succès selon les spécifications fournies. Les sites web sont fonctionnels et les services nécessaires sont installés. Le rapport d'activité a été fourni dans les délais impartis.