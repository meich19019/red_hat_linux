# 15 Accessing Linux File Systems
## Identifying File Systems and Devices
### Storage Management Concepts
1. List small computer system interface device (lsscsi)
    ```bash
    $ lsscsi
    ```
2. List block device (lsblk)
    ```bash
    $ lsblk
    ```
3. Device partitions
    ```bash
    $ cat /proc/partitions
    ```
### Examining File Systems
1. Disk free (df)
    ```bash
    $ df #查看檔案系統的可用磁碟空間
    ```
    ```bash
    $ df -h
    ```
2. Disk usage (du)
    ```bash
    $ du <FILE|DIRECTORY>
    ```
    ```bash
    $ du -s <FILE|DIRECTORY>
    ```
    ```bash
    $ du -h <FILE|DIRECTORY>
    ```
## Mounting and Unmounting File Systems
### Mounting File Systems Manually
1. List block device (lsblk)
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
2. Mount (mount)
    ```bash
    $ mount <DEVICE> <DIRECTORY>
    $ mount /dev/vdb1 /mnt/data
    ```
### Automatic Mounting of Removable Storage Devices
### Unmounting File Systems
1. Unmount (umount)
    ```bash
    $ umount <DIRECTORY>
    $ umount /mnt/data
    ```
2. List open files (lsof)
    ```bash
    $ lsof <DIRECTORY>
    ```
## Locating Files on the System
### Searching for Files
1. Locate (locate)
2. Find (find)
### Locating Files by Name
1. Update Database (updatedb)  
    把檔案路徑存在資料庫中供locate查詢，檔案路徑資料庫存放在`/var/lib/mlocate/mlocate.db`。
    ```bash
    $ updatedb
    ```
2. Locate (locate)
    ```bash
    $ locate <KEYWORD>
    ```
    ```bash
    $ locate -i <KEYWORD>
    ```
    ```bash
    $ locate -r <REGEX_KEYWORD>
    ```
    ```bash
    $ locate -n <NUMBER> <KEYWORD>
    ```
### Searching for Files in Real Time
1. Find (find)
    ```bash
    $ find -name <FILE_NAME>
    $ find -name passwd
    ```
    ```bash
    $ find <DIRECTORY> -name <FILE_NAME>
    $ find / -name passwd
    $ find / -name '*.txt'
    ```
    ```bash
    $ find <DIRECTORY> -iname <FILE_NAME>
    ```
    ```bash
    $ find <DIRECTORY> -user <USER>
    ```
    ```bash
    $ find <DIRECTORY> -group <GROUP>
    ```
    ```bash
    $ find <DIRECTORY> -uid <UID>
    ```
    ```bash
    $ find <DIRECTORY> -gid <GID>
    ```
    ```bash
    $ find <DIRECTORY> -user <USER> -group <GROUP>
    ```
    ```bash
    $ find <DIRECTORY> -user <USER> -o -group <GROUP>
    ```
    ```bash
    $ find <DIRECTORY> -perm <LOGICAL_OPERATOR><USER_NUMBER><GROUP_NUMBER><OTHER_NUMBER>
    $ find / -perm 660
    $ find / -perm -324
    $ find / -perm /442
    ```
    ```bash
    $ find <DIRECTORY> -size <COMPARISON_OPERATOR><SIZE>
    $ find / -size 10M
    $ find / -size +10G
    $ find / -size -10k
    ```
    ```bash
    $ find <DIRECTORY> -mmin <COMPARISON_OPERATOR><MINUTES>
    $ find / -mmin 120
    ```
    ```bash
    $ find <DIRECTORY> -mtime <COMPARISON_OPERATOR><DAYS>
    $ find / -mtime -3
    ```
    ```bash
    $ find <DIRECTORY> -amin <COMPARISON_OPERATOR><MINUTES>
    $ find / -amin +240
    ```
    ```bash
    $ find <DIRECTORY> -atime <COMPARISON_OPERATOR><DAYS>
    $ find / -atime 5
    ```
    ```bash
    $ find <DIRECTORY> -cmin <COMPARISON_OPERATOR><MINUTES>
    $ find / -cmin +60
    ```
    ```bash
    $ find <DIRECTORY> -ctime <COMPARISON_OPERATOR><DAYS>
    $ find / -ctime -7
    ```
    ```bash
    $ find <DIRECTORY> -type <FILE_TYPE>
    $ find / -type f
    $ find / -type d
    $ find / -type l
    $ find / -type b
    ```
    ```bash
    $ find <DIRECTORY> -type <FILE_TYPE> -links <COMPARISON_OPERATOR><NUMBER>
    $ find / -type f -links +1
    ```
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
