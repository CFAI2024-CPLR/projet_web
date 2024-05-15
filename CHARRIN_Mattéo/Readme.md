
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

Une fois toutes les config réaliser on clique sur "Commencer l'installation" en bas a droite de la fenêtre

## 3) Mise en réseau de la VM 20min

Pour commencer on va aller chercher les infos pour savoir le nom de la carte reseau et l'adresse IPV6 deja utiliser par SLAA 

```shell
ip a
```

Une fois la commande réaliser on peut trouver comme info : 
- Nom de la carte : ens18 
- adresse ipv6 2a03:5840:111:1024:be24:11ff:fe83:9395/64 

Maintenant on peut ajouter une nouvelle adresse ip avec la commande 
```shell 
sudo nmcli con mod ens18 ipv6.addresses '2a03:5840:111:1024:be24:11ff:fe83:9395/64, 2a03:5840:111:1024::21/64 '
```
Puis cette commande afin d'activer la connexion : 
```shell 
sudo nmcli con up ens18
```
## 4) Création des Groupes et affectation au dossier 30min 

On va avoir besoin de nginx pour faire les groupes donc on va directement installer le paquet 
```shell 
sudo dnf install nginx
```


On commence par crée les différents groupes avec ces commandes 

```shell 
sudo groupadd cplr
sudo groupadd vitrine
sudo groupadd gestion
```

Ensuite on va crée les utilisateurs et gérer leurs mot de passe 
```shell
sudo adduser webmaster
sudo adduser cchampagne
sudo adduser bcramer
---
sudo passwd webmaster
sudo passwd cchampagne
sudo passwd bcramer
```

Puis ajouter les différent utilisateurs a leur groupes :
```shell
sudo usermod -aG vitrine webmaster
sudo usermod -aG vitrine mcharrin
sudo usermod -aG vitrine cchampagne
---
sudo usermod -aG gestion webmaster
sudo usermod -aG gestion mcharrin
sudo usermod -aG gestion bcramer
```

Ensuite on crée les différents sous-dossier de websites 
```shell
sudo mkdir -p /websites/vitrine /websites/gestion
```

Et on viens ajouter les propriétaires et groupes a ces dossier 
```shell
sudo chown apache:cplr /websites
sudo chown webmaster:vitrine /websites/vitrine
sudo chown webmaster:gestion /websites/gestion
```

puis on corrige les droit avec chmod 

```shell 
chmod 775 /websites
chmod 775 /websites/vitrine
chmod 775 /websites/gestion
```


## 5) Enregistrement DNS 

On suit les instruction disposer sur le site :  http://ns1.cfai2024.ajformation.fr:5000/

![](Images/5/Arc_gEi3nsWKhJ.png)

On fait sa pour les 3 Nom / Ipv6 : 
- [product-metrics.vm.cfai24.ajformation.fr](http://product-metrics.vm.cfai24.ajformation.fr/)
- [http://product-metrics.web.cfai24.ajformation.fr](http://product-metrics.web.cfai24.ajformation.fr/)
- [http://product-metrics.admin.cfai24.ajformation.fr](http://product-metrics.admin.cfai24.ajformation.fr/)
