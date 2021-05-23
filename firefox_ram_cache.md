# FIREFOX CACHE RAM

Я храню кэш файрфокса в RAM

Для этого я использую программу, которая называется PSD которую я скачал из yay

~~~~
yay -S profile-sync-daemon
~~~~

Эту штуку включать надо как сервис

~~~~
systemctl --user start psd
systemctl --user status psd
~~~~

Проверить, работает ли она сейчас можно командой

~~~~
psd p
~~~~
