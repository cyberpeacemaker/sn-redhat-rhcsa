```shell
pvcreate, vgcreate, lvcreate
mkfs
pvdisplay, vgdisplay, lvdisplay, pvs, vgs, lvs
vgextend, lvextend, xfs-growfs, resize2fs
pvmove, vgreduce, lvremove, pvremove
```

- physical divice, extents, [pv, pe], vg, [lv, le]
- set lvm type, label pv, cerate vg, create lv
- extend [lv, fs], [swapoff, lvextend, mkswap, swapon]
- reduce, remove[umount, lv, vg, pv]