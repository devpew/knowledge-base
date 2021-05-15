Чтобы создать зашифроваанный swap раздел для начала надо сделать этот раздел из gpardet

размер swap должен быть равен или больше оперативной памяти

Для начала нужно создать раздел LUKS на том разделе, который мы создали для свапа

~~~~
sudo cryptsetup luksFormat --cipher twofish-xts-plain64 --key-size 512 --hash sha512 --iter-time 2000 /dev/nvme0n1p8
~~~~

После чего этот раздел нужно "открыть"

~~~~
sudo cryptsetup luksOpen /dev/nvme0n1p8 swap
~~~~

После этой команды у нас в /dev/mapper должен появиться "swap"

Проверим это командой

~~~~
ls /dev/mapper
~~~~

Если появился, то идем дальше

И делаем swap в этом файле

~~~~
sudo mkswap /dev/mapper/swap
~~~~

### ЗАМЕНЯЕМ ПАРОЛЬ ФАЙЛОМ КЛЮЧА

Для чтого чтобы заменить ввод пароля на вход по ключу для начала отключим свап командой

~~~~
sudo cryptsetup luksDump /dev/nvme0n1p8
~~~~

Теперь создадим ключ командой

~~~~
sudo dd if=/dev/random of=/root/z bs=1 count=512
~~~~

И добавим возможность входить с этим ключом в наш свап

~~~~
sudo cryptsetup luksAddKey /dev/nvme0n1p8 /root/z
~~~~

После чего в файл sudo gedit /etc/crypttab добавить возможность заходить в систему используя ключ просто вставив путь к нему в третье значение.

Если захочешь исползовать вход без ключа, но с паролем, то третье значение можно поставить как none

Вот Как выглядит рабочий файл crypttab

~~~~
sudo gedit /etc/crypttab
~~~~

~~~~
swap   /dev/nvme0n1p8   /root/z   luks
~~~~





А вот так выглядит рабочий fstab

~~~~
sudo gedit /etc/fstab
~~~~

~~~~
/dev/mapper/swap none swap sw 0 0
~~~~








### Полезные информативные команды команды

~~~~
swapon -s
~~~~

Должно выдать что-то типа такого:

~~~~
$swapon -s

Filename				Type		Size	Used	Priority
/dev/nvme0n1p8                         	partition	19763196	0	-1
~~~~

~~~~
$sudoswapon --show

[sudo] password for dm:
NAME           TYPE       SIZE USED PRIO
/dev/nvme0n1p8 partition 18,9G   0B   -1
~~~~

~~~~
free -h                     
              total        used        free      shared  buff/cache   available
Mem:            15G        7,7G        2,6G        1,4G        5,1G        7,5G
Swap:           18G          0B         18G
~~~~







~~~~
/etc/crypttab
~~~~




~~~~
 /etc/fstab
~~~~

~~~~
/dev/mapper/cryptswap1 none swap sw 0 0
~~~~


Узнать статус вашего свапа

~~~~
sudo cryptsetup status cryptswap1
~~~~
