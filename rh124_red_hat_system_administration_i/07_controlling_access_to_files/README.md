# 07 Controlling Access to Files
## Interpreting Linux File System Permissions
### Linux File-system Permissions
1. Read (r)
    1. 檔案
    2. 目錄
2. Write (w)
    1. 檔案
    2. 目錄
3. Execute (x)
    1. 檔案
    2. 目錄
### Viewing File and Directory Permissions and Ownership
1. List (ls)
    ```bash
    $ ls #查看工作目錄下檔案名稱
    ```
    ```bash
    $ ls <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)下檔案或目錄名稱
    ```
    ```bash
    $ ls -l <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)下檔案或目錄名稱及詳細資訊
    ```
    ```bash
    $ ls -d <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)本身名稱
    ```
    ```bash
    $ ls -ld <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)本身名稱及詳細資訊
    ```
### Examples of Permission Effects
1. List (ls)
    ```bash
    $ ls #查看工作目錄下檔案名稱
    ```
    ```bash
    $ ls <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)下檔案或目錄名稱
    ```
    ```bash
    $ ls -l <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)下檔案或目錄名稱及詳細資訊
    ```
    ```bash
    $ ls -a <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)下包含隱藏檔案的所有檔案或目錄名稱
    ```
    ```bash
    $ ls -la <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)下包含隱藏檔案的所有檔案或目錄名稱及詳細資訊
    ```
## Managing File System Permissions from the Command Line
### Changing File and Directory Permissions
1. Change mode (chmod)
    ```bash
    $ chmod <WHO><WHAT><WHICH> <FILE|DIRECTORY>
    $ chmod u+x <FILE|DIRECTORY>
    $ chmod go-rw <FILE|DIRECTORY>
    $ chmod a+w <FILE|DIRECTORY>
    $ chmod u-w,g+w-x,o=rwx <FILE|DIRECTORY>
    ```
    ```bash
    $ chmod -R <WHO><WHAT><WHICH> <FILE|DIRECTORY>
    ```
    ```bash
    $ chmod <USER_NUMBER><GROUP_NUMBER><OTHER_NUMBER> <FILE|DIRECTORY>
    $ chmod 644 <FILE|DIRECTORY>
    ```
### Changing File and Directory User or Group Ownership
1. Change owner (chown)
    ```bash
    $ chown <USER> <FILE|DIRECTORY>
    ```
    ```bash
    $ chown -R <USER> <FILE|DIRECTORY>
    ```
    ```bash
    $ chown :<GROUP> <FILE|DIRECTORY>
    ```
    ```bash
    $ chown <USER>:<GROUP> <FILE|DIRECTORY>
    ```
2. Change group (chgrp)
    ```bash
    $ chgrp <GROUP> <FILE|DIRECTORY>
    ```
## Managing Default Permissions and File Access
### Special Permissions
1. Setuid (suid)
    1. 檔案
    2. 目錄
2. Setgid (sgid)
    1. 檔案
    2. 目錄
3. Sticky (sticky)
    1. 檔案
    2. 目錄
4. Change mode (chmod)
    ```bash
    $ chmod <WHO><WHAT><WHICH> <FILE|DIRECTORY>
    $ chmod u+s <FILE|DIRECTORY>
    $ chmod g+s <FILE|DIRECTORY>
    $ chmod o+t <FILE|DIRECTORY>
    $ chmod u=rwxs,g=rs,o=xt <FILE|DIRECTORY>
    ```
    ```bash
    $ chmod -R <WHO><WHAT><WHICH> <FILE|DIRECTORY>
    ```
    ```bash
    $ chmod <SPECIAL_NUMBER><USER_NUMBER><GROUP_NUMBER><OTHER_NUMBER> <FILE|DIRECTORY>
    $ chmod 2770 <FILE|DIRECTORY>
    ```
### Default File Permissions
1. Initial permissions
    1. File or directory permissions
    2. Umask (umask)
        ```bash
        $ umask
        ```
        ```bash
        $ umask <SPECIAL_NUMBER><USER_NUMBER><GROUP_NUMBER><OTHER_NUMBER>
        ```
2. Default file or directory permissions
    1. 檔案  
        預設權限為0666。
    2. 目錄  
        預設權限為0777。
2. Default umask  
    各使用者UID預設umask存放在`/etc/profile`。
    1. 0-199  
        預設權限遮罩為002。
    2. 200+  
        預設權限遮罩為022。
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
