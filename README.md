# MediaServer
Contains software for my jellyfin media server 

## Setup

### Raspberry Pi 
Flash a 16GB SD card with the latest version of [Raspberry Pi OS Lite](https://www.raspberrypi.org/software/operating-systems/).
For raspberry pi 3b and 3b+:
```32 bit OS (Raspberry Pi OS Lite)``` is better as it consumes less RAM.
For raspberry pi 4:
```64 bit OS (Raspberry Pi OS Lite (64 bit))``` is better as it has more RAM and can take advantage of the architecture.

On ubuntu it is preferrable to flash the SD card with [Raspberry Pi Imager](https://www.raspberrypi.org/software/) or [balenaEtcher](https://www.balena.io/etcher/).

### Headless setup
for a true headless setup use hidden options of [Raspberry Pi Imager](https://www.raspberrypi.org/software/) using the guide at https://raspberrypi-guide.github.io/getting-started/raspberry-pi-headless-setup.html

### SSH
To enable SSH via the terminal, open a terminal window and enter sudo raspi-config. Now with the arrows select Interfacing Options, navigate to and select SSH, choose Yes, and select Ok.

### Static IP
follow the guide at https://pimylifeup.com/raspberry-pi-static-ip-address/ 

nano can be replaced by any terminal text editor of choice, I personally prefer vim/nvim.

ip r | grep default\
sudo nano /etc/resolv.conf
sudo nano /etc/dhcpcd.conf

Static IP can also be set via the router, I do not prefer this as it is not portable.

It is also preferred to have the raspi on a wired connection for better performance.

### Update and Upgrade

After installing each new package it is preferrable to update and upgrade the system using the following commands:\
```sudo apt update```\
```sudo apt upgrade```

### Tailscale

Follow the guide at https://tailscale.com/kb/1017/install-rpi/

Use the web UI to add the device to the network.

### JellyFin
Follow the guide at https://pimylifeup.com/raspberry-pi-jellyfin/

### PiHole
If there is spare processing power, explore using it for PiHole.

### Automount drive(s)
To setup the external drive to automount to a fixed mount point, add a new /etc/fstab entry for the external drive using its UUID or PartUUID.\

use the guide at https://confluence.jaytaala.com/display/TKB/Mount+drive+in+linux+and+set+auto-mount+at+boot 

### File Transfer protocol (FTP or SFTP)
Set up FTP using ```sudo apt install vsftpd``` and configure it using ```sudo nvim /etc/vsftpd.conf``` then restart using ```sudo service vsftpd restart```. follow the guide at https://phoenixnap.com/kb/raspberry-pi-ftp-server or https://pimylifeup.com/raspberry-pi-ftp/.

Make sure to set the folder permissions correctly based on what you want the user to have access to through FTP.

After setting up FTP on the raspi, we can use FileZilla to transfer files to and from the raspi using its IP address and the username and password of the user on the raspi.