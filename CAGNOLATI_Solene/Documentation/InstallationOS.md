# Installation du système d'exploiration

1. Configuration des locales

![Configuration des locales](../Images/InstallationOS/InstallationOs2.png)
![Configuration des locales](../Images/InstallationOS/InstallationOs3.png)
![Configuration des locales](../Images/InstallationOS/InstallationOs4.png)

2. Configuration de la machine

![Configuration de la machine](../Images/InstallationOS/InstallationOs5.png)
![Configuration de la machine](../Images/InstallationOS/InstallationOs6.png)

3. Configuration des utilisateurs principaux

![Configuration des utilisateurs principaux](../Images/InstallationOS/InstallationOs7.png)
![Configuration des utilisateurs principaux](../Images/InstallationOS/InstallationOs8.png)
![Configuration des utilisateurs principaux](../Images/InstallationOS/InstallationOs9.png)
![Configuration des utilisateurs principaux](../Images/InstallationOS/InstallationOs10.png)

4. Partitionnement et formatage du disque

Le partitionnement de la machine virtuelle devait être le suivant :
- Partition primaire **boot**
    - 1GB
    - EXT4
    - Montée sur /boot 
- Partition LVM **root**
    - 10GB
    - EXT4
    - Montée sur /
- Partiton LVM **swap**
    - 2GB
    - SWAP
    - Montée sur swap
- Partition LVM **websites**
    - Tout le reste (3GB)
    - XFS
    - Montée sur /websites

![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs11.png)
![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs14.png)
![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs15.png)
![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs16.png)
![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs17.png)
![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs19.png)
![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs20.png)
![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs21.png)
![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs22.png)
![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs23.png)
![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs24.png)

5. Installation des logiciels essentiels

![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs27.png)
![Partitionnement et formatage du disque](../Images/InstallationOS/InstallationOs29.png)