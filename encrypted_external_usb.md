# Encrypt External Drive

## Setup Filesystem and Encryption
1. Check device name `sudo fdisk -l` (say it's `/dev/sdx`)
1. Optionally: Overwrite with random data `sudo shred -v -n 1 /dev/sdx`
1. Set up a new dm-crypt device in LUKS encryption mode: `sudo cryptsetup luksFormat /dev/sdx`.
You'll have to provide a password here.
1. Open the device and setup mapping with name provided `sudo cryptsetup luksOpen /dev/sdx <mapping_name>`
1. Run ext4 filesystem and label it `mkfs.ext4 -L <label> /dev/sdx`
1. Mount the device `sudo mount /dev/mapper/<mapping_name> /media/<label>`

Done!
Remenber that you have to run
```bash
sudo cryptsetup luksOpen /dev/sdx <mapping_name>
sudo mount /dev/mapper/<mapping_name> /media/<label>
```
when plugging in the drive, and
```bash
sudo umount /media/<label>
sudo cryptsetup luksClose <mapping_name>
```

## Giving right to `plugdev`
Since the owner of the device is `root`, and only `root` may write to it.
To change that, run 
```bash
chown root:plugdev /media/<label>
chmod 1770 /media/<label>
```
with the disk mounted.

To persist the permissions give the filesystem a label such that it is mounted at the same mount point every time.
First unmount the drive, then run
```bash
tune2fs -L <label2>
```
That's it :)

References:
* https://www.linuxquestions.org/questions/slackware-14/automount-luks-encrypted-usb-disk-as-regular-user-765227/
* https://linux.tips/tutorials/how-to-encrypt-a-usb-drive-on-linux-operating-system


