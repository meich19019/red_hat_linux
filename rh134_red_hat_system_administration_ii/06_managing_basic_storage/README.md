# 06 Managing Basic Storage
## Adding Partitions, File Systems, and Persistent Mounts
### Partitioning a Disk
### Managing Partitions with Parted
1. Partition editor (Parted)
    ```bash
    $ parted <DEVICE>
    (parted) <COMMAND>
    $ parted /dev/vda
    (parted) print
    (parted) quit
    $ parted <DEVICE> <COMMAND>
    $ parted /dev/vda print
    ```
    ```bash
    $ parted <DEVICE> unit <UNIT> <COMMAND>
    $ parted /dev/vda unit s print
    ```
    ```bash
    $ parted <DEVICE> <COMMAND>
    $ parted /dev/vda mklabel msdos
    $ parted /dev/vda mklabel gpt
    ```
    ```bash
    $ parted <DEVICE> <COMMAND>
    $ parted /dev/vda help mkpart
    ```
    ```bash
    $ parted <DEVICE>
    (parted) <COMMAND>
    $ parted /dev/vda
    (parted) mkpart
    Partition type?  primary/extended? primary
    File system type?  [ext2]? xfs
    Start? 2048s
    End? 1000MB
    (parted) quit
    $ parted <DEVICE> <COMMAND>
    $ parted /dev/vda mkpart primary xfs 2048s 1000MB
    ```
    ```bash
    $ parted <DEVICE>
    (parted) <COMMAND>
    $ parted /dev/vda
    (parted) mkpart
    Partition name?  []? usersdata
    File system type?  [ext2]? xfs
    Start? 2048s
    End? 1000MB
    (parted) quit
    ```
    ```bash
    $ parted /dev/vda print
    $ parted /dev/vda rm <PARTITION_NUMBER>
    ```
2. Udev administrator (udevadm)
    ```bash
    $ udevadm settle
    ```
### Creating File Systems
1. Make file system (mkfs)
    ```bash
    $ mkfs.xfs <DEVICE>
    $ mkfs.xfs /dev/vda1
    ```
2. List block device (lsblk)
    ```bash
    $ lsblk
    ```
    ```bash
    $ lsblk -f
    ```
    ```bash
    $ lsblk -p
    ```
    ```bash
    $ lsblk -fp
    ```
### Mounting File Systems
1. Mount (mount)
    ```bash
    $ mount
    ```
    ```bash
    $ mount <DEVICE> <DIRECTORY>
    $ mount /dev/vdb1 /mnt/data
    ```
    ```bash
    $ mount -a
    ```
2. File system table (fstab)
    檔案系統掛載存放在`/etc/fstab`。
3. `$ cat /etc/fstab`
    ```bash
    UUID=a8063676-44dd-409a-b584-68be2c9f5570   /           xfs     defaults    0 0
    1                                           2           3       4           5 6
    ```
    1. 掛載裝置
    2. 掛載位置
    3. 檔案系統
    4. 參數
    5. dump是否備份
        1. 0 不備份
        2. 1 備份
    6. 開機時是否使用fsck驗證檔案系統
4. `$ vim /etc/fstab`
    ```bash
    UUID=a8063676-44dd-409a-b584-68be2c9f5570   /           xfs     defaults    0 0
    /dev/vda1                                   /mnt/data   xfs     defaults    0 0
    ```
5. Partition backup and restore
    ```bash
    $ dd if=<DEVICE> of=<FILE> bs=<BLOCK_SIZE>
    $ dd if=/dev/vda1 of=/tmp/vda1.dd bs=2M
    ```
    ```bash
    $ dd if=<FILE> of=<DEVICE> bs=<BLOCK_SIZE>
    $ dd if=/tmp/vda1.dd of=/dev/vda1 bs=2M
    ```
    ```bash
    $ dd if=<DEVICE> of=<DEVICE> bs=<BLOCK_SIZE>
    $ dd if=/dev/vda of=/dev/vdb bs=10M
    ```
## Managing Swap Space
### Introducing Swap Space Concepts
### Creating a Swap Space
1. Partition editor (Parted)
    ```bash
    $ parted <DEVICE> <COMMAND>
    $ parted /dev/vdb print
    ```
    ```bash
    $ parted <DEVICE>
    (parted) <COMMAND>
    $ parted /dev/vdb
    (parted) mkpart
    Partition name?  []? swap
    File system type?  [ext2]? linux-swap
    Start? 1001MB
    End? 1257MB
    (parted) quit
    ```
2. Udev administrator (udevadm)
    ```bash
    $ udevadm settle
    ```
3. Make swap (mkswap)
    ```bash
    $ mkswap <DEVICE>
    $ mkswap /dev/vdb2
    ```
4. Swap on (swapon)
    ```bash
    $ swapon <DEVICE>
    $ swapon /dev/vdb2
    ```
    ```bash
    $ swapon -v <DEVICE>
    $ swapon -v /dev/vdb2
    ```
    ```bash
    $ swapon -a
    ```
5. Free (free)
    ```bash
    $ free
    ```
6. `$ vim /etc/fstab`
    ```bash
    UUID=39e2667a-9458-42fe-9665-c5c854605881   swap           swap     defaults    0 0
    UUID=cb7f71ca-ee82-430e-ad4b-7dda12632328   swap           swap     pri=10      0 0
    ```
## Return to [RH134 Red Hat System Administration II](/rh134_red_hat_system_administration_ii/README.md)
