# Projet Web
## Identité

Nom: COSTON

Prénom: Lenny

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
