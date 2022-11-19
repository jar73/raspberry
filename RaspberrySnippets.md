# Enable auto updates
    sudo apt-get install unattended-upgrades
    sudo dpkg-reconfigure -plow unattended-upgrades
    
# Static IP
ip=<Raspi-IP>:<Netboot-Server>:<Gateway-IP>:<Subnetzmaske>:<Hostname>:<Netzwerkkarte>:<Autoconf>

Sample
ip=192.168.0.x::192.168.0.1:255.255.255.0:raspy:eth0:off
    
    
    
