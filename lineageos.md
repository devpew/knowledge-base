## DOWNLOAD

Первое что нужно сделать это скачать последнюю версию lineageos

https://download.lineageos.org/dumpling

Потом качаем последнюю версию twrp

https://eu.dl.twrp.me/dumpling/

Потом качаем последнюю версию Firmware для моего телефона

https://downloads.oneplus.com/devices/oneplus-5t/

Закачиваем все три файла, которые мы скачали в телефон с помощью android-file-transfer

## BACKUP

Теперь нужно сделать полный бекап телефона на ноутбук

для начала включаем adb server

~~~~
adb start-server
~~~~

После этой команды телефон спросит доверять ли этому компьютеру.

Далее вводим

~~~~
adb backup -apk -shared -all -f backup-file.adb
~~~~

Теперь на телефоне появится окошко, которое попросит пароль. Вводим пароль и начнется бекап.

Потребуется минут 10 на создание бекапа. Полный бекап будет находится в домашней папке с именем backup-file.adb

## RESTORE

Если вдруг понадобится восстановиться то это делается довольно просто

Включаем ADB сервер

~~~~
adb start-server
~~~~

и вводим команду для восстановления

~~~~
adb restore backup-file.adb
~~~~

## INSTALL

Перегружаемся в recovery

Из TWRP устанавливаем Firmware https://dl.twrp.me/dumpling/

Далее загружаем телефон и выбираем ADVANCED

reboot to fastboot

вбиваем команду

~~~~
sudo fastboot flash recovery /home/dm/Downloads/twrp-3.2.3-1-dumpling.img
~~~~

выбираем Recovery mode

Далее устанавливаем через TWRP последнюю версию lineageos которую мы скачали

Перезагружаемся и все готово
