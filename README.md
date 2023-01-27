# backup-restore
backup and restore

sudo apt install qemu-utils virtualbox-ext-pack -y

# Backup/Restore with compress
- install <br>
sudo apt-get install gzip -y
- Backup <br>
dd if=/dev/sdX | gzip -c > path/to/your-backup.img.gz
- Restore <br>
gunzip -c /path/to/your-backup.img.gz | dd of=/dev/sdX


sudo dd if=openSUSE-Leap-15.1-DVD-x86_64.iso of=/dev/sdc bs=4M status=progress

dd if=/dev/hda of=/path/to/dir/hda.raw


qemu-img convert -O qcow2 /path/to/dir/hda.raw /path/to/dir/hda.qcow2

qemu-img convert -O qcow2 /dev/hda /path/to/dir/hda.qcow2



sudo VBoxManage clonehd input.vhd output.img --format RAW
# Convert
- install <br>
sudo apt install virtualbox-ext-pack -y
VBoxManage convertfromraw myfile.raw myfile.vhd --format VHD

VDI|VMDK|VHD|RAW|<other>
