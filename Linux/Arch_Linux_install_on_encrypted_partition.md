# Arch Linux install on encrypted partition

First of all, recommend to plug Ethernet cable, it will be much easier to install arch.

So, plug your flash drive and turn on your PC.

If everything is fine and you successfully boot from flash first of all check your internet

```
ping 8.8.8.8
```

Next, if you want bigger font, you can install terminus font

```
pacman -S terminus-font
```

All the fonts for console will be there:

```
cd /usr/share/kbd/consolefonts
```

Now you can set bigger font:

```
setfont ter-v32b
```

Next, you could check what drives your system sees. Usually it sd* or nvme*

```
lsblk
```

Ok, next step is to create two partitions. For / and for /boot

```
gdisk /dev/nvme0n1
```

There we can type

```
o
```

To create new GPT

And after that type

```
n
```

To create new partition for /boot

We should create this partition with

```
+512MB
```

And when it asks type of partition we should type

```
EF00
```

And we should create second partition for our system.

Next step is to encrypt partition that we created:

```
cryptsetup -y -v luksFormat /dev/nvme0n1p2
```

And we can open it with command:

```
cryptsetup open /dev/nvme0n2 cryptroot
```

We should format our partition:

```
mkfs.ext4 /dev/mapper/cryptroot
```

And mount it:

```
mount /dev/mapper/cryptroot /mnt
cd /mnt
```

Make boot dir

```
mkdir /boot
```

And format it

```
mkfs.vfat /dev/nvme0n1
```

Mount it

```
mount /dev/nvme0n1 /mnt/boot
```

And we’re ready to install Arch

```
pacstrap /mnt
```

After install we could go to our arch with command:

```
arch-chroot /mnt
cd
```

Next, we will install boot

```
bootctl install
```

Install VIM

```
pacman -S vim
```

We need to edit our core, to add encrypt compability

```
vim /etc/mkinitcpio.conf
```

We need to find HOOKS string and add

```
encrypt
```

After that

```
cd /boot/loader
vim loader.conf
```

with content

```
default arch
cd entries
touch myarch.conf
vim myarch.conf
title archlinux /vmlinuz-linuxinitrd /initramfs-linux.imgoptions rw cryptdevice=UUID=1111827398172983:cryptroot root=/dev/mapper/cryptroot
:r !blkid
```

After that we should rebuild our core

```
mkinitcpio -p linux
exit
reboot
```

Done!

After Install we might have a problem with internet if our wifi has DHCP enabled.

We could type this command to fix it.