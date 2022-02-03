# proxmox-setup
proxmox-setup

> Simplified installation of a [proxmox](https://www.wireguard.com/) hypervisor (tested on T460s+16GB+512SSD)

*NB: Below are the setup document for setting up proxmox hypervisor

Usefull commadss:

    ssh ubuntu@1.2.3.4

Remove LVM disk , run:

to remove LVM Volume

lvremove 

Type y for yes

to use remainign full disk ( 100% disk space )
lvresize -l +100%FREE /dev/pve/root

to make it permentant 
resize2fs /dev/mapper/pve-root

