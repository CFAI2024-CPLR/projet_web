
# Identité : Mattéo Charrin 

--- 

##  1) Création d'une VM RockyLinux *Temps : 10min*


Une fois connecté à Proxmox, cliquez en haut à droite sur "Create VM", puis configurez-la avec les paramètres demandés précédemment.
![](Images/1/Arc_6RekT5Xylv.png)
![](Images/1/Arc_s3O9UWUV9a.png)
![](Images/1/Arc_E2CTxJ23oE.png)
![](Images/1/Arc_jqD8nDkWbN.png)
![](Images/1/Arc_WYLzmLm0mR.png)

## 2) Partitionnement de la VM *Temps :  25min* 

Une fois la VM lancer une choisis la langue de la machine. Ici le Français puis on arrive sur l'interface de configuration  
![](Images/2/Arc_2zxbuFqZNH.png)

En bas a droit on va crée un mot de passe **root** et crée un utilisateur (voir administration.yaml)

Puis passer aux partitionnement du disque 
On clique sur 'Installation Destination' puis on choisis notre disque et on coche la case 'Personnalisé' pour la configuration du stockage. 

![](Images/2/Arc_vtgQ0YEurM.png)

Une nouvelle fenêtre va s'afficher en nous demandant de crée notre premier partition 
Exemple pour la partition : 1 partition lvm taille 10GB de type ext4 montée sur / et labellisé root
![](Images/2/Arc_UPMaxMWwzL.png)

Une fois les 4 partitions montée : 
![](Images/2/Arc_t49Q38G2X7.png)
Pour finaliser on clique sur fait en haut a gauche et on accepte les modifications. 

Une fois toutes les config réaliser on clique sur "Commencer l'installation" en bas a droite de la fenetre
