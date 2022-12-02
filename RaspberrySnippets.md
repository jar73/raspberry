# Enable auto updates
    sudo apt-get install unattended-upgrades
    sudo dpkg-reconfigure -plow unattended-upgrades
    
# Static IP
Edit cmd
    ip=<Raspi-IP>:<Netboot-Server>:<Gateway-IP>:<Subnetzmaske>:<Hostname>:<Netzwerkkarte>:<Autoconf>

Sample
    ip=192.168.0.x::192.168.0.1:255.255.255.0:raspy:eth0:off
    
    
# GPIO install    
sudo apt update    
sudo apt install gpiod
    
usage: https://www.ics.com/blog/gpio-programming-exploring-libgpiod-library    
    
    
# Squeezelitze
    sudo apt-get update
    sudo apt-get upgrade
    
    Audio-Codecs installieren
    sudo apt-get install libflac-dev libfaad2 libmad0 libmpg123-0
    
    
 //  sudo apt install squeezelite
    wget https://sourceforge.net/projects/lmsclients/files/squeezelite/linux/squeezelite-1.9.9.1411-armhf.tar.gz/download
    tar -C /usr/bin -zxvf squeezelite-1.9.9.1411-armhf.tar.gz
    
    Media Server
    wget https://downloads.slimdevices.com/LogitechMediaServer_v8.2.0/logitechmediaserver_8.2.0_arm.deb
    
    
    
    sudo apt-get --fix-broken install libio-socket-ssl-perl
sudo dpkg -i logitechmediaserver_8.2.0_arm.deb
sudo apt-get install -y libsox-fmt-all libflac-dev libfaad2
    
    
 NFS mount to NAS   
    Configure directory permission in Settings NFS for IP
    
    On client
    sudo apt-get install nfs-common
    sudo apt-get install autofs
    
    
    
    
