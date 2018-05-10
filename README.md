# rhcsa
Red Hat Certified System Administrator Commands

## File System Mount Points

|  Location  |  Size  |
| ---------- | ------ |
| /boot      | 500MB  |
| /          | 10GB   |
| /home      | 1024MB |
| /swap      | 1024MB |

The above table is similar to what the exam will offer.

## Creating Bootable USB/CD/DVD

Using the dd command will be the easiest way to mount an iso image.


|  Command   |  Result  |
| ---------- | ------                                  |
| fdisk -l   | Lists drives                            |
| dd if=path-to-iso of=</dev/drive> (bs=512k)          | write input file to output file (drive)                     |

## Default Security Settings

|  Command   |  Result  |
| ---------- | ------                                  |
| sestatus   | check SELinux settings and ensure enforcing mode is enabled                            |
| firewall-cmd --list-all   | check detailed information about the current firewall configuration |
| iptables -L   | additional firewall rules |
|  sysctl -p   | implement changes immediatel on this system |

Add 'net.ipv4.ip_forward=1' to /etc/sysctl.conf file to permanently activate IP forwarding (will survive reboot).


