- Identité : Bureau Mathis

# Activité 1 : création de la VM et Configuration Rocky Linux (temps total additionné : 20min)

## Connexion à proxmox et création VM (temps passé : 10min)

- Se connecter à ProxMox et effectuer un clic-droit sur "cfai-2024" et "create VM".

- Suivre les instruction jusqu'à arriver à ce résultat :

![image](./images/proxmoxconfig.jpg)

- Démarrer la VM

## Configuration rocky linux (temps passé : 10min)

- Suivre les instructions d'installation :
    - Définir pwd root
    - Définir utilisateur mbureau administrateur
    - Définir la gestion des partitions (voir image suivante)
    - Confirmer et attendre l'installation 
    - Redémarrer la VM et se connecter

![image](./images/partitions.jpg)

![image](./images/rockyinstall.jpg)

 
# Activité 2 : COnfiguration du réseau

## Ajout des ipv6 
- Récupérer l'ipv6 automatique (2a03:5840:111:1024:be24:11ff:fe6d:f34a)
- Sur Rocky utiliser le CLI NetworkManager pour ajouter 2 ip
    - 2a03:5840:111:1024::7/64 (web)
    - 2a03:5840:111:1024::8/64 (admin)
- Utiliser les commande suivante :
- nmcli connection edit ens18

```
set ipv6.addresses 2a03:5840:111:1024::7/64, 2a03:5840:111:1024::8/64
save
quit

```

- Redémarrer le service NetworkManager (sudo systemctl restart NetworkManager)
- Vérifier le résultat avec "ip -6 addr show"

## Ajout dans le DNS
- Suivre les instructions du site "http://ns1.cfai2024.ajformation.fr:5000"

![image](./images/DNS.jpg)