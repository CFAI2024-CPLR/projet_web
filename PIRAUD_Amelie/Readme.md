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




