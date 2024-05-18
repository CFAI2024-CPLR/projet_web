Guide d'Installation de Debian en Mode Non Graphique
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

