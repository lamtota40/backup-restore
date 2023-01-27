# backup-restore
backup and restore

dd if=/dev/hda of=/path/to/dir/hda.raw
qemu-img convert -O qcow2 /path/to/dir/hda.raw /path/to/dir/hda.qcow2

qemu-img convert -O qcow2 /dev/hda /path/to/dir/hda.qcow2
