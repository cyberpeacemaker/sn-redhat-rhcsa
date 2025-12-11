```shell
df, du, lsblk, lsof, locate, updatedb, find

{-mmin-amin-cmin-mtime}
find / -mmin 2 2>/dev/null
find / -path /proc -prune -o -path /run/systemed -prune -o -mmin 2 -print
```

- XFS, ext4, exFAT
- mount point, block {storage, device}, removable media
- SCSI{SATA, SAS, USB}, NVMe (SSDs), paravirtualized VMs {virtio-blk, virtil-scsi}, SD Cards
- VG, LV, LVM
- tmpfs, devtmpfs, /etc/fstab
- UUID
- find {name, type, user, group, perm, size, time}, -exec <command> {} +

### **Key differences**

* **`find`** → “where is this file on disk right now?”
* **`locate`** → “where *might* this file be according to the database?”
* **`grep`** → “which files contain this text?”


