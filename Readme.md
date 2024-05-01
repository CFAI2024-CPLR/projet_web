# Projet Web

## Méthode de rendu

Merci de créer une branche spécifique à chaque utilisateur : work/pnom

exemple : Bernard Cervantes -> branche **work/bcervantes**

Vous travailler dans votre branche

Votre branche doit contenir un dossier nommé <NOM_Prénom> (exemple **CERVANTES_Bernard**)

### Vos commits

Les commits doivent être lisible, clair et "propre"

- chaque modification doit être décrite en un minimum de mot dans le titre du commit
    - e.g. : *Activité : Configuration du serveur web*
- chaque commit doit contenir uniquement les fichiers ou modifications propres à l'activité

### Un fichier text markdown : **Readme.md**

Dans votre dossier **<NOM_Prénom>** le fichier **Readme.md** contiendra les renseignements suivants :

- Identité : Vos noms et prénoms
- Journal de chaque activité
    - Titre de l'activité
    - Temps de réalisation : Le temps nécessaire à remplir la mission ( à la 1/2h près )
    - travaux réalisés
    - Le commit correspondant et le lien vers ce commit
    - Un lien vers le fichier de configuration final (si nécessaire)
- Pour chaque utilisateur : 
    - Les logins et mot de passe de touts les utilisateurs (root compris), à l'exception du votre
    - La configuration ssh permettant de se connecter à la VM en format ssh/config (pas d'IPs uniquement les FQDN)

> note : L'orthographe et la grammaire doivent faire l'objet d'une attention suffisante.
>
> Sans être notée, elle peut faire varier l'humeur de l'examinateur. 
>
> Pensez à vous relire.

### Un fichier yaml : **administration.yaml**

Dans votre dossier **<NOM_Prénom>** le fichier **administration.yaml** contiendra les informations suivantes

```yaml
administrateur: 
  identite: Prénom Nom
  login: pnom
machine:
  fqdn: [fqdn]
utilisateurs:
  - login: webmaster
    passwd: ...
  - login: root
    passwd: ...
    ...
services:
    - name: ssh
      version: ...
    - ...
sites_web:
    - type: vitrine
      chemin: /websites/vitrine/
      url: http://...
      login: [si besoin]
      password: [si besoin]
    - type: gestion
      chemin: /websites/vitrine/
      url: http://...
      login: ...
      ...

```

### Les fichiers de configuration de chaque service

Ne mettre que les fichiers pertients

exemple : 

```
serveur_web
├── config
│   ├── nginx.conf
│   └── sites-enabled
│       ├── gestion.conf
│       └── vitrine.conf
└── sites
    ├── gestion
    │   └── config.php
    └── vitrine
        └── config.php
serveur_bdd
└── mysql.cnf


```

## Finalisation

Vous serez noté sur le pull request que vous créerez à la fin,

- Il doit contenir des commits propres, clairs et lisibles
- Les fichiers demandés doivent être présent
- Les accès ssh doivent être fonctionnels
- Les sites demandés doivent être fonctionnels

> :warning: **ATTENTION !** Je ne vous demande pas de FAIRE des sites webs, les sites peuvent être vides ! 
> :warning: 
> :warning: Ils doivent néanmoins être fonctionnel pour les fournir au client {{ data.web.entreprise }}


Votre PULL REQUEST sera étudié seulement s'il arrive avant le **jeudi 16 mai à 23h50**

Sinon c'est considéré comme 0/20.

Je vous conseille de ne pas "rusher", et de faire les activités petit à petit.

:warning:

En cas de problème : **N'hésitez pas à m'envoyer un email ou me contacter sur Discord**
