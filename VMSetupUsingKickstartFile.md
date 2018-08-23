# Virtual Machines/ Automated Installations with Kickstart

1. Install Virt Host/Client packages
  * \# yum group install "Virtualization Host" "Virtualization Client"

2. Load appropriate kernel modules (should be done automatically from step 1)
  * \# lsmod | grep kvm    #intel or amd?
  * \# modprobe kvm_intel  

3. Kickstart File Steps
  * Copy _/root/anaconda-ks.cfg_ file to ks.cfg and do the following:
    * Remove __cdrom__ directive and add __url --url ftp://192.168.122.1/pub/inst__  #insert appropriate IP addr
    * Change __firstboot --enable__ to __firstboot --disabled__  #KS cannot  answer Firstboot prompts => disabled helps automate process
    * __ignoredisk --only-use=vda__
    * _For DHCP server:_ 
       *__network --device etho- --bootproto dhcp__
    * _For static IP addr:_
       *__network --bootproto static --device=eth0 --gateway=192.168.122.1 \
          --ip=192.168.122.150 --netmask=255.255.255.0 --noipv6 \
          --nameserver==192.168.122.1 --activate__
       *__network --hostname tester1.example.com__
    * Add users:
       * user --groups=wheel name=mike --password=<copy from shadow file> --iscrypted --gecos='Real Name Info'
    * Add services through firewall
       * firewall --service=ssh
    * Ensure SELinux in __enforcing__ mode
       * selinux --enforcing
    * clearpart --all --initlabel --drives=vda
    * Before __%packages__ add shutdown
