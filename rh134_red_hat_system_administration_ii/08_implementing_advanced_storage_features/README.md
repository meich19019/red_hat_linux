# 08 Implementing Advanced Storage Features
## Managing Layered Storage with Stratic
### Describing the Architecture of Stratis
### Working with Stratis Storage
1. Yellow dog updater, modified (yum)
    ```bash
    $ yum install stratis-cli stratisd
    ```
2. Stratis (stratis)
    ```bash
    $ stratis pool create <POOL_NAME> <DEVICE>
    $ stratis pool create pool1 /dev/vdb
    ```
    ```bash
    $ stratis pool add-data <POOL> <DEVICE>
    $ stratis pool add-data pool1 /dev/vdc
    ```
    ```bash
    $ stratis blockdev list <POOL>
    $ stratis blockdev list pool1
    ```
    ```bash
    $ stratis filesystem create <POOL> <FILE_SYSTEM_NAME>
    $ stratis filesystem create pool1 fs1
    ```
    ```bash
    $ stratis filesystem list
    ```
    ```bash
    $ stratis filesystem snapshot <POOL> <FILE_SYSTEM> <SNAPSHOP_NAME>
    $ stratis filesystem snapshot pool1 fs1 snapshop1
    ```
3. `$ vim /etc/fstab`
    ```bash
    /stratis/pool1/fs1                          /mnt/fs1           xfs      defaults,x-systemd.requires=stratisd.service    0 0
    ```
4. Mount (mount)
    ```bash
    $ mount -a
    ```
## Compressing and Deduplicating Storage with VDO
### Describing Virtual Data Optimizer
### Implementing Virtual Data Optimizer
1. Yellow dog updater, modified (yum)
    ```bash
    $ yum install vdo kmod-kvdo
    ```
2. Virtual data optimizer (vdo)
    ```bash
    $ vdo create --name=<VDO_NAME> --device=<DEVICE> --vdoLogicalSize=<SIZE>
    $ vdo create --name=vdo1 --device=/dev/vdd --vdoLogicalSize=50G
    ```
    ```bash
    $ vdo status --name=<VDO>
    $ vdo status --name=vdo1
    ```
    ```bash
    $ vdo list
    ```
3. Udev administrator (udevadm)
    ```bash
    $ udevadm settle
    ```
4. Make file system (mkfs)
    ```bash
    $ mkfs.xfs <DEVICE>
    $ mkfs.xfs /dev/mapper/vdo1
    ```
5. `$ vim /etc/fstab`
    ```bash
    /dev/mapper/vdo1                          /mnt/vdo1           xfs      defaults,x-systemd.requires=vdo.service    0 0
    ```
6. Mount (mount)
    ```bash
    $ mount -a
    ```
7. Virtual data optimizer statistics (vdostats)
    ```bash
    $ vdostats --human-readable
    ```
## Return to [RH134 Red Hat System Administration II](/rh134_red_hat_system_administration_ii/README.md)
