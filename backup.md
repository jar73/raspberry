## Installing backup job on raspberry to backup nightly to NAS

```
sudo apt-get update
sudo apt-get upgrade
sudo apt install nfs-common

sudo mkdir -m 777 /mnt/backup
sudo mount 192.168.XX.XX:/volume1/Backup/rasp1 /mnt/backup
sudo vi /etc/fstab
+ 192.168.XX.XX:/volume1/Backup/rasp1 /mnt/backup nfs rsize=8192,wsize=8192,timeo=14,intr,noauto,rw,users,x-systemd.automount 0

sudo vi /mnt/backup/system_backup.sh

#!/bin/bash
#
# Automate Raspberry Pi Backups
#

# Declare vars and set standard values
backup_path=/mnt/backup
retention_days=7

# Check that we are root!
if [[ ! $(whoami) =~ "root" ]]; then
echo ""
echo "**********************************"
echo "*** This needs to run as root! ***"
echo "**********************************"
echo ""
exit
fi

# Check to see if we got command line args
if [ ! -z $1 ]; then
   backup_path=$1
fi

if [ ! -z $2 ]; then
   retention_days=$2
fi

# Create trigger to force file system consistency check if image is restored
touch /boot/forcefsck

# Perform backup
dd if=/dev/mmcblk0 of=$backup_path/$HOSTNAME.$(date +%Y%m%d).img bs=1M

# Remove fsck trigger
rm /boot/forcefsck

# Delete old backups
find $backup_path/$HOSTNAME.*.img -mtime +$retention_days -type f -delete


sudo chmod +x /mnt/backup/system_backup.sh

sudo crontab -e
+ 0 3 * * * /mnt/backup/system_backup.sh
```
