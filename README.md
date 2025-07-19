# Install-xfce-on-WSL-Ubuntu

**Download update and upgrade systems
sudo apt update && sudo apt -y upgrade

# install xfce 

sudo apt-get install -y xfce4 xfce4-goodies

sudo cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak
sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini
sudo sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g' /etc/xrdp/xrdp.ini
sudo sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini

**Call Sessions
echo xfce4-session > ~/.xsession

**For configurations
sudo nano /etc/xrdp/startwm.sh 

1 step add: "startxfce4"
And save

#enable dbus
sudo systemctl enable dbus
sudo /etc/init.d/dbus start
sudo /etc/init.d/xrdp start

# check xrdp status and start it
sudo /etc/init.d/xrdp status
