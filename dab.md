## welle.io command line interface only on raspberry (2) 
 Linux version 5.10.63-v7+ (dom@buildbot) (arm-linux-gnueabihf-gcc-8 (Ubuntu/Linaro 8.4.0-3ubuntu1) 8.4.0, GNU ld (GNU Binutils for Ubuntu) 2.34) #1488 SMP Thu Nov 18 16:14:44 GMT 2021

sudo apt-get update
sudo apt-get upgrade

sudo reboot -n

sudo apt install libtool libusb-1.0-0-dev librtlsdr-dev rtl-sdr build-essential autoconf cmake pkg-config 
sudo apt install libfftw3-dev libmpg123-dev libfaad-dev libsoapysdr-dev alsa-utils libmp3lame-dev

git clone https://github.com/AlbrechtL/welle.io
mkdir welle.io/build
cd welle.io/build/
cmake .. -DRTLSDR=1 -DSOAPYSDR=1 -DBUILD_WELLE_IO=OFF -DBUILD_WELLE_CLI=ON
make
sudo make install

cd /usr/local/share/welle-io/html
welle-cli -s "driver=sdrplay,soapy=0,rfnotch_ctrl=true,dabnotch_ctrl=true" -w 8008 -c 12B
