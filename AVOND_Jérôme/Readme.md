# Projet Web

## Création branche git 2024-05-17 00:00

## Création VM 2024-05-17 00:00

## Accès SSH

- Installation de qemu-guest-agent
- Activation de guest agent dans options
- stop / restart VM
- IP : 2a03:5840:111:1024:be24:11ff:fe1a:dbd9
- DNS : forward-brass.vm.cfai24.ajformation.fr.

```confssh
Host forward-brass.vm.cfai24.ajformation.fr
    Hostname forward-brass.vm.cfai24.ajformation.fr.
    User javond
```

## Ajout IP manuelle

- Choix IP : 2a03:5840:111:1024::f1fa/64
- Test nmap : OK


- dns :
    - forward-brass.web.cfai24.ajformation.fr.
    - forward-brass.admin.cfai24.ajformation.fr

## Set hostname

```shell
[root@localhost ~]# hostnamectl hostname forward-brass.vm.cfai24.ajformation.fr
[root@localhost ~]# hostnamectl status
 Static hostname: forward-brass.vm.cfai24.ajformation.fr
       Icon name: computer-vm
         Chassis: vm 🖴
      Machine ID: 3d7c37c4fcee484ea39e197890c7faaa
         Boot ID: fdd971a046c34c059cdff143b93239de
  Virtualization: kvm
Operating System: Rocky Linux 9.4 (Blue Onyx)                 
     CPE OS Name: cpe:/o:rocky:rocky:9::baseos
          Kernel: Linux 5.14.0-427.16.1.el9_4.x86_64
    Architecture: x86-64
 Hardware Vendor: QEMU
  Hardware Model: Standard PC _i440FX + PIIX, 1996_
Firmware Version: rel-1.16.2-0-gea1b7a073390-prebuilt.qemu.org
[root@localhost ~]# reboot

```

## Création des dossiers

```shell
[root@forward-brass ~]# mkdir -p /websites/{vitrine,gestion}
```

## Créations des utilisateurs


- webmaster : compte service
- krumsey   : Utilisateur, gestion du site vitrine
- jdiga     : Utilisateur, gestion du site de gestion

```csv
webmaster ru8IaHeifahZ5ahz
krumsey Kutushooc2quaevo
jdiga ieSahyohSevei8oh
```

> :warning: ```pwgen -s 16``` **is the B3a5t**

```shell
[root@forward-brass ~]# cat > /tmp/users
webmaster ru8IaHeifahZ5ahz
krumsey Kutushooc2quaevo
jdiga ieSahyohSevei8oh
[root@forward-brass ~]# while read user pass
> do
> useradd -m $user
> chpasswd <<< "${user}:${pass}"
> done
[root@forward-brass ~]#

```

## Création des groupes

- cplr      : compte général
- vitrine   : gestion du site vitrine
- gestion   : gestion du site de gestion

```csv
cplr    javond
gestion webmaster,jdiga,javond
vitrine webmaster,krumsey,javond
```

```shell
[root@forward-brass ~]# cat > /tmp/groups
cplr    javond
gestion webmaster,jdiga,javond
vitrine webmaster,krumsey,javond
[root@forward-brass ~]# while read group users
> do
> groupadd ${group} -U ${users}
> done < /tmp/groups
```

## Affectation des dossiers

```shell
[root@forward-brass ~]# chown webmaster:vitrine /websites/vitrine/
[root@forward-brass ~]# chown webmaster:gestion /websites/gestion/
[root@forward-brass ~]# chmod u=rwx,g=rwx,o=rx /websites/
[root@forward-brass ~]# chmod u=rwx,g=rwx,o=rx /websites/vitrine/
[root@forward-brass ~]# chmod u=rwx,g=rwx,o=rx /websites/gestion/
```


