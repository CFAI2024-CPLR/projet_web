# Installation des paquets

La machine doit disposer des logiciels suivants :

* serveur ssh
* outils de compilation (gcc,make...)
* snmp server
* **apache**
* **mysql**
* php (dernière version, fonctionne avec apache)

on ajoute dans le fichier `etc/apt/sources.list` les derniers dépôts disponibles pour debian 12 :

![fichier depots debian](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/155d904e-ea6c-4a40-8bda-bf33683c48c3)

### Installation serveur ssh
Le serveur SSH a été installé lors de l'installation de l'OS.

### Installation de GCC
`apt install -y gcc`

![installer gcc](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/8a97608f-3b81-4b27-bf58-c4556f42a095)

### Installation de Make
`apt install -y make`

![installer make](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/8c07fa33-937a-47d8-bafd-125507cba91f)

### Installation de php
`apt install -y php php-fpm php-mysql`

![installer php](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/f55618be-7d55-4b49-9056-78abad716ef6)

### Installation de snmpd server
`apt install -y snmpd`

![installer snmpd](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/60cdf668-1b43-460c-b548-09095250c32f)

On démarre le service et on vérifie s'il a demarré :
![activer snmpd](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/53236b56-73d2-4644-abd9-9dda1896d549)

### Installation de apache
`apt install apache2`

On démarre le service et on vérifie s'il a demarré :
![installer apache](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/4fd89cdf-8bb2-40e0-a0d6-8a815e999dd0)

### Instalaltion de mysql
Nous devons installer la version 8.0 de Mysql qui est comptabile avec Espocrm :

`wget https://dev.mysql.com/get/mysql-apt-config_0.8.30-1_all.deb
apt install -y ./mysql-apt-config_*_all.deb`

![wegt mysql](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/2991a8c9-2c9b-4f76-a1c0-bd2fc8feec61)
![installer mysql](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/2d1dfa85-2337-44a6-9d6a-48d00e171b2b)

![installer1 mysql](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/3c1d981b-3198-468e-b93f-d74bec4957bd)
![installer2 mysql](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/de6983ea-e312-4ed6-979b-74a6b145000d)
![installer3 mysql](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/2b8c6d3b-2dad-4276-b51b-5f4c3ef55c04)

On démarre le service et on vérifie s'il a demarré :
![demarrer mysql](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/d1e808c5-f679-4a91-8e1b-27d0579280c8)

# Installation des outils

Pour les sites web il faut installer les outils suivants :

- site vitrine : Jekyllrb
- site gestion : Espocrm
