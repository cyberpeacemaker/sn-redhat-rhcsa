```shell
parted, mkpart, udevadm settle
mkswap, swapon, free
lsblk, systemctl daemon-reload
```
`/etc/fstab`

- fstab(1)
- partition, label,  register, {file system/(make swap)}
- persist {mount/acitvate}, register
- [swap, hibernation, signature, priority, [dump flag, fsck order]]