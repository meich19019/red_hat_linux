# 05 Managing SELinux Security
## Changing the SELinux Enforcement Mode
### How SELinux Protects Resources
1. Security-enhanced linux (SELinux)
### Why use Security Enhanced Linux?
### Basic SELinux security concepts
1. Process status (ps)
    ```bash
    $ ps
    ```
    ```bash
    $ ps axZ
    ```
2. List (ls)
    ```bash
    $ ls #查看工作目錄下檔案名稱
    ```
    ```bash
    $ ls <FILE|DIRECTORY> #查看檔案或目錄(<FILE|DIRECTORY>)下檔案或目錄名稱
    ```
    ```bash
    $ ls -Z <FILE|DIRECTORY>
    ```
3. `$ ls -Z`
    ```bash
    system_u:object_r:var_t:s0
    1        2        3     4
    ```
    1. 代表User
    2. 代表Role
    3. 代表Type，在SELINUXTYPE=targeted時，只需專注於Type欄位
    4. 擴增項目
### Changing the current SELinux mode
1. Get enforce (getenforce)
    ```bash
    $ getenforce
    ```
2. Set enforce (setenforce)
    ```bash
    $ setenforce
    ```
    ```bash
    $ setenforce <MODE>
    $ setenforce permissive
    $ setenforce enforcing
    ```
### Setting the default SELinux mode
1. Security-enhanced linux (SELinux)  
    存取控制安全增強設定存放在`/etc/selinux/config`。
2. `$ cat /etc/selinux/config`
    ```bash
    SELINUX=enforcing
    SELINUXTYPE=targeted
    ```
## Controlling SELinux File Contexts
### Initial SELinux Context
### Changing the SELinux context of a file
1. Change context (chcon)
    ```bash
    $ chcon -u <USER_CONTEXT> <FILE|DIRECTORY>
    ```
    ```bash
    $ chcon -r <ROLE_CONTEXT> <FILE|DIRECTORY>
    ```
    ```bash
    $ chcon -t <TYPE_CONTEXT> <FILE|DIRECTORY>
    ```
    ```bash
    $ chcon --reference <SOURCE_FILE|SOURCE_DIRECTORY> <FILE|DIRECTORY>
    ```
2. Restore context (restorecon)
    ```bash
    $ restorecon <FILE|DIRECTORY>
    ```
    ```bash
    $ restorecon -v <FILE|DIRECTORY>
    ```
    ```bash
    $ restorecon -R <FILE|DIRECTORY>
    ```
### Defining SELinux Default File Context Rules
1. SELinux manage (semanage)
    ```bash
    $ semanage fcontext -l
    ```
    ```bash
    $ semanage fcontext -a -f <FILE_TYPE> -t <TYPE_CONTEXT> <RANGE>
    $ semanage fcontext -a -f a -t httpd_sys_content_t 'WWW(/.*)?'
    ```
2. SELinux search (sesearch)
    ```bash
    $ sesearch -A
    ```
    ```bash
    $ sesearch -s <SOURCE_TYPE_CONTEXT>
    ```
    ```bash
    $ sesearch -t <TYPE_CONTEXT>
    ```
    ```bash
    $ sesearch -A -s <SOURCE_TYPE_CONTEXT> -t <TYPE_CONTEXT>
    ```
3. SELinux status (sestatus)
    ```bash
    $ sestatus
    ```
## Adjusting SELinux Policy with Booleans
### SELinux booleans
1. Get SELinux boolean (getsebool)
    ```bash
    $ getsebool -a
    ```
    ```bash
    $ getsebool <SELINUX_BOOLEAN>
    $ getsebool httpd_enable_homedirs
    ```
2. Set SELinux boolean (setsebool)
    ```bash
    $ setsebool <SELINUX_BOOLEAN> on
    $ setsebool httpd_enable_homedirs on
    ```
    ```bash
    $ setsebool <SELINUX_BOOLEAN> off
    $ setsebool httpd_enable_homedirs off
    ```
    ```bash
    $ setsebool -P <SELINUX_BOOLEAN> on
    ```
    ```bash
    $ setsebool -P <SELINUX_BOOLEAN> off
    ```
3. SELinux manage (semanage)
    ```bash
    $ semanage boolean -l
    ```
    ```bash
    $ semanage boolean -l -C
    ```
## Investigating and Resolving SELinux Issues
### Troubleshooting SELinux Issues
### Monitoring SELinux Violations
1. Security-enhanced linux (SELinux)  
    記錄所有作業系統操作細節的日誌存放在`/var/log/audit/audit.log`，關於SELinux的日誌會被setroubleshoot-server整理存放在`/var/log/messages`。
    ```bash
    $ tail /var/log/audit/audit.log
    ```
    ```bash
    $ tail /var/log/messages
    ```
2. `$ tail /var/log/messages`
    ```bash
    ...
    sealert -l 613ca624-248d-48a2-a7d9-d28f5bbe2763
    ...
    ```
3. SELinux alert (sealert)
    ```bash
    $ sealert -l 613ca624-248d-48a2-a7d9-d28f5bbe2763
    ```
    ```bash
    $ sealert -a /var/log/audit/audit.log
    ```
4. Audit log search (ausearch)
    ```bash
    $ ausearch -m AVC -ts recent
    ```
### Web Console
## Return to [RH134 Red Hat System Administration II](/rh134_red_hat_system_administration_ii/README.md)
