# Auteur : Titouan Bonnet Plomb

### Installation des services

Pour installer les services nous passerons par le gestionnaire de paquet APT voici les commandes utilisé :
(A noter que nous avons déjà installer le serveur SSH dans la configuration de la VM donc pas besoin de le reinstaller)

Outils de compilation : 
```apt install gcc gdb make```

SNMP Serveur :
```apt install snmp snmpd```

Apache :
```apt install apache2```

MySQL (MariaDB)
```apt install mariadb-server```

PHP
```apt install php8.2```