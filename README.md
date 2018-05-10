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
| ---------- | ------ |
| fdisk -l   | Lists drives  |
| dd if=<path to iso> of=</dev/drive> (bs=512k)          | write input file to output file (drive)   |
