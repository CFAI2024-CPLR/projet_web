Présentation de Debian
----------------------

Debian est une distribution Linux populaire, connue pour sa stabilité, sa sécurité et sa vaste collection de logiciels. Créée en 1993 par Ian Murdock, Debian est l'une des plus anciennes distributions Linux encore activement développées. Elle est utilisée comme base pour de nombreuses autres distributions, y compris Ubuntu. Debian se distingue par son engagement envers les principes du logiciel libre et son développement communautaire.

### Caractéristiques de Debian

-   **Stabilité** : Debian est réputée pour sa stabilité. Les logiciels sont rigoureusement testés avant d'être inclus dans la version stable.
-   **Sécurité** : Les mises à jour de sécurité sont promptement publiées et gérées par une équipe dédiée.
-   **Paquets** : Plus de 50,000 paquets logiciels disponibles dans les dépôts officiels.
-   **Support multi-architecture** : Supporte plusieurs architectures matérielles, y compris x86, ARM, et plus.
-   **Gestion des paquets** : Utilise `APT` pour la gestion des paquets, ce qui facilite l'installation et la mise à jour des logiciels.

Comparaison avec d'autres distributions Linux pour serveurs
-----------------------------------------------------------

### Debian vs Ubuntu Server

-   **Stabilité** : Debian est souvent considérée plus stable que Ubuntu Server, car Ubuntu incorpore des versions plus récentes des logiciels, ce qui peut parfois introduire des bugs.
-   **Cycle de sortie** : Debian a des cycles de sortie plus longs (tous les 2 à 3 ans), tandis qu'Ubuntu a des versions LTS (Long Term Support) tous les 2 ans, avec un support de 5 ans.
-   **Support et communauté** : Ubuntu bénéficie du support commercial de Canonical, en plus d'une large communauté. Debian est principalement soutenue par sa communauté.
-   **Utilisation** : Ubuntu est souvent choisi pour ses facilités d'utilisation et son support commercial, tandis que Debian est préféré pour des environnements nécessitant une stabilité maximale.

### Debian vs CentOS / Rocky Linux

-   **Origine** : CentOS (et maintenant Rocky Linux) est basé sur Red Hat Enterprise Linux (RHEL), tandis que Debian est indépendante.
-   **Paquets** : CentOS/Rocky Linux utilise le gestionnaire de paquets `yum` ou `dnf` et les paquets RPM, alors que Debian utilise `APT` et les paquets DEB.
-   **Stabilité et support** : CentOS est très stable et est utilisé dans des environnements de production critique, similaire à Debian. Cependant, CentOS a une politique de support de 10 ans, ce qui est plus long que celle de Debian.
-   **Cycle de sortie** : CentOS suit les cycles de RHEL, avec des mises à jour moins fréquentes mais de longue durée.

### Debian vs Fedora Server

-   **Objectif** : Fedora est souvent considéré comme une version plus expérimentale, avec des logiciels plus récents et des fonctionnalités de pointe, tandis que Debian se concentre sur la stabilité.
-   **Cycle de sortie** : Fedora a un cycle de sortie rapide (tous les 6 mois), comparé aux sorties plus espacées de Debian.
-   **Utilisation** : Fedora est idéal pour les développeurs et les utilisateurs qui veulent tester les dernières technologies, tandis que Debian est préféré pour les serveurs nécessitant une stabilité maximale.

### Debian vs Arch Linux

-   **Complexité** : Arch Linux est connu pour sa philosophie "Keep It Simple, Stupid" (KISS) et requiert une installation manuelle plus complexe, tandis que Debian offre une installation plus automatisée et conviviale.
-   **Rolling release** : Arch Linux suit un modèle de publication continue (rolling release), fournissant toujours les versions les plus récentes des logiciels. Debian, avec ses versions stables, favorise la stabilité par rapport aux dernières fonctionnalités.
-   **Stabilité** : Debian est plus stable et testée, tandis qu'Arch peut être plus susceptible aux bugs en raison de ses logiciels plus récents.

### Conclusion

Pour choisir la bonne distribution Linux pour un serveur, il est important de considérer vos besoins spécifiques :

-   **Debian** : Idéal pour ceux qui recherchent une stabilité et une sécurité maximales sans la nécessité d'un support commercial.
-   **Ubuntu Server** : Meilleur pour les utilisateurs qui veulent un support commercial et des versions logicielles plus récentes avec une bonne communauté de support.
-   **CentOS / Rocky Linux** : Préférable pour les environnements d'entreprise nécessitant un support à long terme et une stabilité de niveau production.
-   **Fedora Server** : Convient aux développeurs et utilisateurs avancés voulant expérimenter les dernières technologies.
-   **Arch Linux** : Pour les utilisateurs avancés qui veulent une flexibilité maximale et un accès aux versions les plus récentes des logiciels.

Chaque distribution a ses propres forces et faiblesses, et le choix dépend de vos priorités en termes de stabilité, de mise à jour des logiciels, de support et de facilité d'utilisation.

Création de la VM
====================================================

J'ai créé la VM moi-même dans le Proxmox à l'adresse suivante : <https://cfai2024.ajformation.fr:8006> avec mon compte préalablement créé.

Cette VM a les caractéristiques suivantes (j'ai coché la case "Advanced") :

-   **Name** : dynamic-baseline-bfayant
-   **Ressource Pool** : bfayant
-   **Start at boot** : Yes
-   **ISO** : Debian (latest)
-   **Disk Size** : 15Go
-   **VCPU** : 2
-   **RAM** : 2Go



d'Installation de Debian en Mode Non Graphique
====================================================

Pré-requis
----------

-   Média d'installation de Debian (CD, DVD, USB)
-   Connexion Internet (facultative mais recommandée pour installer les mises à jour)

Étapes de l'Installation
------------------------

### Étape 1 : Démarrage de l'Installation

1.  Insérez le média d'installation de Debian dans votre machine.
2.  Démarrez la machine et accédez au menu de démarrage pour démarrer à partir du média d'installation.
3.  Sélectionnez "Install" pour démarrer l'installation en mode texte.

### Étape 2 : Configuration Initiale

1.  **Sélection de la langue** :

    -   Choisissez votre langue (par exemple, Français).
2.  **Sélection du pays** :

    -   Choisissez votre pays (par exemple, France).
3.  **Configuration du clavier** :

    -   Sélectionnez la disposition du clavier (par exemple, Français).

### Étape 3 : Configuration du Réseau

1.  **Nom de la machine (hostname)** :

    -   Entrez un nom pour votre machine (par exemple, `debian`).
2.  **Nom de domaine** :

    -   Laissez vide ou entrez un nom de domaine si nécessaire.

### Étape 4 : Configuration des Utilisateurs

1.  **Mot de passe du superutilisateur (root)** :

    -   Entrez et confirmez le mot de passe pour l'utilisateur `root`.
2.  **Créer un utilisateur ordinaire** :

    -   Entrez le nom complet de l'utilisateur (par exemple, `Utilisateur`).
    -   Entrez le nom d'utilisateur (par exemple, `user`).
    -   Entrez et confirmez le mot de passe de l'utilisateur.

### Étape 5 : Configuration des Partitions

1.  **Sélection du disque** :

    -   Sélectionnez le disque pour l'installation (par exemple, `/dev/sda`).
2.  **Choisissez le partitionnement manuel**.

#### Créer la partition pour `/boot`

1.  **Nouvelle partition** sur `/dev/sda` :
    -   Taille : 1GB
    -   Type : Primaire
    -   Système de fichiers : ext4
    -   Point de montage : /boot

#### Créer la partition pour LVM

1.  **Nouvelle partition** sur `/dev/sda` :
    -   Taille : reste de l'espace disponible
    -   Type : Primaire
    -   Configurer comme : partition physique pour LVM

#### Configurer LVM

1.  **Configurer le LVM** :
    -   Utiliser l'espace de la partition LVM pour créer un groupe de volumes (VG) nommé `vg0`.

#### Créer les volumes logiques dans LVM

1.  **Volume logique pour `/`** :

    -   Nom : `root`
    -   Taille : 10GB
    -   Système de fichiers : ext4
    -   Point de montage : /
    -   Label : root
2.  **Volume logique pour `swap`** :

    -   Nom : `swap`
    -   Taille : 2GB
    -   Système de fichiers : swap
    -   Point de montage : swap
    -   Label : swap
3.  **Volume logique pour `/websites`** :

    -   Nom : `websites`
    -   Taille : reste de l'espace disponible
    -   Système de fichiers : xfs
    -   Point de montage : /websites
    -   Label : websites

#### Finaliser le partitionnement

1.  **Vérifiez** les partitions et les volumes logiques :
    -   `/dev/sda1` : 1GB, ext4, monté sur `/boot`
    -   `/dev/sda2` : partition physique pour LVM
        -   `vg0-root` : 10GB, ext4, monté sur `/`, label `root`
        -   `vg0-swap` : 2GB, swap, monté sur `swap`, label `swap`
        -   `vg0-websites` : reste de l'espace, xfs, monté sur `/websites`, label `websites`
2.  **Appliquez les changements**.

### Étape 6 : Installation du Système de Base

1.  **Sélectionner le miroir de l'archive Debian** :

    -   Choisissez un miroir proche de votre localisation pour télécharger les paquets.
2.  **Configurer le gestionnaire de paquets** :

    -   configurez l'utilisation d'un serveur ssh.
### Étape 7 : Configuration du Gestionnaire de Paquets

1.  **Participer au sondage sur l'utilisation des paquets** :
    -   Choisissez si vous souhaitez participer ou non.

### Étape 8 : Sélection des Logiciels

1.  **Sélection des logiciels** :
    -   Choisissez "Système standard" uniquement pour une installation en mode CLI.

### Étape 9 : Installation du Chargeur de Démarrage

1.  **Installer le chargeur de démarrage GRUB** :
    -   Choisissez d'installer GRUB sur le disque (par exemple, `/dev/sda`).

### Étape 10 : Finaliser l'Installation

1.  Une fois l'installation terminée, redémarrez votre machine.
2.  Retirez le média d'installation.

Utilisation de Debian en CLI
----------------------------

Après le redémarrage, vous serez accueilli par l'invite de connexion en ligne de commande (CLI). Connectez-vous avec l'utilisateur créé pendant l'installation.


### d'installation des logiciels demander sur Debian

Assurez-vous d'avoir les privilèges root pour effectuer ces installations. Vous pouvez utiliser `sudo` pour chaque commande si vous n'êtes pas connecté en tant que root.

1.  **Mettez à jour le système** :

    bash

-   `sudo apt update
    sudo apt upgrade -y`

    -   **Installer le serveur SSH** :

    bash

`sudo apt install -y openssh-server`

Pour vérifier que le serveur SSH fonctionne correctement :

bash

-   `sudo systemctl status ssh`

    -   **Installer les outils de compilation** (gcc, make, etc.) :

    bash

    -   `sudo apt install -y build-essential`

    -   **Installer le serveur SNMP** :

    bash

`sudo apt install -y snmpd`

Pour configurer le serveur SNMP, éditez le fichier `/etc/snmp/snmpd.conf` selon vos besoins et redémarrez le service :

bash

-   `sudo systemctl restart snmpd
    sudo systemctl enable snmpd`

    -   **Installer Apache** :

    bash

    -   `sudo apt install -y apache2`

    Pour vérifier que le serveur Apache fonctionne, ouvrez un navigateur web et accédez à `http://votre_ip`.

    -   **Installer MySQL** :

    bash

`sudo apt install -y mysql-server`

Après l'installation, exécutez la commande suivante pour sécuriser votre installation MySQL :

bash

-   `sudo mysql_secure_installation`

    Suivez les instructions à l'écran pour configurer le mot de passe root de MySQL et sécuriser votre installation.

    -   **Installer PHP** (dernière version compatible avec Apache) :

    bash

`sudo apt install -y php libapache2-mod-php php-mysql`

Pour vérifier l'installation de PHP, créez un fichier de test :

bash

1.  `echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php`

    Ensuite, ouvrez un navigateur web et accédez à `http://votre_ip/info.php`. Vous devriez voir une page d'information sur PHP.

### Résumé des commandes

Voici un résumé de toutes les commandes pour une installation rapide :

bash

`sudo apt update
sudo apt upgrade -y

sudo apt install -y openssh-server
sudo systemctl status ssh

sudo apt install -y build-essential

sudo apt install -y snmpd
sudo systemctl restart snmpd
sudo systemctl enable snmpd

sudo apt install -y apache2

sudo apt install -y mysql-server
sudo mysql_secure_installation

sudo apt install -y php libapache2-mod-php php-mysql
echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php`

Ce guide vous aidera à installer et configurer un serveur SSH, les outils de compilation, le serveur SNMP, Apache, MySQL et PHP sur Debian.



### Ajouter les adresses IPv6 supplémentaires

Utilisez `nmcli` pour ajouter les nouvelles adresses IPv6 à l'interface `ens18`.

bash

`sudo nmcli con mod ens18 +ipv6.addresses "2a03:5840:111:1024::7/64"
sudo nmcli con mod ens18 +ipv6.addresses "2a03:5840:111:1024::8/64"`

| FQDN | Adresse IPv6 | Utilisation |
| :-: | :-: | :-: |
| dynamic-baseline.vm.cfai24.ajformation.fr. | 2a03:5840:111:1024:7a97:cf98:662:cc59 | Accès SSH |
| dynamic-baseline.web.cfai24.ajformation.fr. | 2a03:5840:111:1024::7 | Site web vitrine |
| dynamic-baseline.admin.cfai24.ajformation.fr. | 2a03:5840:111:1024::8 | Site web de gestion |


