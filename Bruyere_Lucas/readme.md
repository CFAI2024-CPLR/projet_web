2a03:5840:111:1024:934b:13ce:7c62:d645

# Etape 1 : Création de la VM Debian

## **Paramétrer la VM :**

<p><u>Etape 1 : Général :</u></p>

![Etape 1](./Images/Création%20VM/Création%20de%20la%20vm%201.png "Général")

<p><u>Etape 2 : Système d'exploitation :</u></p>

![Etape 2](./Images/Création%20VM/Création%20de%20la%20vm%202.png "Système d'exploitation")

<p><u>Etape 3 : Système :</u></p>

![Etape 3](./Images/Création%20VM/Création%20de%20la%20vm%203.png "Système")

<p><u>Etape 4 : Disques :</u></p>

![Etape 4](./Images/Création%20VM/Création%20de%20la%20vm%204.png "Disques")

<p><u>Etape 5 : Processeur :</u></p>

![Etape 5](./Images/Création%20VM/Création%20de%20la%20vm%205.png "Processeur")

<p><u>Etape 6 : Mémoire :</u></p>

![Etape 6](./Images/Création%20VM/Création%20de%20la%20vm%206.png "Mémoire")

<p><u>Etape 7 : Réseau :</u></p>

![Etape 7](./Images/Création%20VM/Création%20de%20la%20vm%207.png "Réseau")

<p><u>Etape 8 : Confirmation :</u></p>

![Etape 8](./Images/Création%20VM/Création%20de%20la%20vm%208.png "Confirmation")

## **Partitionner les disques :**

* 1 partition primaire de taille 1GB de type ext4 montée sur / et labellisé boot
* 1 partition lvm taille 10GB de type ext4 montée sur / et labellisé root
* 1 partition lvm taille 2GB de type swap montée sur swap et labellisé swap
* 1 partition lvm taille reste de type   xfs  montée sur /websites et labellisé websites

<p>Une fois cela fait nous allons ajouter les logiciels que nous aurons besoins.</p>

## **Choix des logiciels à installer**

* serveur ssh
* serveur web

<p>De plus le nom de domaine à été designer lors de l'instalation que voici : cfai24.ajformation.fr </p>

# Etape 2 : Ajout des utilisateurs avec leurs rôles :

## **Passer lbruyere en administrateur :**

1. Se connecter en tant que root :
    ```bash
        su -
    ```
    Entrez le mot de passe du compte root.

2. Ajouter "lbruyere" au groupe sudo :
    ```bash
        usermod -aG sudo lbruyere
    ```

3. Vérifier que "lbruyere" a été ajouté au groupe sudo :
    Vous pouvez vérifier que "lbruyere" a été ajouté au groupe sudo en affichant les informations de groupe pour "lbruyere".   
    ```bash
        id lbruyere
    ```
    Vous devriez voir "sudo" dans la liste des groupes auxquels appartient "lbruyere".

4. Déconnectez-vous de la session root :
    Une fois "lbruyere" ajouté au groupe sudo, vous pouvez vous déconnecter de la session root.
    ```bash
        exit
    ```

5. Testez les droits sudo de l'utilisateur "lbruyere" :
    Connectez-vous maintenant avec le compte "lbruyere" et testez les droits sudo pour vous assurer que les modifications ont été prises en compte.
    ```bash
        sudo ls
    ```

<p>Une fois l'utilisateur lbruyere défini en tant qu'administrateur nous pouvons créer les autres utilisateur ainsi que leur groupes depuis l'utilisateur lbruyere</p>

## **Crééer les differents groupes et utilisateurs :**

1. Créer un utilisateur
    Utilisez la commande adduser pour créer un nouvel utilisateur.

    ```bash
        sudo adduser cdaniels
    ```
    ```bash
        sudo adduser lpfeiffer
    ```
    Suivez les instructions à l'écran pour définir un mot de passe et fournir des informations supplémentaires sur l'utilisateur si nécessaire.


2. Créer des groupes
    Utilisez la commande addgroup pour créer un nouveau groupe.

    ```bash
        sudo addgroup vitrine
    ```
    ```bash
        sudo addgroup gestion
    ```

3. Ajouter des utilisateurs à des groupes
    Utilisez la commande adduser avec l'option --ingroup pour ajouter un utilisateur à un groupe existant.

    ```bash
        sudo adduser cdaniels vitrine
    ```
    ```bash
        sudo adduser lpfeiffer gestion
    ```

# Etape 3 : Fixer l'IPV6 :

## **Rendre fixe l'IPV6 :**

1. Ouvrir le fichier de configuration réseau :
    ```bash
        sudo nano /etc/network/interfaces.d/50-cloud-init.cfg
    ```

2. Ajouter la configuration pour l'adresse IPv6 fixe :
    Ajoutez les lignes suivantes à la configuration de votre interface réseau.

    ```plaintext
        iface ens18 inet6 static
            address 2a03:5840:111:1024:934b:13ce:7c62:d645
            netmask 64
    ```

3. Redémarrer le service réseau :
    Après avoir enregistré les modifications, redémarrez le service réseau pour appliquer les nouveaux paramètres.

    ```bash
        sudo systemctl restart networking
    ```

4. Vérifier la configuration :
    Vérifiez que l'adresse IPv6 a été configurée correctement en exécutant la commande suivante :

    ```bash
        ip addr show dev ens18
    ```
    Vous devriez voir votre adresse IPv6 listée dans les résultats, avec l'état "UP".

5. Tester la connectivité :
    Testez la connectivité IPv6 en essayant de pinguer une adresse IPv6 accessible sur Internet, par exemple :

    ```bash
        ping6 ipv6.google.com
    ```