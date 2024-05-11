## Configuration du réseau

1. Déterminer l'IPV6 SLAAC :
L'IPP6 de notre VM est "2a03:5840:111:1024:be24:11ff:fea9:df45" comme on le voit ici grâce à un "ip addr" :

![Capture d'écran 2024-05-11 190919](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/12526d00-b4e2-4c26-a972-50d3d87dd072)

3. Choix de l'IPV6 pour les sites web :

Après consultation des IP des collègues, je choisis "2A03:5840:111:1024::31"

4. Paramétrages du réseau

Pour cela, on modifie le fichier /etc/network/interfaces :
![Capture d'écran 2024-05-11 191809](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/e0d0091e-3b01-4313-a945-d483130eec32)

et on vérifie si tout cela a été prit en compte :
![Capture d'écran 2024-05-11 191929](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/d2dd6f7b-30b1-4e2f-8025-b95541b9e0ee)
