# Auteur : Titouan Bonnet Plomb
Si tu regardes ce commit c'est que tu es trop curieux :)

### Choix de la langue et selection des parametres regionaux

![Image 1](../pics/creation%20vm/choix_langue.png)
*Image 1*

Voici la première étape de l'installation d'un OS Debian (*Image 1*), nous devons selectionné la langue souhaité (ici français).

![Image 2](../pics/creation%20vm/choix_regional.png)
*Image 2*

Ensuite nous devons selectionné la region dans laquelle nous nous trouvons (*Image 2*) ici nous choisirons la France avec un grand F

![Image 3](../pics/creation%20vm/choix_clavier.png)
*Image 3*

Nous devons choisir maintenant la disposition du clavier (*Image 3*) nous choisirons la disposition du clavier en AZERTY français #BépoHateAccount

### Partie Réseau et utilisateur

![Image 4](../pics/creation%20vm/choix_domaine.png)
*Image 4*

Nous rentrerons dans cette partie le FQDN donnée dans le sujet (*Image 4*)

![Image 5](../pics/creation%20vm/choix_nom_complet.png)
*Image 5*

Nous renseigneront ici (*Image 5*) le(s) nom et prénom(s) de l'utilisateur principal (dans l'ordre que vous souhaitez)

Quant au champ de l'*Image 6*, il faudra rentrer le nom d'utilisateur de l'utilisateur principal qui sera utilisé pour se connecter en SSH à la machine ou tout simplement se logger sur le shell

![Image 6](../pics/creation%20vm/choix_identifiant.png)
*Image 6*

### Partitionnement du disque

![Image 7](../pics/creation%20vm/choix_partitionnement.png)
*Image 7*

Dans notre cas (*Image 7*), nous ferons un partitionnement manuel du disque afin de divisé le disque comme nous le souhaitions

![Image 8](../pics/creation%20vm/choix_disk.png)
*Image 8*

(*Image 8*) Nous choisirons le disque présent sur le système (en rouge) pour le partitionnement. Une fenetre apparait en nous demendant si l'on veut créer une nouvelle table de parition, ce a quoi nous répondrons oui

![Image 9](../pics/creation%20vm/choix_partition.png)
*Image 9*

Une fois cela fait, une nouvelle ligne apparait (*Image 9*). Il s'agit de la partion que nous avons créer mais il faut encore la formater et l'attribuer à un point de montage.

![Image 10](../pics/creation%20vm/choix_type.png)
*Image 10*

Dans notre example, nous ferons uniquement la partition de boot monté sur /boot. Il faudrat choisir de créer une partition Primaire (*Image 10*). 

![Image 11](../pics/creation%20vm/choix_taille.png)
*Image 11*

Nous choisirons la taille de la partition de boot, étant donnée que cela est une partition de boot nous lui attriburons 1GB d'espace pour ne pas gaspiller les 15 GB (*Image 11*)

![Image 12](../pics/creation%20vm/config_partition_example.png)
*Image 12*

Nous devrions arriver sur ce menu pour configurer notre partition (*Image 12*) La première ligne en rouge, nous permettra de choisir le type de partition, ici ca sera une partition de type EXT4. La deuxième ligne défini le point de montage de la partition ici cela sera /boot, nous lui donnerons comme étiquette "boot" et pour finir, nous définirons la ligne "Indicateur d'amorcage" sur "Présent" et nous pourrons valider la partition.

Le reste des partitions se configure de la même facon uniquement le type de partition et le point de montage diffère.

Une fois toutes les partitions créer nous n'aurons plus qu'à valider la table de partitionnement.

### Fin de la configuration de la VM

Après avoir partitionner le disque il ne vous reste plus qu'à laisser les parametre par défaut sur les dernières questions.

Enjoy ;)