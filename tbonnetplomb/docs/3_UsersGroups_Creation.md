# Auteur : Titouan Bonnet Plomb

Nous devons créer et gerer les différents utilisateurs sur le serveur web. Nous devrons aussi créer la hiérarchie des dossier et definir le propriétaire, le groupe propriétaire et les droits d'accès r w x

Voici les utilisateurs dont nous aurons besoin :
 - Le compte serveur web ici www-data
 - webmaster qui sera propriétaire des dossiers /websites/vitrine|/gestion
 - vredmond (Virginia Redmond)
 - lhervey (Linda Hervey)

Passons à la création des utilisateurs et des groupes :

` adduser *nom_utilisateur* `

Voila ce qu'on obtient après avoir rentrer cette commande : 

```
Ajout de l'utilisateur « example » ...
Ajout du nouveau groupe « example » (1007) ...
Ajout du nouvel utilisateur « example » (1007) avec le groupe « example » (1007) ...
Création du répertoire personnel « /home/example » ...
Copie des fichiers depuis « /etc/skel » ...
Nouveau mot de passe :
Retapez le nouveau mot de passe :
passwd : mot de passe mis à jour avec succès
Modifier les informations associées à un utilisateur pour example
Entrer la nouvelle valeur, ou appuyer sur ENTER pour la valeur par défaut
        NOM []:
        Numéro de chambre []:
        Téléphone professionnel []:
        Téléphone personnel []:
        Autre []:
Cette information est-elle correcte ? [O/n]
```

Nous rentrerons les informations lié a chaque utilisateur.

Nous devons maintenant créer les groupe suivants :
 - clpr
 - vitrine (pour le site de gestion)
 - gestion (pour le site vitrine)

Pour faire cela on utilisera la commande `addgroup *nom_du_groupe*`

Nous devons rajouter maintenant les utilisateurs aux groupes. La répartition des utilisateurs est dans le mail du sujet.

`usermod -aG *nom_groupe* *nom_utilisateur*`

Maintenant nous devons créer les dossiers vitrine/ et gestions/ avec la commande mkdir et designer les propriétaire du dossier.

Pour cela nous utiliserons la commande 

`chown *nom_groupe*:*nom_utilisateur* vitrine/|gestion/|/websites/`

Pour finir, nous devons configurer les droits R W X sur chaque dossier. 

Pour rappel, les droits unix se configure avec un nombre à trois chiffre, chaque chiffre correspond au niveau d'accès d'un groupe.

nous pouvons retrouver cette information avec un `ls -l`

![Image](../pics/droits%20unix/droits_unix.png)

En jaune les droits unix d'un dossier (ici /etc) :

 - la lettre d spécifie que c'est un dossier
 - les trois caractères suivant définisse les droits d'accès du propriétaire ici lecture, écriture et execution
 - les trois suivants définisse les droits d'accès du groupe principal du dossier
 - enfin le reste défini les droits d'accès pour les utilisateurs n'étant ni propriétaire du dossier ni membre du groupe principal.

Chaque chiffre est une addition des droits :

 - R = 4
 - W = 2
 - X = 1

Le chiffre 7 indique un accès en lecture, écriture et execution

Exemple : dans le nombre 750 : 

 - le chiffre 7 attribue un accès RWX (4 + 2 +1)
 - le chiffre 5 un accès RX (4 + 1)
 - et le chiffre 0 attribue aucun accès.

Pour parametrer les droits on utilisera la commande `chmod 775 *nom_dossier*`

Nous avons finis avec la création et attribution des dossiers