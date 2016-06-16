#xenserver-automater

Based on [jonathanhoskin/xenserver-automater](https://github.com/jonathanhoskin/xenserver-automater), these scripts will be used to setup Xenserver guests created with [puppet-xenserver](https://github.com/tiengo/puppet-xenserver) module.

If you want to test it without Puppet module, just follow the steps below:

## Create and start a new VM with custom xenstore data:
  UUID=`xe vm-install template=mytemplate new-name-label=newvm`  
  xe vm-param-set uuid=$UUID xenstore-data:vm-data/ipaddress=192.168.0.2  
  xe vm-param-set uuid=$UUID xenstore-data:vm-data/gateway=192.168.0.1  
  xe vm-param-set uuid=$UUID xenstore-data:vm-data/netmask=255.255.255.0  
  xe vm-param-set uuid=$UUID xenstore-data:vm-data/nameserver=8.8.8.8  
  xe vm-param-set uuid=$UUID xenstore-data:vm-data/hostname=xe-automate.andretiengo.me  
  xe vm-param-set uuid=$UUID xenstore-data:vm-data/key_pairs='ssh-rsa abc user@key.com'  
  xe vm-param-set uuid=$UUID xenstore-data:vm-data/rootpw=s3cr3t  

  xe vm-start uuid=$UUID  

## Install scripts on guest VM:

git clone https://github.com/tiengo/xenserver-automater  
cd xenserver-automater  
./post-install.sh  

## Reboot
