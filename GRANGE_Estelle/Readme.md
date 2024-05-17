# identité : Grange Estelle

# Ordre de mission
- temps de réalisation : 15 min

- traveaux realisés :
    - Analyse du besoin du client avec l'odre de mission
    - prise de note

# creation de la VM
- temps de réalisation : 25 min

- travaux realisés :
    - creation de la VM sur Proxmox
    - prise de note

    * [Documentation](documentation/Creation-VM-Rocky.md)
    * [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/c568257da6ac66c5088469404f08e9a20253864e#)

<u>*Note*</u> : Je n'ai pas réussi a faire un commit bien propre, malgrès mes nombreuses tentatives. Je me suis même demandé si avec **git rebase -i HEAD~NBR** , je pouvais réllement supprimer un commit sur le depot origin. Sur le projet, j'avais environs 13 commit et j'ai voulu en supprimer en utilisant squash afin de fussionner mes commits , drop pour les supprimer et pick pour "valider", cependant, à chaque merge, ou git rebase --continue, celà me créaient des nouveau commits. 

<u>*Reflexion sur git*</u> : Peut être que la commande git rebase -i Head~NBR ne permet pas de supprimer un commit direcment ( car c'est important de garder un historique même si nous avons fait des erreurs), mais permet de créer un commit propre avec des commits qui ont été supprimés ou fussionnés. Ainsi, celà augmente le nombre de mes commits quand je push même avec push --force.  

# Installation du système d'exploitation

- temps de réalisation : 35 min

- travaux realisés :
    - Installation de L'OS et partionnement du disque
    - prise de note

    * [Documentation](documentation/Creation-VM-Rocky.md)
    * [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/https://github.com/CFAI2024-CPLR/projet_web/commit/1ab0937c665d90b8dbe9ca0080989531d0f0b046#)


# configuration Réseaux

- Se connecter à la machine : `ssh  egrange@2a03:5840:111:1024:be24:11ff:fe74:c34b -i CheminDeLaCléPrive`

- temps de réalisation : 3h

- travaux realisés :
    - mise en place du SSH et des clés ( celle du proffesseur de Linux et la miennes)
       
        - Désactivation de l'accès root et par mot de passe.

        - Possibilité de se connecter en SSH uniquement avec l'addresse IPV6 **2a03:5840:111:1024:be24:11ff:fe74:c34b**

        - connexion uniquement par clé

    - creation de l'adresse IPv6 pour les sites web

    - creation des FQN

    - prise de note

    * [Documentation](documentation/3-Configuration%20-RESEAUX.md)

    * [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/6c9674af1488d8a343cbe168f36b612f46e8bf79)

    <u>*Note*</u> : Cette partie a pris plus de temps que prévu en raison de la longue durée des mises à jour des paquets, qui ont pris environ 40 minutes. En outre, la prise de notes a été laborieuse en raison  de la structure des informations et des captures d'écrans. J'aime organiser mes notes avec soin, ce qui a ajouté à la durée de la prise de notes. Cependant, une fois les mises à jour terminées, je n'ai rencontré aucune difficulté majeure. J'ai eu quelques problèmes lors de la création de l'adresse IPv6 avec la commande `nmcli`, mais j'ai finalement trouvé la solution.

    **Je réussis enfin à faire des commits propres ! C'est la fête ! 🎉**


# configuration des utilisateurs et des groupes

- **livraison en retard et ne respecte pas les délais.**

- temps de réalisation : 30 min

- travaux realisés :

    - ajoute de l'util'utilisateur egrange en sudo.

    - création les comptes suivants :

    - **webmaster** : compte service
    - **lberube** (Lori Berube ) : Utilisateur, gestion du site vitrine
    - **jjackson** (John Jackson): Utilisateur, gestion du site de gestion

- création les groupes suivants :

    - Groupe: **vitrine**
        - utilisateurs:
            - webmaster
            - egrange
            - lberube - Lori Berube

    - Groupe: **gestion**
        - utilisateurs:
            - webmaster
            - egrange
            - jjackson - John Jackson

    - prise de note

    * [Documentation](documentation/4-Creation-Utilisateur-Groupes.md)

    * [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/9ed83690d87c94e89c8b99553cb97fd662dc234d#)

    # configuration des outils et des services

    - **livraison en retard et ne respecte pas les délais.**

- temps de réalisation : 1H

- travaux realisés :

    -installations des outils suivants :
        - serveur ssh
        - outils de compilation (gcc,make...)
        - snmp server
        - apache
        - MariaDb
        - php8:2 (dernière version, fonctionne avec apache)

    - prise de note

    * [Documentation](documentation/5-Outils%20et%20services.md)

    * [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/e605b14a8e857bdd8e9c0a108a6c70e905fe4dad)

    # configuration du site PICOMS 

- temps de réalisation : 1H

- travaux realisés :

    - installation du site

    - prise de note

     * [Documentation](documentation/6-Sites-Webs.md)

    * [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/e605b14a8e857bdd8e9c0a108a6c70e905fe4dad)

*<u>note</u>* : problème de droits