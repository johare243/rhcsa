1) Install vsftpd (very secure ftp daemon)
  # yum -y install vsftpd

2) Start ftpd
  #systemctl start vsftpd

3) Enable (for reboot)
  #systemctl enable vsftpd


Configure for installation files on ftp server
  (-p makes parent directories if they don't exist)

  # mkdir -p /var/ftp/pub/inst
  # cp -a <path-to-iso> /var/ftp/pub/inst
  # chcon -R --reference=/var/ftp/pub /var/ftp/pub/inst

  ^This 'chcon' command applied the default SELinux context from /var/ftp/pub to /var/ftp/pub/inst (-R = recursively)


Configure firewall 

  # firewall-cmd --permanent --add-service=ftp
  # firewall-cmd --reload


Ensure  is running and Enabled

  # systemctl restart vsftpd
  # systemctl enable vsftpd


Mounting DVD/ISO

  # mount /dev/cdrom /media
  # mount -ro loo <path-to-iso> /media
