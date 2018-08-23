#Configure Repo Server (HTTP/FTP)
## Permanently Activate IP Forwarding (KVM hyperviser has IP forwarding disabled by default)

  1. Add the following line to '/etc/sysctl.conf'
    + net.ipv4.ip_forward=1
  
  2. Implement Changes immediately on local system
    + # sysctl -p


## Create HTTP/FTP server of RH7 iso
  
  1. Install and start server client (HTTP or FTP)
    + # yum -y install httpd (vsftpd)
    + # systemctl start httpd

  2. Mount iso to drive and copy files to server location
    + # mount -o loop <path-to-iso> /media        #mount iso to directory (use # mount /dev/cdrom /media for CD mounting)
    + # mkdir /var/www/html/inst (/var/ftp/pub/inst)
    + # cp -a /media/. /path/to/dir (/var/www/html/inst or /var/ftp/pub/inst)         # -a copies all files in archive recursively 

  3. Ensure correct SELinux context
    + #chcon -R --reference=/var/www/html /var/www/html/inst

  4. Configure Firewall
    + # firewall-cmd --permanent --add-service=http (--add-service=ftp)
    + # firewall-cmd --reload

  5. Start/enable server to start at boot
    + # systemctl restart httpd
    + # systemctl enable httpd
