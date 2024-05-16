# Auteur : Loic CONVERT

# Journal d'activités

# Création de la VM
 Temps de réalisation : 45 min

Travaux réalisés:
 1. Création de la VM
 2. Partionnement de la VM et création des utilisateurs root et lconvert
 3. Update des packages avec la commande :
    ```
    sudo dnf update && sudo dnf upgrade -y
    ```
# Configuration et Activation de l'IPv6 

 Temps de réalisation : 30 min

Travaux réalisés: 
* Ajout d'une adresse IPv6 :
```
sudo nmcli con mod ens18 ipv6.addresses "2a03:5840:111:1024:be24:11ff:feb7:a70a/64, 2a03:5840:111:1024::14/64"
```
Activer la connexion réseau pour l'interface ens18 : 
```
sudo nmcli con up ens18
```
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/938e04950e76f29dce3ad9c8b8e49c6c914a3540)

# Enregistrement dans le DNS les FQDN
 Temps de réalisation : 30 min

Travaux réalisés: Enregistrement des FQDN

![](Images/ajoutdns1.png)

![](Images/ajoutdns2.png)

![](Images/ajoutdns3.png)


| Domaine                                             | Adresse IPv6                                 |
|-----------------------------------------------------|----------------------------------------------|
| future-empowerment.vm.cfai24.ajformation.fr         | 2a03:5840:111:1024:be24:11ff:feb7:a70a       |
| future-empowerment.web.cfai24.ajformation.fr        | 2a03:5840:111:1024::14                       |
| future-empowerment.admin.cfai24.ajformation.fr      | 2a03:5840:111:1024::14                       |

# Installation et Configuration des logiciels
Temps de réalisation: 1 h

Travaux réalisés:

Pour installer tous les paquets nécessaires, j'ai executé la commande suivante : 
```
sudo dnf install -y openssh-server gcc make net-snmp nginx mysql php php-fpm php-mysqlnd
```

Fichier de configuration Nginx :
* [Configuration](Configuration/nginx.conf)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/33e126fc9e8de812f5adac17bd346b8f877a43b5)

Fichier de configuration PHP :
* [Configuration](Configuration/php.ini)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/fa5a4daeb2b502817215048bfa682d4f230f4e32)
* Configuration ssh :

Autorisation de la connexion SSH uniquement depuis l'adresse IPv6 :

![](Images/authssh.png)

Fichier de configuration SSH : 
* [Configuration](Configuration/sshd_config)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/5353dc039a9b294734a07a0dc0ec0c7ed7f6fdfc)

Fichier de configuration du Serveur Mysql :
* [Configuration](Configuration/mysql-server.cnf)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/4c13bdea24ef454acbcade3048500c9dbce3ad35)
* Après avoir executé la commande suivante : 
```
dnf install -y mysql-server, nous devons démarrer le service --> systemctl start mysqld
```
Maintenant, pour sécuriser l'installation de MySQL, utiliser cette commande : mysql_secure_installation

![](Images/mysqlsec1.png)
![](Images/mysqlsec2.png)

# Création des groupes et des utilisateurs : 
Temps de réalisation: 1h

Travaux réalisés:

* Création du groupe clpr
* Création du groupe vitrine
* Création du groupe gestion

Executer la commande suivante pour chaque groupes : 
```
sudo groupadd "groupe"
```
Assuré vous de remplacer "groupe" par le nom du groupe souhaité.

* Création du compte webmaster
* Création du compte dkee
* Création du compte wtownsend
Executer la commande suivante pour chaque utilisateurs :
```
sudo useradd -mU utilisateur -c "utilisateur"
```
Assuré vous de remplacer "utilisateur" par le nom d'utilisateur souhaité.

Ensuite, pour ajouter les utilisateurs aux groupes correspondant : 

![](Images/addgrp.png)

Bien pensez a donner les droits avec cette commande : 

![](Images/adddroit.png)

Pour afficher les droits :

![](Images/affichedroit.png)


# Ajout des clés SSH pour les nouveaux utilisateurs

```
ssh-copy-id -i wtownsend.pub wtownsend@2a03:5840:111:1024:be24:11ff:feb7:a70a
ssh-copy-id -i wtownsend.pub dkee@2a03:5840:111:1024:be24:11ff:feb7:a70a
ssh-copy-id -i wtownsend.pub webmaster@2a03:5840:111:1024:be24:11ff:feb7:a70a
```
* On modifie le fichier ~/.ssh/authorized_keys de chaque utilisateur
* On ajoute à la suite la clé publique suivante : 
```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDWsfbTbSlxcvxUL1286nwhwrDPJq6bctkxPpZ+TyujHrDwyymvqEjMJNxiwDPRoomPgOcg+YYUYXbfRiLp0VNlUqA5oG9nhlgtiryZrWY6zrywnsDOk6wJvWA/YNbWLlFN14OiKXOH5KJpgYQh1pLIw1TPeR56vU5wv1Ggb0Jr1sg14TJgm2M4lSmQs1CAY8hBLDj/qQcwVNtuYqTXOulwCPZAzhP6ncHM7lHbwJua/3bGQ8IeFzjRGjL0s2XVECYPufCbM0cX1VtmaSQdVmwqXGW2c+rPAq8cFHecfaw/0fdSMeNV4qSl+VqpCGn/XXnpWAYi0OfifddH80ffdAp5 /home/jerome/.ssh/id_rsa
```

Au niveau des sites web demandés, j'arrive me connecter sur mon Nginx mais je n'est pas réussi à configurer Vtiger pourtant j'ai fais des recherches.
J'ai quand même installer le paquet et extrait le fichier tar.gz J'ai ensuite crée une base de données pour Vtiger (qui ne m'a pas été utile vu que je n'est pas réussi à configurer Vtiger) :

```
CREATE USER 'vtiger'@'localhost' IDENTIFIED BY 'Secret'; 
donne les droits : GRANT ALL PRIVILEGES ON vtiger.* TO 'vtiger'@'localhost';
FLUSH PRIVILEGES;
exit
```

# Utilisateurs

## Root

- **Login** : root
- **MDP** : Banana203!

## Webmaster

- **Login** : webmaster
- **MDP** : webmaster

## Donovan Kee

- **Login** : dkee
- **MDP** : dkee

## Willis Townsend

- **Login** : wtownsend
- **MDP** : wtownsend

