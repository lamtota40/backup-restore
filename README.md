# backup-restore
backup and restore
- From partition to partition <br>
```console
sudo dd if=/dev/sda2 of=/dev/sda3 bs=1M status=progress
```
- From partition to raw(img) <br>
```console
sudo dd if=/dev/hda of=/path/to/dir/hda.raw bs=1M status=progress
```
- From ISO(CD) to flashdrive <br>
```console
sudo dd if=openSUSE-Leap-15.1-DVD-x86_64.iso of=/dev/sdc bs=1M status=progress
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
- Example Clone(*) <br>
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
- To convert raw(img) to qcow2:
```console
sudo qemu-img convert -f raw -O qcow2 vm_hdd.img vm_hdd.qcow2
```
- To convert qcow2 to raw(img):
```console
sudo qemu-img convert -f qcow2 -O raw /path/to/image.qcow2 /path/to/image.img
```
- To convert partiton(raw) to qcow2:
```console
sudo qemu-img convert -f raw -O qcow2 /dev/sda2 image.qcow2
```
https://manpages.ubuntu.com/manpages/xenial/man1/ccd2iso.1.html
# install iso
wget n9.cl/win7ulti1 -O win7.iso
audo mkdir /mnt/win7setup
sudo nano /etc/fstab
>add /dev/sda3 /mnt/win7setup
reboot
unetbootin installtype=HDD targetdrive=/dev/win7setup/
