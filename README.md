# Simple script for installing Vdr on Raspberry Pi4 & Pi3

Os: 
Bullseye Lite 32 bit for Rpi3
Bullseye Lite or Desktop 32/64 bit for Rpi4 

a) Raspberry Pi3 OS Lite (only 32bit)

At first install Raspberry Pi OS Lite (script tested with Debian Bullseye)
https://downloads.raspberrypi.org/raspios_lite_armhf/images/raspios_lite_armhf-2023-02-22/2023-02-21-raspios-bullseye-armhf-lite.img.xz

After installation update the system (sudo apt update && sudo apt full-upgrade)
and configure through Raspi-config (sudo raspi-config)
- System Options - Set Wireless LAN (optional) - Set Boot on Console autologin)
- Interface Options (optional but I suggest enable SSH for check and work from remote)
- 
- Localisation Options (Set 1,2 & 4  item - for the language L1 use yourlanguage-UTF8)
At the end reboot the system

Create a new folder in your Home (mkdir -p 'a name of your choice' f.e "myvdr")

Now we install the script

cd new folder
download the file
wget https://www.dropbox.com/s/ukepxg7o75w1g39/vdr_installer_2.6.4_rpi
or copy/paste in this folder the script vdr_installer_2.6.4_rpi via Usb or SSH (ifconfig gives your IP address) or via Lan using Filezilla

chmod 755 vdr_installer_2.6.4_rpi

now we open the file
sudo su
./vdr_installer_2.6.4_rpi 

And follow the script  ...
Trick: at point 1 type 'First install libraries' just only now

 1 creates a new folder downloading progs & libraries needed by Vdr 
 2 install some DVB firmware FFMPEG e Eventlircd
 3 install Vdr
 4 install Vdr  Basic plugins (Rpihddevice(for rpi3)/Softhddevice-drm(for Rpi4) - Text2Skin-NarrowHd - Iptv - Radio - Dvbapi)
On Raspberry Pi3 choice Rpihddevice!!!!
 5 configure all the Vdr system (remember when requested type b) Console)
Select a) installing shared parts 
Select c) installing Vdr on console On Raspberry Pi3

Reboot

b) Raspberry Pi4 OS Lite (32 or 64 bit)

Same as above for the first part
At point 5 of the script
Select a) Install shared parts
Select b) Configure Raspberry Pi 4 (Bullseye Desktop & Lite 32/64 bit Bullseye )
then b) Rpi4 Console (Bullseye Lite version 32/64 bit)

c) Raspberry Pi4 OS Desktop (32 or 64 bit)

Same as above for the first part
At point 5 of the script
Select a) Install shared parts
Select b) Configure Raspberry Pi 4 (Bullseye Desktop & Lite 32/64 bit Bullseye )
then a) Rpi4 Desktop (Bullseye Desktop version 32/64 bit)

Vdr automatically starts on all the three version after booting 
and (console version) shutdown after poweroff of your remote
while on desktop version shut Vdr e display the usual Bullseye screen  

# Tips & Tricks

Using a simple USB Audio Device [f.e. USB PnP Sound Device] from a remote terminal check
aplay -l and control where is your Usb - In my case I have
"card 1: Device [USB PnP Sound Device], device 0: USB Audio [USB Audio]"
so we have to change alsa.conf with
sudo nano /usr/share/alsa/alsa.conf
and change the two follwing lines
defaults.ctl.card 0
defaults.pcm.card 0
with
defaults.ctl.card 1
defaults.pcm.card 1

Using a solid sound device like hifiberry or similar add to 
sudo nano /boot/config.txt
dtoverlay=hifiberry-dac 

- The "dark" is in /usr/local/etc
- You can put your channells as usual in /etc/vdr
