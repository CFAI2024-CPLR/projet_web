# Configuration SSH

## Création d'une clé SSH
1. Je génère une clé SSH sur ma machine personnelle
![Capture d'écran 2024-05-13 191922](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/5c6a257f-abcc-4b37-8f17-28ef1ba9a290)

2. Puis je l'ajoute au serveur de ma VM
![Capture d'écran 2024-05-13 191945](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/72ff3d64-3efe-49cc-92b8-2386b35a585e)

3. Je vérifie si tout fonctionne correctement
![Capture d'écran 2024-05-13 191957](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/fdecc29b-aeb6-43e6-a13f-8e595872fb09)

## Ajout de la clé aux autres utilisateurs
### Nous ajoutons la clé SSH aux autres utilisateurs
webmaster :

![image](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/4d5fef4b-6bbc-4b4b-9556-f800ca4698a9)

rferretti :

![image](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/ec52db30-6ca4-4ec2-a551-a2b322427fb4)

cyerger :

![image](https://github.com/CFAI2024-CPLR/projet_web/assets/154502835/00574ed5-662b-4a8d-ab7a-c8552ef3849c)

## Ajout de la clé de notre formateur sur chaque utilisateur
Pour chaque utilisateur (webmaster, rferretti, cyerger) dans le dossier :

`~/.ssh/authorized_keys` 

j'ajoute cette ligne (clé de Mr Avond) :

`ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDWsfbTbSlxcvxUL1286nwhwrDPJq6bctkxPpZ+TyujHrDwyymvqEjMJNxiwDPRoomPgOcg+YYUYXbfRiLp0VNlUqA5oG9nhlgtiryZrWY6zrywnsDOk6wJvWA/YNbWLlFN14OiKXOH5KJpgYQh1pLIw1TPeR56vU5wv1Ggb0Jr1sg14TJgm2M4lSmQs1CAY8hBLDj/qQcwVNtuYqTXOulwCPZAzhP6ncHM7lHbwJua/3bGQ8IeFzjRGjL0s2XVECYPufCbM0cX1VtmaSQdVmwqXGW2c+rPAq8cFHecfaw/0fdSMeNV4qSl+VqpCGn/XXnpWAYi0OfifddH80ffdAp5 /home/jerome/.ssh/id_rsa`
