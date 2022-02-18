# proxmox-setup
proxmox-setup

> Simplified installation of a [proxmox](https://www.wireguard.com/) hypervisor (tested on T460s+16GB+512SSD)

*NB: Below are the setup document for setting up proxmox hypervisor

Usefull commadss:

    ssh ubuntu@1.2.3.4

Remove LVM disk , run:

To remove LVM Volume:

    lvremove /dev/pve/data 

    Type y for yes

To use remainign full disk ( 100% disk space )
    
    lvresize -l +100%FREE /dev/pve/root

To make it permentant:

    resize2fs /dev/mapper/pve-root



## Questions during installation

### Wher to see the upload iso ? [y/n]

    /var/lib/vz/template/iso

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

 
 
##Delete default user
deluser --removehome testuser

##Create swap file
dd if=/dev/zero of=/swapfile bs=1024 count=1536000
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
echo "/swapfile       swap    swap    defaults        0 0" >> /etc/fstab

##Install pakages
#Mandatory
apt install -y cloud-init cloud-initramfs-growroot qemu-guest-agent sudo git curl
#Optional
apt install -y fish figlet tmux mlocate fonts-powerline resolvconf htop iftop bmon net-tools dnsutils gnupg2 ntpdate


## Qemu Guest 
https://pve.proxmox.com/wiki/Qemu-guest-agent


()
Establishing API connection with host '192.168.0.200'
Login succeeded.
check cluster join API version
No cluster network links passed explicitly, fallback to local node IP '192.168.0.137'
Request addition of this node
Join request OK, finishing setup locally
stopping pve-cluster service

# Nexus
https://securitywing.com/setup-a-nexus3-repository-using-docker-on-virtual-box/

## proxmox CPU plugin to check temperature
apt install xsensors
sensors

https://www.programmerall.com/article/5981210525/

https://forum.proxmox.com/threads/temperature.67755/

Bash:
#! /bin/bash

# ©locknessKo 2022

# Slack incoming webhook URL
slack_url=https://hooks.slack.com/services/xxx/xxx/xxx

# Threshold for when to send alert
threshold=80

sensors | grep -e "temp1" | while read line; do
        temp=$(echo $line | awk -F "+" '{ print $2 }' | awk -F "." '{ print $1 }');
        if (( temp > $threshold )); then
                curl -X POST -H 'Content-type: application/json' --data "{'text':'ALERT for $(hostname). Temperature is $temp degrees'}" $slack_url;
        fi;
        done
 
 A guide on how to setup slack incoming webhook: https://api.slack.com/messaging/webhooks

How to use cronjobs: https://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/

Hope this helps!
-----------------
 
## Relevant Articles: 
- [Proxmox](https://proxmox.com/en/)
- [Before I do anything on Proxmox, I do this first.](https://www.youtube.com/watch?v=GoZaMgEgrHw)
- [Docker, Rancher, Kubernetes..? (Rancher Setup and Install Tutorial)](https://www.youtube.com/watch?v=oILc0ywDVTk)


