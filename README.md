
Simple script for installing Vdr on Raspberry Pi4 

a) Raspberry Pi OS Lite

At first install Raspberry Pi OS Lite (script tested with Debian Bullseye)
https://www.raspberrypi.com/software/operating-systems/

After installation update the system (sudo apt update && sudo apt full-upgrade)
and configure through Raspi-config (sudo raspi-config)
1 - System Options - Set Wireless LAN (optional) - Set Boot on Console autologin)
3 - Interface Options (optional but I suggest enable SSH for check and work from remote)
4 - 
5 - Localisation Options (Set 1,2 & 4  item - for the language L1 use yourlanguage-UTF8)
At the end reboot the system

Now we install the script
# sudo apt install tar git wget
Create a new folder in your Home (mkdir -p 'a name of your choice')
cd new folder
download the file "https://www.dropbox.com/s/4ls1exbn24bs88f/vdr_installer_2.6.4_rpi"
or copy/paste in this folder the script vdr_installer_2.6.4_rpi via Usb or SSH (ifconfig gives your IP address) or via Lan using Filezilla

chmod u+rwx vdr_installer_2.6.4_rpi

now we open the file

sudo ./vdr_installer_2.6.4_rpi
Follow the script  ...
Trick: at point 1 type 'First install libraries' just only now
Follow the script  ...
Point 1 creates a new folder downloading progs & libraries needed by Vdr 
Point 2 install some DVB firmware FFMPEG e Eventlircd
Point 3 install Vdr
Point 4 install Vdr  Basic plugins (Softhddevice-drm - Skinflatplus - Iptv - Radio - Dvbapi)
Point 5 configure all the Vdr system (remember when requested type b) Console)


Tips & Tricks

- Using a simple USB Audio Device [f.e. USB PnP Sound Device] from a remote terminal check

aplay -l

and control where is your Usb - In my case I have
"card 1: Device [USB PnP Sound Device], device 0: USB Audio [USB Audio]"
so we have to change alsa.conf with

sudo nano /usr/share/alsa/alsa.conf

and change the two follwing lines
defaults.ctl.card 0
defaults.pcm.card 0
with
defaults.ctl.card 1
defaults.pcm.card 1

- Using a solid sound device like hifiberry or similar add to 
sudo nano /boot/config.txt
dtoverlay=hifiberry-dac 


- The "dark" is in /usr/local/etc

- You can put your channells as usual in /etc/vdr

b) Raspberry Pi OS Desktop

At first install Raspberry Pi Desktop version (& update it) remembrer apt updare & apy full-upgrade

Same as above up to point five of the script

Point 5 - configure all the Vdr system (remember when requested type a) Desktop )
that's all

IMPORTANT !!!
Remember that Softhddevice-drm NEEDS no running X
so change in console Ctrl + Alt + F1
and type sudo ./vdrrun
