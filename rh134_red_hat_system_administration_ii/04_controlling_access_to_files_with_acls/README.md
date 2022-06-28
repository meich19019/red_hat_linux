# 04 Controlling Access to Files with ACLs
## Interpreting File ACLs
### Access Control List Concepts
1. Access control list (ACL)  
    讓一個檔案可以有多個Owner及多個Group owner。
### Viewing and Interpreting ACL Permissions
1. `$ ls -l`
    ```bash
    drwxr-xr-x. 2 user user 4096 Feb  7 14:02 Desktop
     1  2  3  4
    ```
    1. User ACL
    2. ACL mask
    3. Other ACL
    4. ACL權限
        1. 有 (+)
        2. 無 (.)
2. Get file ACL (getfacl)
    ```bash
    $ getfacl <FILE|DIRECTORY>
    ```
### Examples of ACL Use by the Operating System
## Securing Files with ACLs
### Changing ACL File Permissions
1. Set file ACL (setfacl)
    ```bash
    $ setfacl -m <WHO>:<NAME>:<PERMISSION> <FILE>
    $ setfacl -m u:root:r-x /etc/passwd
    ```
    ```bash
    $ setfacl -m <WHO1>:<NAME1>:<PERMISSION1>,<WHO2>:<NAME2>:<PERMISSION2>,... <FILE>
    $ setfacl -m u::rwx,g:root:rX,o::- /etc/passwd
    ```
    ```bash
    $ getfacl <SOURCE_FILE> | setfacl --set-file=-<FILE>
    ```
    ```bash
    $ setfacl -m m::<PERMISSION> <FILE>
    $ setfacl -m m::r /etc/passwd
    ```
    ```bash
    $ setfacl -R -m m::<PERMISSION> <DIRECTORY>
    $ setfacl -R -m m::rX /etc
    ```
    ```bash
    $ getfacl -R <DIRECTORY> > <FILE>
    $ setfacl --set-file=<FILE>
    ```
    ```bash
    $ setfacl -x <WHO>:<NAME> <FILE>
    $ setfacl -x u:root /etc/passwd
    ```
    ```bash
    $ setfacl -x <WHO1>:<NAME1>,<WHO2>:<NAME2>,... <FILE>
    $ setfacl -x u:root,g:root /etc/passwd
    ```
    ```bash
    $ setfacl -b <FILE|DIRECTORY>
    ```
### Controlling Default ACL File Permissions
1. Set file ACL (setfacl)
    ```bash
    $ setfacl -m d:<WHO>:<NAME>:<PERMISSION> <DIRECTORY>
    $ setfacl -m d:u:root:r-x /etc
    ```
    ```bash
    $ setfacl -x d:<WHO>:<NAME> <DIRECTORY>
    $ setfacl -x d:u:root /etc
    ```
    ```bash
    $ setfacl -k <DIRECTORY>
    $ setfacl -k /etc
    ```
## Return to [RH134 Red Hat System Administration II](/rh134_red_hat_system_administration_ii/README.md)
