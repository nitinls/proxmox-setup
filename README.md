# proxmox-setup
proxmox-setup

> Simplified installation of a [proxmox](https://www.wireguard.com/) hypervisor (tested on T460s+16GB+512SSD)

*NB: Below are the setup document for setting up proxmox hypervisor

Usefull commadss:

    ssh ubuntu@1.2.3.4

Remove LVM disk , run:

To remove LVM Volume:

    lvremove 

    Type y for yes

To use remainign full disk ( 100% disk space )
    
    lvresize -l +100%FREE /dev/pve/root

To make it permentant:

    resize2fs /dev/mapper/pve-root



## Questions during installation

### Question 1? [y/n]

xxxxxx

### Question 2

yyyyyy



## Need to work up ...

## More advanced topics

### gggggg

To add new clients later, run the command that you copied at the end of installation, incrementing the last number (`7`, in this case) by one each time you run it:

    ggg
    
You'll find the new client conf file created in the `clients` directory. You can either send the file, or use `cat` to display its contents and copy that. e.g.

```bash
$ cat clients/7.conf

[Interface]
PrivateKey = +NrpspR++zR509u71WEPKpqoOw5+1p5z8HpS4Vyrw2k=
Address = 10.42.42.7/24
[Peer]
PublicKey = VwSJ06TopxpF2Dvlj4ZUDUqwVeHuwZpLDQSvvJtCo3s=
Endpoint = 54.213.232.25:51820
AllowedIPs = 10.42.42.0/24
PersistentKeepalive = 15
```
