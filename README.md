# backup-restore
backup and restore

# Backup/Restore with compress
- install <br>
```console
sudo apt-get install gzip -y
```
- Backup <br>
```console
dd if=/dev/sdX | gzip -c > path/to/your-backup.img.gz
```
- Restore <br>
```console
gunzip -c /path/to/your-backup.img.gz | dd of=/dev/sdX
```

sudo dd if=openSUSE-Leap-15.1-DVD-x86_64.iso of=/dev/sdc bs=4M status=progress

dd if=/dev/hda of=/path/to/dir/hda.raw


sudo VBoxManage clonehd input.vhd output.img --format RAW
# Convert with VirtualBox
- Install <br>
```console
sudo apt install virtualbox-ext-pack -y
```
- Format option <br>
```VDI```/```VMDK```/```VHD```/```RAW```/other
- Example Command <br>
```console
VBoxManage convertfromraw myfile.raw myfile.vhd --format VHD
```
# Convert with Qemu
- Install <br>
```console
sudo apt install qemu-utils -y
```
- Format option<br>
<img src="https://user-images.githubusercontent.com/26719371/215086857-4c76bcf4-e5b9-4692-9dab-272a457bb909.jpg" width="200">

- To convert vhd to qcow2:
```console
qemu-img convert -p -f vpc -O qcow2 windowsdata.vhd windowsdata.qcow2
```
- To convert raw to qcow2:
```console
qemu-img convert
```
qemu-img convert -O qcow2 /path/to/dir/hda.raw /path/to/dir/hda.qcow2

qemu-img convert -O qcow2 /dev/hda /path/to/dir/hda.qcow2
