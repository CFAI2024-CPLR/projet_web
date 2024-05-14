# Projet Web
## Identité

**Nom**: COSTON

**Prénom**: Lenny

# Journal d'activités

## Création de la machine virtuelle
Temps de réalisation: 1H00

Travaux réalisés:
- [Configuration de la VM](#création-vm-rockylinux-93-sur-lhyperviseur-proxmox)
- [Installation et configuration de l'OS Rocky Linux 9.3](#configuration-de-la-vm-rockylinux-93)

## Configuration réseau / serveur openSSH
Temps de réalisation: 30 minutes

Travaux réalisés:
- [Mettre une IPV6 manuel en plus de celle en SLAAC](#mettre-une-ipv6-manuel-en-plus-de-celle-en-slaac)
- [Ajout clé public SSH Mr Avond sur chaque utilisateurs](#ajout-clé-public-ssh-mr-avond-sur-chaque-utilisateurs)
- [Configuration SSH](#configuration-ssh)

## Gestion des utilisateurs et groupe
Temps de réalisation: 30 minutes

Travaux réalisés:
- [Création utilisateurs](#création-utilisateurs)
- [Changement de mot de passe utilisateurs](#changement-de-mot-de-passe-utilisateurs)
- [Ajout utilisateurs aux groupes](#hiérarchie-des-dossiers)

## Installation des paquets
Temps de réalisation: 10 minutes

Travaux réalisés:
- [Logiciels et services](#logiciels-et-services)

## Enregistrement DNS
Temps de réalisation: 10 minutes

Travaux réalisés:
- [Enregistrement DNS](#enregistrement-dns)

## Installation et configuration des sites web
Temps de réalisation: 1H00

Travaux réalisés:
- [Configuration Vhost](#configuration-vhost)
- [Vtiger](#vtiger)
      - [Configuration Vhost du site gestion](#configuration-vhost-du-site-gestion)
      - [Configuration socket PHP](#configuration-socket-php)
- [HUGO](#hugo)
      - [Configuration Vhost du site vitrine](#configuration-vhost-du-site-vitrine)
- [Selinux permissive](#selinux)
- [Firewalld](#ouverture-des-ports)

# Utilisateurs
## Informations de connexion

| Utilisateur |login| mot de passe |
| :---: | :---: | :---: | 
|root| root | BonjourToto43 |
|Gabe Newell| webmaster | 3gecHc917RAFeFUOROXI |
| Margaret Unga | munga | zeKqumwH81UblPPK3Smz |
| Mildred Kasack | mkasack | LBhsF51N4kOBeM9OfLUb |


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

# Sites WEB
Voici le rendu du site web vitrine : [Vitrine](http://district-ownership.web.cfai24.ajformation.fr)
Voici le rendu du site web gestion : [Gestion](http://district-ownership.web.cfai24.ajformation.fr)

## Configuration Vhost
```bash
sudo mkdir /etc/httpd/sites-available
sudo mkdir /etc/httpd/sites-enabled
```

## Vtiger

```bash
cd /websites/gestion
sudo wget https://deac-riga.dl.sourceforge.net/project/vtigercrm/vtiger%20CRM%208.1.0/Core%20Product/vtigercrm8.1.0.tar.gz
sudo tar -xvzf vtigercrm8.1.0.tar.gz
```
```bash
sudo dnf install httpd php php-mysqlnd php-zip php-gd php-mbstring php-xml php-json mariadb-server
```
```bash
sudo chown -R webmaster:gestion /websites/gestion
```
```bash
mysql -u root -p
```
```sql
CREATE DATABASE vtiger;
CREATE USER 'vtigeruser'@'localhost' IDENTIFIED BY '**************';
GRANT ALL PRIVILEGES ON vtiger.* TO 'vtigeruser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```
### Configuration Vhost du site gestion
```bash
cd /etc/httpd/sites-available
sudo touch gestion.conf
sudo vi gestion.conf

<VirtualHost *:80>
    ServerName district-ownership.admin.cfai24.ajformation.fr
    DocumentRoot /websites/gestion/

    ErrorLog /var/log/httpd/gestion_error.log
    CustomLog /var/log/httpd/gestion_access.log combined

    <Directory "/websites/gestion/">
        AllowOverride All
        Require all granted
    </Directory>
    <FilesMatch \.php$>
       SetHandler "proxy:unix:/run/php-fpm/vtiger.sock|fcgi://localhost/"
    </FilesMatch>

</VirtualHost>

sudo ln -s /etc/httpd/sites-available/gestion.conf /etc/httpd/sites-enabled/gestion.conf
```
### Configuration socket PHP
```bash
cd /etc/php-fpm.d/
sudo mkdir vtiger.conf

[source]
user = webmaster
group = gestion
listen = /run/php-fpm/vtiger.sock
listen.owner = webmaster
listen.group = gestion
listen.mode = 0775

pm = dynamic
pm.max_children = 50
pm.start_servers = 5
pm.min_spare_servers = 5
pm.max_spare_servers = 35

php_admin_value[error_log] = /var/log/php-fpm/vtiger-error.log
php_admin_flag[log_errors] = on
php_value[session.save_handler] = files
php_value[session.save_path]    = /var/lib/php/session
```


## Hugo

```bash
cd /websites/vitrine
sudo wget https://github.com/gohugoio/hugo/releases/download/v0.125.5/hugo_extended_0.125.5_Linux-64bit.tar.gz
sudo tar -xzf hugo_extended_0.125.5_Linux-64bit.tar.gz -C /usr/local/bin
hugo new site /website/vitrine/
hugo
```
```bash
sudo chown -R webmaster:vitrine /websites/vitrine
```
### Configuration Vhost du site vitrine
```bash
cd /etc/httpd/sites-available
sudo touch vitrine.conf
sudo vi vitrine.conf


<VirtualHost *:80>
    ServerName district-ownership.web.cfai24.ajformation.fr
    DocumentRoot /websites/vitrine/public
    <Directory "/websites/vitrine/public">
        AllowOverride All
        Require all granted
    </Directory>
    ErrorLog /var/log/httpd/vitrine_error.log
    CustomLog /var/log/httpd/vitrine_access.log combined
</VirtualHost>


sudo ln -s /etc/httpd/sites-available/vitrine.conf /etc/httpd/sites-enabled/vitrine.conf
```
## Ouverture des ports

```bash
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --reload
```
## SeLinux

Je le met en mode permissive pour pas qu'il me pose de problème, à voir plus tard quel ID règles match pour les commenter.
```bash
sudo setenforce 0
```

## Modification configuration utilisateur et groupe httpd
```bash
cd /etc/httpd/conf/
sudo vim httpd.conf

# Lignes 71 et 72 changer l'utilisateur et le groupe par webmaster et gestion
User webmaster
Group gestion

sudo systemctl restart httpd
```