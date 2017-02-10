# JOSM Live
Live USB with JOSM preinstalled.

# Purpose
We had some problems with installing JOSM on users laptops during Mapathons. So
idea of live USB with JOSM preinstalled had born.

# Making live USB
* Install needed packages by `apt-get install live-build git` (commands fits for
  Debian-like systems, root needed).
* Clone this repository `git clone https://github.com/qeef/josm-live.git`.
* Change into directory `cd josm-live`.
* Build live image `lb build` (root needed).
* Copy to USB flash drive `dd if=live-image-i386.hybrid.iso of=/dev/sdb bs=4M;
  sync` (root needed). !! Change `/dev/sdb` to your USB flash drive !!
* Boot with your new live USB.

# Making persistent volume
* Start fdisk by `fdisk /dev/sdb` (root needed).
* Create new partition by `n`.
* Primary partition default by pressing [enter] key.
* Partition number default by pressing [enter] key.
* First sector default by pressing [enter] key.
* Last sector default by pressing [enter] key.
* Save and exit fdisk by `w`.
* Make filesystem on new partition by `mkfs.ext4 -L persistence /dev/sdb2`.
* Mount new partition by `mount /dev/sdb2 /mnt`.
* Create *persistence.conf* file by `touch /mnt/persistence.conf`.
* Let */home* folder be persistent by `echo "/home" >> /mnt/persistence.conf`.
* Unmount new partition by `umount /mnt`.
* Boot with your new live persistent USB.

# Contributing
This project is built on [Debian Live](https://wiki.debian.org/DebianLive/). For contributing, starting point is [Live Systems Manual](https://debian-live.alioth.debian.org/live-manual/stable/manual/html/live-manual.en.html).
