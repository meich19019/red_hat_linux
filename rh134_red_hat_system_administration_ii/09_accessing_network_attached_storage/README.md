# 09 Accessing Network-Attached Storage
## Mounting Network-Attached Storage with NFS
### Mounting and Unmounting NFS Shares
1. Mount (mount)
    ```bash
    $ mount -t nfs <REMOTE_HOST>:<REMOTE_DIRECTORY> <DIRECTORY>
    $ mount -t nfs serverb.lab.example.com:/shares/direct/external /mnt
    ```
    ```bash
    $ mount -t nfs -o <OPTION> <REMOTE_HOST>:<REMOTE_DIRECTORY> <DIRECTORY>
    $ mount -t nfs -o rw,sync serverb.lab.example.com:/shares/direct/external /mnt
    ```
2. `$ vim /etc/fstab`
    ```bash
    serverb.lab.example.com:/shares                         /mnt           nfs      rw,sync    0 0
    ```
3. Unmount (umount)
    ```bash
    $ umount <DEVICE|DIRECTORY>
    $ umount /mnt
## Automounting Network-Attached Storage
### Mounting NFS Shares with the Automounter
1. Yellow dog updater, modified (yum)
    ```bash
    $ yum install autofs
    ```
2. Automount file system (autofs)  
    自動掛載設定存放在`/etc/auto.master`，預設載入`/etc/auto.master.d`目錄下檔案內容，檔名必須為`.autofs`結尾。
3. Direct maps test
    ```bash
    $ mount -t nfs serverb.lab.example.com:/shares/direct/external /mnt
    ```
    ```bash
    $ ls -l /mnt
    ```
    ```bash
    $ umount /mnt
    ```
4. `$ vim /etc/auto.master.d/direcct.autofs`
    ```bash
    /-     /etc/auto.direct
    1           2
    ```
    1. 直接自動掛載固定為/-
    2. 自訂設定檔
5. `$ vim /etc/auto.direct`
    ```bash
    /external   -rw,sync,fstype=nfs4    serverb.lab.example.com:/shares/direct/external
    1           2                       3
    ```
    1. 直接自動掛載自定存取目錄
    2. 參數
    3. 掛載設備
6. Indirect maps test
    ```bash
    $ mount -t nfs serverb.lab.example.com:/shares/indirect /mnt
    ```
    ```bash
    $ ls -l /mnt
    ```
    ```bash
    $ umount /mnt
    ```
7. `$ vim /etc/auto.master.d/indirect.autofs`
    ```bash
    /internal     /etc/auto.indirect
    1           2
    ```
    1. 間接自動掛載自訂存取目錄
    2. 自訂設定檔
8. `$ vim /etc/auto.indirect`
    ```bash
    *   -rw,sync,fstype=nfs4    serverb.lab.example.com:/shares/indirect/&
    1   2                       3
    ```
    1. 存取目錄下任意
    2. 參數
    3. 掛載設備
9. System control (systemctl)
    ```bash
    $ systemctl enable <UNIT_NAME>.<UNIT_TYPE> --now
    $ systemctl enable autofs.service --now
    ```
    ```bash
    $ systemctl reboot
    ```
## Return to [RH134 Red Hat System Administration II](/rh134_red_hat_system_administration_ii/README.md)
