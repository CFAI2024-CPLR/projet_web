# Identité 
Nom: Piraud

Prénom: Amélie 

# Journal d'activités
## Création de la machine virtuelle
Temps de réalisation: 30 minutes

Travaux réalisés:
- Configuration matérielle de la machine virtuelle
- Installation de l'OS Debian 12
- Partitionnement et formattage du disque 

## Mise en réseau / Serveur SSH
Temps de réalisation: 15 minutes

Travaux réalisés:
- Ajout d'une 2 ème adresse IPV6 à la carte réseau
- Configuration SSH
- [Commit configuration SSH](https://github.com/CFAI2024-CPLR/projet_web/commit/5d723b6086c09034182fca8c389db65cf3f64e09)

## Configuration des utilisateurs / groupes
Temps de réalisation: 10 minutes

Travaux réalisés:
- Création des comptes utilisateurs
- Création des groupes 
- Ajout des utilisateurs dans les groupes 

## Installation des paquets 
Temps de réalisation: 10 minutes

Travaux réalisés:
- Installation des paquets suivants : 
    - serveur SSH (installé lors d'installation de l'OS)
    - mysql -> J'ai fait le choix d'installer MariaDB (alternative OpenSource)
    - snmpd 
    - nginx
    - PHP 8.2.7
    - buil-essential (pour les outils de compilation)

## Enregistrement DNS
Temps de réalisation: 10 minutes

Travaux réalisés:
- Enregistrement des FQDN suivants dans le DNS

| FQDN |Adresse IP| Utilisation|
| :---: | :---: |  :---: |
|investor-system.vm.cfai24.ajformation.fr.|  2a03:5840:111:1024:be24:11ff:fe85:7f62 | Accès SSH 
|investor-system.web.cfai24.ajformation.fr.| 2a03:5840:111:1024::5 | Site web vitrine
|investor-system.admin.cfai24.ajformation.fr.| 2a03:5840:111:1024::5 | Site web de gestion

## Installation des sites web
Temps de réalisation: 40 minutes

Travaux réalisés:
- Création des répertoires de travail dans /websites
- Configuration du serveur Web Nginx
    > [Commit configuration Nginx](https://github.com/CFAI2024-CPLR/projet_web/commit/d6a5d4f26de6a8bd83486149f500e7beb1debe07)
- Installation et configuration du [site vitrine - HUGO](http://investor-system.web.cfai24.ajformation.fr) 
     > [Commit configuration Site vitrine HUGO](https://github.com/CFAI2024-CPLR/projet_web/commit/3b30a9f7dd7daa550cc06fe2f84e54177eeed82c)
- Installation et configuration du [site de gestion - Vtiger](http://http://investor-system.admin.cfai24.ajformation.fr)
    > [Commit configuration Site de gestion - Vtiger ](https://github.com/CFAI2024-CPLR/projet_web/commit/904da872b0e5d2f49371c126ee55b705833c081e)

# Utilisateurs
## Informations de connexion

| Utilisateur |login| mot de passe |
| :---: | :---: | :---: | 
|root| root | 2^2egale4 |
|Kerry Flores| kflores | 2^1egale2 |
|Patrick Salas| psalas | 2^1egale2 |

## Configuration SSH

### Fichier config

*N'oubliez pas d'adapter l'utilisateur dans votre fichier config*

```
Host investor-system
	HostName investor-system.vm.cfai24.ajformation.fr 
	User kflores
```
### Commande connexion 

```
ssh investor-system
```

**Attention:** : Les connexions SSH en utilisant un login/mdp ne sont pas autorisées. Vous devez m'envoyez votre clé publique si vous voulez vous connectez à la machine.




