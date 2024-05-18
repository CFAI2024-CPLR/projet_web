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

