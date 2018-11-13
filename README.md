# chuwihi10prolinux
Attempt at Linux on the Chuwi Hi10 Pro

After deciding to remove the preinstalled Windows and Android OS that came with the system and install Linux as a replacement, these are my notes/walkthrough on installing Linux on the Chuwi Hi10 Pro. Mainly in case i do something to brick the system and have to start over, but hopefully will be of some use to others.

Whats Working:

Sound
Bluetooth
Touchscreen
Wifi
Internal MMC storage
Graphics
Micro USB
USB C 
Battery
Brightness Control
Buttons (Power, Volume)


Not Working:

Cameras (Front, Rear)
SD Card


Current Distro = Ubuntu 18.04 LTS (Using Linuxinuim isorespin.sh http://linuxiumcomau.blogspot.com/) - Kernel 4.19.1-041901-generic using Ukuu


Graphics -

Screen rotated 90 degrees so once logged in use display properties to rotate screen

Sound -

https://github.com/plbossart/UCM/tree/master/bytcr-rt5651

Touchscreen -

https://github.com/onitake/gslx680-acpi
https://github.com/onitake/gsl-firmware

Clone both of these repos and run make in the acpi repo (remember to install build-essentials before make)

Wifi

Should work out of the box with the linuxium isorespin.sh or the newest kernel with the RTL8723BS drivers - If using an older kernel try https://github.com/hadess/rtl8723bs (make && sudo make install) 

Firmware should be rtl8723bs_nic.bin
Module should be r8723bs

Bluetooth

Tricky... After trying a number of routes and using a USB BT adapter for a while i decided to have another go:
install rtl8723bs_4.12.0_amd64.deb from linuxium - http://linuxiumcomau.blogspot.com/2017/06/rtl8723bs-wifi-and-bt-firmware-package.html (This installs both the drivers and a service which runs a hciattach modified by lwfinger on boot - make sure rtl8723bsbt.service is set up and running -- sudo systemctl start rtl8723bsbt.service)

Depending on system/kernel bluetooth should work on reboot - if not (like mine) clone and make https://github.com/lwfinger/rtl8723bs_bt - firmware files should be in /lib/firmware/rtl_bt

a look at dmesg (dmesg | egrep -i '8723') shows that the kernel finds hci0 but is trying to load the non existant rtl8723bs_fw.bin as firmware instead of rtlbt_fw in /lib/firmware/rtl_bt

Solution is to copy/rename rtlbt_fw to rtl8723bs_fw.bin and rtlbt_config to rtl8723bs_config-0BDA8723.bin	(may also need to copy/rename rtlbt_config to rtl8723bs_config.bin though on my tablet it wanted -0BDA8723 added)

Quick reboot and bluetooth should be available.





........

