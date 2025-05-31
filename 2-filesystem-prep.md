# filesystem-prep

## commands used to format disks
### confirm which disk the OS is on, so you don't delete yourself
```
lsblk -f
df /
lsblk -f | grep -v loop
```

in this case, working with a server that was prev. used as a windows server. Need to format the disks for linux ext4

```
gob@gob-X10SLM-F:~$ lsblk -f |  grep -v loop
NAME   FSTYPE   FSVER LABEL           UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
sda
└─sda1 ntfs           OS              EABA4919BA48E423
sdb
├─sdb1 ntfs           System Reserved CE10416B10415C19
└─sdb2 ntfs           F               C40ED9AB0ED99730
sdc
├─sdc1
└─sdc2 ext4     1.0                   69f851b3-26b0-4976-bae8-8e496ef2fdcc  194.2G     6% /
sr0

gob@gob-X10SLM-F:~$ df /
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sdc2      229637452 14295304 203604396   7% /
```

**don't touch /dev/sdc2**

### wiping the windows ntfs formatted drives
I don't need to unmount the sda or sdb disk is not mounted because of the empty MOUNTPOINTS column entries for them.
```
# wipe
sudo wipefs -a /dev/sda

# create new partition table
sudo parted /dev/sda -- mklabel gpt

# create new partition
sudo parted -a optimal /dev/sda -- mkpart primary ext4 0% 100%

# format the new partition
sudo mkfs.ext4 /dev/sda1
```
### mounting the formatted partitions
```
# create mount point
sudo mkdir -p /mnt/disk1

# mount
sudo mount /dev/sda1 /mnt/disk1

# add to fstab for automatic mounting
# get uuid
sudo blkid /dev/sda1

# edit /etc/fstab
86a2c0ea-b99d-4ee7-badf-f3caf2feba77  /mnt/disk1  ext4  defaults  0  2

#apply changes
sudo mount -a
systemctl daemon-reload

```
### repeat the above steps for sdb

```
gob@gob-X10SLM-F:~$ ls /mnt
disk1  disk2
```