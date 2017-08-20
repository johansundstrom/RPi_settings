### RPi_settings
## Setup File Share och VNCServer
```bash
sudo apt update && sudo apt full-upgrade
```
```bash
sudo apt install -y tightvncserver
```
```bash
sudo apt install -y xrdp
```
```bash
sudo apt install -y samba
```
Starta Microsoft Remote Desktop
```bash
sudo leafpad /etc/samba/smb.conf &
```
Lägg till följande i slutet på filen smb.conf...
```
[PiShare]
 comment=Raspi Share
 path=/home/pi
 browseable=Yes
 writeable=Yes
 only guest=No
 create mask=0740
 directory mask=0750
 public=no
 ```
```bash
sudo smbpasswd -a pi
```
## Fixed IP
```
sudo nano /etc/dhcpcd.conf
```
```
interface eth0

static ip_address=192.168.0.10/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1

interface wlan0

static ip_address=192.168.0.200/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1
```
