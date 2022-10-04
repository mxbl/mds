# TOC

- [TOC](#toc)
- [Install (Bullseye)](#install-bullseye)
- [Create the Pool](#create-the-pool)
- [Provisioning file systems or volume](#provisioning-file-systems-or-volume)
- [Snapshots](#snapshots)
- [NFS shares](#nfs-shares)
- [Commands](#commands)

**Sources:**
- [wiki.debian.org/ZFS](https://wiki.debian.org/ZFS)
- [ZFS on Linux](https://www.stefanux.de/wiki/doku.php/linux/zfs)

# Install (Bullseye)
```
apt install linux-headers-amd64 dkms
apt install zfs-dkms
modprobe zfs
apt install zfsutils-linux
```

**Load modul at boot time:**
`echo "zfs" >> /etc/modules-load.d/modules.conf`


# Create the Pool
`zpool create tank [mirror raidz raidz2] DISK_IDs`

- Disk ids can be retrieved from **/dev/disk/by-id/**
- **mirror:** like raid-1, 1:1 redundancy
- tank is the name


# Provisioning file systems or volume
**ZVOL:**
```
zfs create -s -V 4G tank/vol
mkfs.ext4 /dev/zvol/tank/vol
mount /dev/zvol/tank/vol /mnt
```

**file system:**
```
mkdir -p /data
zfs create -o mountpoint=/data tank/data
```

**and destroy them again:**
```
zfs destroy tank/data
umount /dev/zvol/tank/vol
zfs destroy tank/vol
```


# Snapshots

**Make and remove a snapashot of tank/data:**
```
zfs snapshot tank/data@2022-01-04
zfs destroy tank/data@2022-01-04
```


# NFS shares


# Commands
```
zfs list -o name,type,mountpoint
zpool status
zpool list
```
