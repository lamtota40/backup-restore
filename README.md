# backup-restore
backup and restore
- From partition to img/raw <br>
```console
sudo dd if=/dev/hda of=/path/to/dir/hda.raw
```
- From ISO(CD) to flashdrive <br>
```console
sudo dd if=openSUSE-Leap-15.1-DVD-x86_64.iso of=/dev/sdc bs=4M status=progress
```
# Backup/Restore with compress
- install <br>
```console
sudo apt-get install gzip -y
```
- Backup <br>
```console
sudo dd if=/dev/sdX | gzip -c > path/to/your-backup.img.gz
```
- Restore <br>
```console
sudo gunzip -c /path/to/your-backup.img.gz | dd of=/dev/sdX
```

# Convert with VirtualBox
- Install <br>
```console
sudo apt install virtualbox-ext-pack -y
```
- Format option <br>
```VDI```/```VMDK```/```VHD```/```RAW```/other
- Example Convert <br>
```console
sudo VBoxManage convertfromraw myfile.raw myfile.vhd --format VHD
```
- Example Cloning(*) <br>
```console
sudo VBoxManage clonehd myfile.vhd myfile.raw --format RAW
```
(*)This command duplicates a registered virtual hard disk image to a new image file with a new unique identifier (UUID).
# Convert with Qemu
- Install <br>
```console
sudo apt install qemu-utils -y
```
- Format option<br>
<img src="https://user-images.githubusercontent.com/26719371/215086857-4c76bcf4-e5b9-4692-9dab-272a457bb909.jpg" width="200">

- To convert vhd to qcow2:
```console
sudo qemu-img convert -p -f vpc -O qcow2 windowsdata.vhd windowsdata.qcow2
```
- To convert raw to qcow2:
```console
sudo qemu-img convert -f raw -O qcow2 vm_hdd.img vm_hdd.qcow2
```
qemu-img convert -O qcow2 /path/to/dir/hda.raw /path/to/dir/hda.qcow2

qemu-img convert -O qcow2 /dev/hda /path/to/dir/hda.qcow2
