# 07 Managing Logical Volumes
## Creating Logical Volumes
### Logical Volume Management (LVM) Concepts
1. Logical volume management (LVM)
    1. Physical devices
    2. Physical volumes (PVs)
    3. Physical extents (PEs)
    4. Volume groups (VGs)
    5. Logical volumes (LVs)
    6. Logical extents (LEs)
### Implementing LVM storage
1. Partition editor (Parted)
    ```bash
    $ parted <DEVICE> <COMMAND>
    $ parted /dev/vdb print
    ```
    ```bash
    $ parted -s <DEVICE> <COMMAND>
    $ parted -s /dev/vdb mkpart primary 1MiB 769MiB
    $ parted -s /dev/vdb mkpart primary 770MiB 1026MiB
    ```
    ```bash
    $ parted -s <DEVICE> <COMMAND>
    $ parted -s /dev/vdb set 1 lvm on
    $ parted -s /dev/vdb set 2 lvm on
    ```
2. Udev administrator (udevadm)
    ```bash
    $ udevadm settle
    ```
3. Physical volume scan (pvscan)
    ```bash
    $ pvscan
    ```
4. Physical volume create (pvcreate)
    ```bash
    $ pvcreate <PV>
    $ pvcreate /dev/vdb1
    $ pvcreate /dev/vdb2
    ```
5. Physical volume display (pvdisplay)
    ```bash
    $ pvdisplay <PV>
    $ pvdisplay /dev/vdb1
    $ pvdisplay /dev/vdb2
    ```
6. Volume group scan (vgscan)
    ```bash
    $ vgscan
    ```
7. Volume group create (vgcreate)
    ```bash
    $ vgcreate -s <PE_SIZE> <VG_NAME> <PV1> <PV2> ...
    $ vgcreate -s 10M vg0 /dev/vdb1 /dev/vdb2
    ```
8. Volume group display (vgdisplay)
    ```bash
    $ vgdisplay <VG>
    $ vgdisplay /dev/vg0
    ```
9. Logical volume scan (lvscan)
    ```bash
    $ lvscan
    ```
10. Logical volume create (lvcreate)
    ```bash
    $ lvcreate -l <PE_NUMBER> -n <LV_NAME> <VG_NAME>
    $ lvcreate -l 13 -n lv1 vg0
    ```
    ```bash
    $ lvcreate -L <SIZE> -n <LV_NAME> <VG_NAME>
    $ lvcreate -L 200M -n lv2 vg0
    ```
11. Logical volume display (lvdisplay)
    ```bash
    $ lvdisplay <LV>
    $ lvdisplay /dev/vg0/lv1
    $ lvdisplay /dev/vg0/lv2
    ```
12. Make file system (mkfs)
    ```bash
    $ mkfs.ext4 <DEVICE>
    $ mkfs.ext4 /dev/vg0/lv1
    ```
    ```bash
    $ mkfs.xfs <DEVICE>
    $ mkfs.xfs /dev/vg0/lv2
    ```
13. Make directory (mkdir)
    ```bash
    $ mkdir <DIRECTORY> #建立日錄(<DIRECTORY>)
    ```
    ```bash
    $ mkdir -p <DIRECTORY> #建立日錄(<DIRECTORY>)路徑所有目錄
    ```
    ```bash
    $ mkdir <DIRECTORY1> <DIRECTORY2> #建立多個日錄(<DIRECTORY>)
    $ mkdir /mnt/lv1 /mnt/lv2
    ```
14. `$ vim /etc/fstab`
    ```bash
    /dev/vg0/lv1                                /mnt/lv1           ext4     defaults    0 0
    /dev/vg0/lv2                                /mnt/lv2           xfs      defaults    0 0
    ```
15. Mount (mount)
    ```bash
    $ mount -a
    ```
16. Unmount (umount)
    ```bash
    $ umount <DEVICE|DIRECTORY>
    $ umount /dev/vg0/lv1
    $ umount /dev/vg0/lv2
17. `$ vim /etc/fstab`
    ```bash
    ```
18. Logical volume remove (lvremove)
    ```bash
    $ lvremove <LV>
    $ lvremove /dev/vg0/lv1
    $ lvremove /dev/vg0/lv2
    ```
19. Volume group remove (vgremove)
    ```bash
    $ vgremove <VG>
    $ vgremove /dev/vg0
    ```
20. Physical volume remove (pvremove)
    ```bash
    $ pvremove <PV>
    $ pvremove /dev/vdb1
    $ pvremove /dev/vdb2
    ```
21. Remove (rm)
    ```bash
    $ rm -r <DIRECTORY> #移除目錄(<DIRECTORY>)及所有子目錄檔案
    $ rm -r /mnt/lv1
    $ rm -r /mnt/lv2
    ```
## Exteding Logical Volumes
### Extending and Reducing a Volume Group
1. Partition editor (Parted)
    ```bash
    $ parted <DEVICE> <COMMAND>
    $ parted /dev/vdb print
    ```
    ```bash
    $ parted -s <DEVICE> <COMMAND>
    $ parted -s /dev/vdb mkpart primary 1027MiB 1539MiB
    ```
    ```bash
    $ parted -s <DEVICE> <COMMAND>
    $ parted -s /dev/vdb set 3 lvm on
    ```
2. Udev administrator (udevadm)
    ```bash
    $ udevadm settle
    ```
3. Physical volume scan (pvscan)
    ```bash
    $ pvscan
    ```
4. Physical volume create (pvcreate)
    ```bash
    $ pvcreate <PV>
    $ pvcreate /dev/vdb3
    ```
5. Physical volume display (pvdisplay)
    ```bash
    $ pvdisplay <PV>
    $ pvdisplay /dev/vdb3
    ```
6. Volume group scan (vgscan)
    ```bash
    $ vgscan
    ```
7. Volume group extend (vgextend)
    ```bash
    $ vgextend <VG_NAME> <PV>
    $ vgcreate vg0 /dev/vdb3
    ```
8. Volume group display (vgdisplay)
    ```bash
    $ vgdisplay <VG>
    $ vgdisplay /dev/vg0
    ```
9. Physical volume move (pvmove)
    ```bash
    $ pvmove <SOURCE_PV> <PV>
    $ pvmove /dev/vdb1 /dev/vdb3
    ```
10. Volume group reduce (vgreduce)
    ```bash
    $ vgreduce <PV>
    $ vgreduce /dev/vdb1
    ```
11. Physical volume remove (pvremove)
    ```bash
    $ pvremove <PV>
    $ pvremove /dev/vdb1
    ```
### Extending a Logical Volume and XFS File System
### Extending a Logical Volume and ext4 File System
1. Volume group display (vgdisplay)
    ```bash
    $ vgdisplay <VG>
    $ vgdisplay /dev/vg0
    ```
2. Logical volume scan (lvscan)
    ```bash
    $ lvscan
    ```
3. Logical volume extend (lvextend)
    ```bash
    $ lvextend -l <PE_NUMBER> <LV>
    $ lvextend -l 20 /dev/vg0/lv1
    ```
    ```bash
    $ lvextend -l +<PE_NUMBER> <LV>
    $ lvextend -l +7 /dev/vg0/lv1
    ```
    ```bash
    $ lvextend -L <SIZE> <LV>
    $ lvextend -L 300M /dev/vg0/lv2
    ```
    ```bash
    $ lvextend -L +<SIZE> <LV>
    $ lvextend -L +100M /dev/vg0/lv2
    ```
4. Logical volume display (lvdisplay)
    ```bash
    $ lvdisplay <LV>
    $ lvdisplay /dev/vg0/lv1
    $ lvdisplay /dev/vg0/lv2
    ```
5. Resize to file system (resize2fs)
    ```bash
    $ resize2fs <DEVICE>
    $ resize2fs /dev/vg0/lv1
    ```
6. XFS grow file system (xfs_growfs)
    ```bash
    $ xfs_growfs <DEVICE>
    $ xfs_growfs /dev/vg0/lv2
    ```
7. Disk free (df)
    ```bash
    $ df #查看檔案系統的可用磁碟空間
    ```
    ```bash
    $ df -h
    ```
### Extending a Logical Volume and swap space
1. Volume group display (vgdisplay)
    ```bash
    $ vgdisplay <VG>
    $ vgdisplay /dev/vg0
    ```
2. Swap off (swapoff)
    ```bash
    $ swapoff <DEVICE>
    $ swapoff /dev/vg0/vdb4
    ```
    ```bash
    $ swapoff -v <DEVICE>
    $ swapoff -v /dev/vg0/vdb4
    ```
2. Logical volume scan (lvscan)
    ```bash
    $ lvscan
    ```
3. Logical volume extend (lvextend)
    ```bash
    $ lvextend -l <PE_NUMBER> <LV>
    $ lvextend -l 20 /dev/vg0/lv4
    ```
    ```bash
    $ lvextend -l +<PE_NUMBER> <LV>
    $ lvextend -l +7 /dev/vg0/lv4
    ```
    ```bash
    $ lvextend -L <SIZE> <LV>
    $ lvextend -L 300M /dev/vg0/lv4
    ```
    ```bash
    $ lvextend -L +<SIZE> <LV>
    $ lvextend -L +100M /dev/vg0/lv4
    ```
4. Logical volume display (lvdisplay)
    ```bash
    $ lvdisplay <LV>
    $ lvdisplay /dev/vg0/lv4
    ```
5. Make swap (mkswap)
    ```bash
    $ mkswap <DEVICE>
    $ mkswap /dev/vg0/lv4
    ```
6. Swap on (swapon)
    ```bash
    $ swapon <DEVICE>
    $ swapon /dev/vdb4
    ```
    ```bash
    $ swapon -v <DEVICE>
    $ swapon -v /dev/vdb4
    ```
    ```bash
    $ swapon -a
    ```
## Return to [RH134 Red Hat System Administration II](/rh134_red_hat_system_administration_ii/README.md)
