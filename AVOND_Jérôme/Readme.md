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

```

