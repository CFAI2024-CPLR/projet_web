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