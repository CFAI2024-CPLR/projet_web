## Installtion de l'OS

1) Configuration
![Installation1](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/914f7c88-eff3-4af3-a9f0-accbcbf85c28)
![Installation2](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/f0fd2ff2-fe18-4a9d-8fac-b3fb9fd2ecb8)
![Installation3](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/e9485fc0-d947-435f-ba3a-5778fa906018)

2) Nommage de la machine
![Installation4](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/27bf9cd7-51c7-4ffe-ad66-084ef8bf54da)

3) Ajout du domaine
![Installation5](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/f5cf627b-e249-4c07-bd39-e8c76b8e287b)

4) Ajout du MDP du compte root
![Installation6](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/a612ced6-14ba-4c2b-bbcc-e0f883618cea)

5) Nom de l'utilisateur et identifiant
![Installation7](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/9955ce58-9f32-418c-b602-ecc0bea09d8f)
![Installation8](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/bd7ce84e-ccb6-44f7-8abc-ecd284ec27aa)

6) Partionnement des disques

Le partitionnement de la machine doit être le suivant :

* 1 partition primaire de taille 1GB de type ext4 montée sur /boot et labellisé boot       
* 1 partition lvm taille 10GB de type ext4 montée sur / et labellisé root
* 1 partition lvm taille 2GB de type swap montée sur swap et labellisé swap
* 1 partition lvm taille reste de type xfs montée sur /websites et labellisé websites

![Installation9](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/c4e173c3-0d79-4034-84b2-16850574219b)
![Installation10](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/4d598b16-34c7-41e4-b2a7-ccc2251c961b)
- création partition primaire
![Installation10bis](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/46f5e5c2-3598-4ef9-a882-9092f3375552)
![Installation11](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/f8d868fa-028e-4256-9d11-d582fe3272b6)
![Installation12](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/a7ca3f0f-6bba-4aa6-af3b-0543c8b33682)
- création du volume des groupes
![Installation13](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/4fe5bcd9-5796-4271-98b8-d5262c17284a)
![installation17](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/f25c8a1f-0c1e-44bd-bfca-daf2e7e2d13b)

7) Selection des logiciels
![Installation18](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/ee2d0f86-887e-4dd6-8f75-f46b9e14c00f)

8) Installation terminée
![Installation18](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/cb719433-84d8-4ae3-a109-5342daf81b1d)
