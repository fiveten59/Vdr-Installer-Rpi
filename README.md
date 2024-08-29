# Simple script for installing Vdr on Raspberry Pi4

Os: 
Bookworm Lite or Desktop 64 bit for Rpi4 

At first install Raspberry Pi OS  (script tested with Debian Bookworm)

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

or copy/paste in this folder the script vdr_installer_2.6.X_rpi4 via Usb or SSH (ifconfig gives your IP address) or via Lan using Filezilla

chmod 755 vdr_installer_2.6.X_rpi4

now we open the file
sudo su
./vdr_installer_2.6.X_rpi4 

And follow the script  ...
Trick: at point 1 type 'First install libraries' just only now

 1 creates a new folder downloading progs & libraries needed by Vdr 
 2 install some DVB firmware FFMPEG e Eventlircd
 3 install Vdr
 4 install Vdr  Basic plugins Softhddevice-drm-gles - Skinflatplus - Iptv - Radio - Dvbapi - Vnsiserver)

 5 configure all the Vdr system (remember when requested type b) Console)
Select a) installing shared parts 

 6 Final install
Select a) installing Vdr on consolle
Select b) installing Vdr on Desktop

Reboot

Tips & Tricks

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

- Libraries are in /lib/vdr folder
- You can put your channells as usual in /etc/vdr
