# Projet Web
## Identité

Nom: COSTON

Prénom: Lenny

##  Création VM RockyLinux 9.3 sur l'hyperviseur Proxmox
Connectez-vous sur la plateforme Proxmox : https://cfai2024.ajformation.fr:8006

![installation](/COSTON_Lenny/images/installation_1.png)

Faire un clique droit puis cliquer sur "create VM"

![installation](/COSTON_Lenny/images/installation_2.png)

Je renseigne le nom de ma VM "district-ownership-lcoston" et en Ressource Pool: "lcoston"

![installation](/COSTON_Lenny/images/installation_3.png)

:warning: Ne pas oublier de cocher le "Start at boot"

![installation](/COSTON_Lenny/images/installation_7.png)

Je met l'ISO RockyLinux 9.3

![installation](/COSTON_Lenny/images/installation_4.png)

Je renseigne 15GiB

![installation](/COSTON_Lenny/images/installation_5.png)

Il faut mettre 2 au lieu de "1"

![installation](/COSTON_Lenny/images/installation_6.png)

Cliquer sur "Finish"

![installation](/COSTON_Lenny/images/installation_8.png)

### Configuration de la VM RockyLinux 9.3
J'ai choisi le langague Français.

![configuration](/COSTON_Lenny/images/configuration_1.png)

Les facteurs à parametrer avant de faire l'installation.

![configuration](/COSTON_Lenny/images/configuration_2.png)

Voici les partitionnements demandés:

![configuration](/COSTON_Lenny/images/configuration_3.png)

L'installation se fait.

![configuration](/COSTON_Lenny/images/configuration_4.png)

Une fois fini l'installation il faut cliquer sur "Redémarrer le système".

![configuration](/COSTON_Lenny/images/configuration_5.png)

## Mise à jour du kernel et des packages
Une fois connecter sur votre serveur que ce soit en ssh ou en console, metter à jour le kernel et package à l'aide de la commande suivante :

> sudo dnf update && sudo dnf upgrade -y
![update](/COSTON_Lenny/images/update_1.png)

## Mettre une IPV6 manuel en plus de celle en SLAAC
J'utilise la commande "ip a" afin de retrouver les informations ci-dessous:
- 1: Le nom de la carte réseau utilisé.
- 2: Adresse IPv6 attribué par le SLAA.
```bash
ip a
```

![ipv6](/COSTON_Lenny/images/ipv6_1.png)

Pour ajouter une autre IPv6, il suffit de tapper cette commande:
```bash
sudo nmcli con mod ens18 ipv6.addresses "2a03:5840:111:1024:be24:11ff:fed6:e28b/64, 2a03:5840:111:1024::9/64"
```
```bash
sudo nmcli con up ens18
```

La commande ci dessous permet de montrer les adresses IPv6 de la carte réseau ens18:
```bash
ip -6 addr show ens18
```

![ipv6](/COSTON_Lenny/images/ipv6_2.png)

Voici le résultat avec les IPv6 de set.

![ipv6](/COSTON_Lenny/images/ipv6_3.png)

## Faire un enregistrement DNS
Pour accéder au serveur que ce soit en SSH et/ou sites web, je vais crée un enregistrement DNS en fonction des IPv6.

![dns](/COSTON_Lenny/images/dns_1.png)
- 1: Rendez-vous sur le site: http://ns1.cfai2024.ajformation.fr:5000/
- 2: Insérer l'identifiant de l'hyperviseur Proxmox.
- 3: Insérer le mot de passe de votre compte Proxmox.
- 4: Insérer le nom de l'enregistrement.
- 5: Insérer l'adresse IPv6 sur laquel que vous voulez que l'enregistrement DNS target. 
- 6: Une fois tout bien remplie, cliquer sur "Envoyer"

| FQDN |Adresse IPv6| Utilisation|
| :---: | :---: |  :---: |
|district-ownership.vm.cfai24.ajformation.fr.|  2a03:5840:111:1024:be24:11ff:fed6:e28b | Accès SSH 
|district-ownership.web.cfai24.ajformation.fr.| 2a03:5840:111:1024::9 | Site web vitrine
|district-ownership.admin.cfai24.ajformation.fr.| 2a03:5840:111:1024::9 | Site web de gestion

## Création utilisateurs
```bash
sudo useradd -mU mkasack -c "Mildred Kasack"
sudo useradd -mU munga -c "Margaret Unga"
sudo useradd -mU webmaster
```

## Changement de mot de passe utilisateurs

```bash
sudo passwd mkasack
```
```bash
sudo passwd munga
```
```bash
sudo passwd webmaster
```
```bash
sudo passwd root
```

## Ajout clé public SSH Mr Avond sur chaque utilisateurs

```bash 
su  [nom_utilisateur]
mkdir -p ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
vi ~/.ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDWsfbTbSlxcvxUL1286nwhwrDPJq6bctkxPpZ+TyujHrDwyymvqEjMJNxiwDPRoomPgOcg+YYUYXbfRiLp0VNlUqA5oG9nhlgtiryZrWY6zrywnsDOk6wJvWA/YNbWLlFN14OiKXOH5KJpgYQh1pLIw1TPeR56vU5wv1Ggb0Jr1sg14TJgm2M4lSmQs1CAY8hBLDj/qQcwVNtuYqTXOulwCPZAzhP6ncHM7lHbwJua/3bGQ8IeFzjRGjL0s2XVECYPufCbM0cX1VtmaSQdVmwqXGW2c+rPAq8cFHecfaw/0fdSMeNV4qSl+VqpCGn/XXnpWAYi0OfifddH80ffdAp5 /home/jerome/.ssh/id_rsa
```

## Configuration SSH
Bien penser à enlever le commentaire de la ligne 45
```bash
sudo vi /etc/ssh/sshd_config
#PubkeyAuthentication yes
-> PubkeyAuthentication yes
```
Redémarrer le service SSH
```bash
sudo systemctl restart sshd
```

## Hiérarchie des dossiers
```bash
sudo mkdir -p /websites/vitrine
sudo mkdir -p /websites/gestion
sudo groupadd clpr
sudo groupadd vitrine
sudo groupadd gestion
sudo chown apache:clpr /websites
sudo chown webmaster:vitrine /websites/vitrine
sudo chown webmaster:gestion /websites/gestion
```
## Ajout utilisateurs aux groupes
```bash
sudo usermod -a -G vitrine webmaster
sudo usermod -a -G gestion webmaster
sudo usermod -a -G gestion munga
sudo usermod -a -G vitrine mkasack
sudo usermod -a -G gestion lcoston
sudo usermod -a -G vitrine lcoston
```
## Logiciels et services
```bash
sudo dnf update
```
### OpenSSH
```bash
sudo dnf install openssh-server
sudo systemctl enable --now sshd
sudo systemctl status sshd
```
### Outils de compilation (gcc, make, etc.)
Ces outils sont essentiels pour la compilation de logiciels à partir des sources :
```bash
sudo dnf group install "Development Tools"
```

Vérification des packages installés demandé:
```bash
gcc --version
make --version
```

###  SNMP Server
Pour installer un serveur SNMP (comme Net-SNMP) :
```bash
sudo dnf install net-snmp net-snmp-utils
sudo systemctl enable --now snmpd
sudo systemctl status snmpd
```
###  Apache HTTP Server
Pour installer Apache :
```bash
sudo dnf install httpd
sudo systemctl enable --now httpd
sudo systemctl status httpd
```
###  MySQL (MariaDB)
Pour installer MariaDB :
```bash
sudo dnf install mariadb-server mariadb
sudo systemctl enable --now mariadb
sudo systemctl status mariadb
```
### PHP (dernière version)
```bash
sudo dnf install epel-release
sudo dnf install https://rpms.remirepo.net/enterprise/remi-release-9.rpm
sudo dnf module reset php
sudo dnf module enable php:remi-8.1
sudo dnf install php php-cli php-fpm php-mysqlnd php-xml php-json php-gd php-mbstring
```