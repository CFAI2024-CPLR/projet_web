# Auteur : CAGNOLATI Solène

# Journal d'activités

## Création de la machine virtuelle

* [Documentation](Documentation/CreationVM.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/ee1f51b4e8120ebf0751ce2b4bdc460b15749143)

- **Temps de réalisation** : 30m
- **Travaux réalisés** : 
    - Paramétrage de la machine virtuelle
    - Création de la machine virtuelle

## Installation du système d'exploitation

* [Documentation](Documentation/InstallationOS.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/7ea530892a364a7fb911b505b9d37874462ee280)

- **Temps de réalisation** : 1h
- **Travaux réalisés** : 
    - Configuration des locales
    - Configuration de la machine
    - Configuration des utilisateurs principaux
    - Partitionnement et formatage du disque
    - Installation des logiciels essentiels
    - Installation du système d'exploitation

## Configuration du réseau

* [Documentation](Documentation/ConfigurationReseau.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/d55b24db605d06f0ba5dc5d9474724dca078134b)
* [/etc/network/interfaces](Configuration/interfaces)

- **Temps de réalisation** : 30m
- **Travaux réalisés** : 
    - Déterminer l'adresse IPv6 SLAAC
    - Choix d'une adresse IPv6 fixe pour les sites web
    - Paramètrage des adresses IPv6 fixes
    - Configuration du réseau
    
## Configuration du SSH

* [Documentation](Documentation/ConfigurationSSH.md)
* [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/e212cfb81c64bf07cccfba2d2408cb0df28b0c63)
* [/etc/ssh/sshd_config](Configuration/sshd_config)

- **Temps de réalisation** : 1h
- **Travaux réalisés** : 
    - Interdiction de la connexion en SSH via l'utilisateur root
    - Autorisation de la connexion SSH uniquement depuis l'adresse IPv6 **2A03:5840:111:1024:BC26:11FF:FE46:D54D**
    - Création d'une clé SSH pour la connexion
    - Interdiction de se connecter via un mot de passe
    - Configuration du SSH