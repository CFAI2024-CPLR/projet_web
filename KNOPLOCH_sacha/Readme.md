# Projet Web

# Identité
Nom : KNOPLOCH

Prénom : Sacha

# Rapport d'activités

# Création de la VM
 Temps de réalisation : 1h

 Travaux réalisés:
 1. Création de la VM
 2. Partionnement de la VM et création des users root et sknoploch
 3. Update des packages avec la commande : sudo dnf update && sudo dnf upgrade -y

 # Ajout d'une IPv6 

 Temps de réalisation : 20 min

Travaux réalisés: 
Ajout d'une adresse IPv6 à l'aide de cette commande : sudo nmcli con mod ens18 ipv6.addresses "2a03:5840:111:1024:be24:11ff:fe17:5111/64,2a03:5840:111:1024::22/64 

# Enregistrement DNS
 Temps de réalisation : 20 min

Travaux réalisés: Enregistrement des fqdn
![](Images/fqdn.png)
|FQDN | IPv6 |  
|----------|----------|
|  master-control.admin.cfai24.ajformation.fr | 2a03:5840:111:1024::22  
| master-control.web.cfai24.ajformation.fr  |  2a03:5840:111:1024::22 
|  master-control.vm.cfai24.ajformation.fr  | 2a03:5840:111:1024:be24:11ff:fe17:5111  | 

[Dns commit](https://github.com/CFAI2024-CPLR/projet_web/commit/673dc774d6922a22947904378fd25105c64713a7)

# Installation des paquets
Temps de réalisation: 20 minutes

Travaux réalisés:

Installation des logiciels suivants :
serveur ssh
outils de compilation (gcc,make...)
snmp server
apache
mysql
php (dernière version )


# Création des groupes et des users : 
Temps de réalisation: 20 minutes

Travaux réalisés:

Création des comptes utilisateurs avec la commande : sudo useradd -mU nomduUser -c "nomduUser"

Création des groupes avec la commande : sudo groupadd "nomdugroupe"

Ajout des utilisateurs dans les groupes : sudo usermod -a -G "nomdugroupe" "nomduUser"

Ajout de la clé publique sur chaque user de monsieur Avond

| Utilisateurs | Login | Mot de passe |
|----------|----------|----------|
|  root | root  | Wxcvbn!123  |
| Ida Goodyear  | igoodyear  | @$#$W9me3t62  |
|  Mary Ratermann | mratermann  | 2&6%SZ7X*7s#  |
| webmaster  | webmaster | cr4&9k3@B9%@  |

# Création des sites webs 

Temps de réalisation: 2 heures

Travaux réalisés:

Création des sites webs dans /websites/vitrine et /websites/vtiger

Config site vitrine HUGO
vitrine.conf : server {
listen [2a03:5840:111:1024::22];
server_name [master-control.web.cfai24.ajformation.fr](http://master-control.web.cfai24.ajformation.fr/);

```
    root /websites/vitrine/public;
    index index.html;

```

}
Pas réussi à le faire fonctionner

Config site vitrine vtiger

gestion.conf : server {
listen [2a03:5840:111:1024::22];
server_name [master-control.admin.cfai24.ajformation.fr](http://master-control.admin.cfai24.ajformation.fr/);

```
    root /websites/gestion;
    index index.html;

```

}
User vtiger crée dans la base sql vtiger:
CREATE DATABASE vtiger;
CREATE USER 'vtigeruser'@'localhost' IDENTIFIED BY 'azerty@123';
GRANT ALL PRIVILEGES ON vtiger.* TO 'vtigeruser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
Pareil pas réussi à le faire fonctionner
