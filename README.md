# chuwihi10prolinux
Attempt at Linux on the Chuwi Hi10 Pro

After deciding to remove the preinstalled Windows and Android OS that came with the system and install Linux as a replacment, this is my notes/walkthrough on installing Linux on the Chuwi Hi10 Pro. Mainly in case i do something to brick the system and have to start over, but hopefully will be of some use to others.

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

Sound -

https://github.com/plbossart/UCM/tree/master/bytcr-rt5651

Touchscreen -

https://github.com/onitake/gslx680-acpi
https://github.com/onitake/gsl-firmware

Clone both of these repos and run make in the acpi repo (remember to install build-essentials before make)

........

