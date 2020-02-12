# Debian usb system plików tylko do odczytu
Jak naprawić USB system plików tylko do odczytu.

## Disks
```bash
sudo -i
sudo fdisk -l
```

## /etc/fstab
```bash
sudo nano /etc/fstab

# Add line
/dev/sdb1   /media/usb     vfat defaults,rw,auto,users,uid=1000,gid=100,fmask=0111,dmask=000,fmask=137,utf8,errors=continue   0   0
```

## Mount usb
```bash
# odmontuj wszystko
sudo umount -a

# utwórz dir
sudo mkdir /media/usb

# zamontuj usb
sudo mount -rw /dev/sdb1 /media/usb

# update
mount -o remount, rw /
```

## Napraw usb
```bash
# tak
fsck /dev/md3
fsck -p /dev/md3

# lub
tune2fs -e continue /dev/sda1
```
