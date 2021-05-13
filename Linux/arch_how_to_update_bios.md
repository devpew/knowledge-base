~~~~
sudo pacman -S fwupd
~~~~

Install fwupd using this command

~~~~
# fwupdmgr get-devices
~~~~

This will display all devices detected by fwupd.

~~~~
# fwupdmgr refresh
~~~~

This will download the latest metadata from LVFS.

~~~~
# fwupdmgr get-updates
~~~~

If updates are available for any devices on the system, they'll be displayed.

~~~~
# fwupdmgr update
~~~~

This will download and apply all updates for your system.

    Updates that can be applied live will be done immediately.
    Updates that run at bootup will be staged for the next reboot.
