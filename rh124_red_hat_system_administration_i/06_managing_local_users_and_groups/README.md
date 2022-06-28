# 06 Managing Local Users and Groups
## Describing User and Group Concepts
### What is a User?
1. User
    1. Superuser
    2. System user
    3. Regular user
2. Identification (id)
    ```bash
    $ id
    ```
    ```bash
    $ id <USER>
    ```
3. List (ls)
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
4. Process status (ps)
    ```bash
    $ ps
    ```
    ```bash
    $ ps aux
    ```
5. Local users  
    本地使用者詳細資料存放在`/etc/passwd`。
6. `$ cat /etc/passwd`
    ```bash
    user01:x:1000:1000:User One:/home/user01:/bin/bash
    1      2 3    4    5        6            7
    ```
    1. 使用者名稱
    2. 使用者密碼
    3. User Identification (UID)
    4. Group Identification (GID)
    5. 註解
    6. 家目錄
    7. 使用者的Shell
7. Local users password  
    本地使用者密碼存放在`/etc/shadow`。
    1. Password Convert (pwconv)
        ```bash
        $ pwconv
        ```
    2. Password Unconvert (pwunconv)
        ```bash
        $ pwunconv
        ```
### What is a Group?
1. Group
    1. Primary group
    2. Supplementary groups
2. Local groups  
    本地群組詳細資料存放在`/etc/group`。
3. `$ cat /etc/group`
    ```bash
    group01:x:10000:user01,user02,usr03
    1       2 3     4
    ```
    1. 群組名稱
    2. 群組密碼
    3. Group Identification (GID)
    4. 隸屬成員
## Gain Superuser Access
### The Superuser
1. Root (root)
### Switching Users
1. Switch user (su)
    ```bash
    $ su root
    ```
    ```bash
    $ su -
    $ su - root
    ```
    ```bash
    $ su - <USER>
    ```
    ```bash
    $ su - <USER> -c <SCRIPT>
    ```
### Running Commands with Sudo
1. Substitute user do / Superuser do (sudo)  
    權限設定存放在`/etc/sudoers`，預設載入`/etc/sudoers.d`目錄下檔案內容。
    ```bash
    user01  ALL=(ALL)   NOPASSWD:ALL #不需要輸入密碼
    ```
    ```bash
    $ sudo <SCRIPT>
    ```
    ```bash
    $ sudo su -
    ```
    ```bash
    $ sudo -i
    ```
2. `$ cat /etc/sudoers`
    ```bash
    %wheel  ALL=(ALL)   ALL
    1       2   3       4  
    ```
    1. 使用者名稱或群組名稱，沒有符號為使用者名稱，有%符號為群組名稱
    2. 所在主機
    3. 轉換成的身份
    4. 被授權的指令
## Managing Local User Accounts
### Managing Local Users
1. User add (useradd)  
    建立使用者預設值存放在`/etc/login.defs`。
    ```bash
    $ useradd <USER> #建立使用者(<USER>)
    ```
2. User modify (usermod)
    ```bash
    $ usermod -c <COMMENT> <USER>
    ```
    ```bash
    $ usermod -g <GROUP> <USER>
    ```
    ```bash
    $ usermod -G <GROUP1>,<GROUP2>,... <USER>
    ```
    ```bash
    $ usermod -a -G <GROUP> <USER>
    ```
    ```bash
    $ usermod -m <USER>
    ```
    ```bash
    $ usermod -m -d <DIRECTORY> <USER>
    ```
    ```bash
    $ usermod -s <SHELL> <USER>
    $ usermod -s /sbin/nologin <USER>
    ```
    ```bash
    $ usermod -L <USER> #鎖定使用者(<USER>)
    ```
    ```bash
    $ usermod -U <USER> #解鎖使用者(<USER>)
    ```
3. User delete (userdel)
    ```bash
    $ userdel <USER>
    ```
    ```bash
    $ userdel -r <USER>
    ```
    ```bash
    $ find / -nouser -o -nogroup
    ```
4. Password (passwd)
    ```bash
    $ passwd #變更目前使用者密碼
    ```
    ```bash
    $ passwd <USER> #建立或變更使用者(<USER>)密碼
    ```
5. User identification (UID) ranges
    1. 0
    2. 1-200
    3. 201-999
    4. 1000+
## Managing Local Group Accounts
### Managing Local Groups
1. Group add (groupadd)  
    建立群組預設值存放在`/etc/login.defs`。
    ```bash
    $ groupadd <GROUP>
    ```
    ```bash
    $ groupadd -g <GROUP_ID> <GROUP>
    ```
    ```bash
    $ groupadd -r <GROUP>
    ```
2. Group modify (groupmod)
    ```bash
    $ groupmod -n <NEW_GROUP> <GROUP>
    ```
    ```bash
    $ groupmod -g <GROUP_ID> <GROUP>
    ```
3. Group delete (groupdel)
    ```bash
    $ groupdel <GROUP>
    ```
4. Group identification (GID) ranges
    1. 0-999
    2. 1000+
## Managing User Passwords
### Shadow Passwords and Password Policy
1. Local users password  
    本地使用者密碼存放在`/etc/shadow`。
2. `$ cat /etc/shadow`
    ```bash
    user03:$6$CSsXcYG1L/4ZfHr/$2W6evvJahUfzfHpc...:17933:0:99999:7:2:18113:
    1      2                                       3     4 5     6 7 8     9
            1 2                3
    ```
    1. 使用者名稱
    2. 使用者密碼
        1. 雜湊演算法
        2. 亂數產生的字串(加鹽)
        3. 密碼雜湊值
    3. 最後一次變更密碼的時間
    4. 最少要隔幾天才能變更密碼
    5. 最多幾天必須變更密碼
    6. 必須變更密碼前幾天開始提醒使用者
    7. 必須變更密碼後幾天未變更將使用者鎖定
    8. 使用者的使用期限
    9. 保留未使用
3. OpenSSL (openssl)
    ```bash
    $ echo <PASSWORD> | openssl md5
    ```
    ```bash
    $ echo <PASSWORD> | openssl sha
    ```
### Configuring Password Aging
1. Change age (chage)
    ```bash
    $ chage -l <USER>
    ```
    ```bash
    $ chage -d <DATE> <USER>
    $ chage -d 0 <USER>
    ```
    ```bash
    $ chage -m <DAY> <USER>
    ```
    ```bash
    $ chage -M <DAY> <USER>
    ```
    ```bash
    $ chage -W <DAY> <USER>
    ```
    ```bash
    $ chage -I <DAY> <USER>
    ```
    ```bash
    $ chage -E <DATE> <USER>
    $ usermod -L -e <DATE> <USER>
    ```
### Restricting Access
1. User modify (usermod)
    ```bash
    $ usermod -s <SHELL> <USER>
    $ usermod -s /sbin/nologin <USER>
    ```
2. Linux pluggable authentication modules (PAM) Linux可插拔身份驗證模塊
    1. DUO
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
