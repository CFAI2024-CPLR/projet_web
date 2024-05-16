# identité : Grange Estelle

# Ordre de mission
- temps de réalisation : 15 min

- traveaux realisés :
    - Analyse du besoin du client avec l'odre de mission
    - prise de note

# creation de la VM
- temps de réalisation : 25 min

- traveaux realisés :
    - creation de la VM sur Proxmox
    - prise de note

    * [Documentation](documentation/Creation-VM-Rocky.md)
    * [Commit](https://github.com/CFAI2024-CPLR/projet_web/commit/c568257da6ac66c5088469404f08e9a20253864e#)

   *Note* : Je n'ai pas réussi a faire un commit bien propre, malgrès mes nombreuses tentatives. Je me suis même demandé si avec **git rebase -i HEAD~NBR** , je pouvais réllement supprimer un commit sur le depot origin. Sur le projet, j'avais environs 13 commit et j'ai voulu en supprimer en utilisant squash afin de fussionner mes commits , drop pour les supprimer et pick pour "valider", cependant, à chaque merge, ou git rebase --continue, celà me créer des nouveau commits. 

   *Reflexion sur git* : Peut être que la commande git rebase -i Head~NBR ne permet pas de supprimer un commit direcment ( car c'est important de garder un historique même si nous avons fait des erreurs), mais permet de créer un commit propre avec des commits qui ont été supprimés ou fussionnés. Ainsi, celà augmente le nombre de mes commits quand je push même avec push --force.  

# Installation du système d'exploitation

- temps de réalisation : 35 min

- traveaux realisés :
    - Installation de L'OS et partionnement du disque
    - prise de note

    * [Documentation](documentation/Creation-VM-Rocky.md)