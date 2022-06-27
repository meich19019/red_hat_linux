# 14 Installing and Updating Software Packages
## Registering Systems for Red Hat Support
### Red Hat Subscription Management
### Registration from the Command Line
### Entitlement cerificates
## Explaining and Investigating RPM Sodtware Packages
### Software packages and RPM
1. Redhat package manager (rpm)
    ```bash
    $ rpm -q <PACKAGE>
    ```
    ```bash
    $ rpm -qa
    ```
    ```bash
    $ rpm -qf <FILE>
    ```
    ```bash
    $ rpm -qi <PACKAGE>
    ```
    ```bash
    $ rpm -ql <PACKAGE>
    ```
    ```bash
    $ rpm -qc <PACKAGE>
    ```
    ```bash
    $ rpm -qd <PACKAGE>
    ```
    ```bash
    $ rpm -q --scripts <PACKAGE>
    ```
    ```bash
    $ rpm -q --changelog <PACKAGE>
    ```
2. `$ rpm -qa`
    ```bash
    coreutils-8.30-4.el8.x86_64.rpm
    1         2    3 4   5
    ```
    1. 名稱
    2. 版本
    3. 發行次數
    4. 發行作業系統
    5. 發行處理器架構
3. Scripts
    1. Preinstall scriptlet  
        開始安裝之前被執行。
    2. Postinstall scriptlet  
        安裝完成之後被執行。
    3. preuninstall scriptlet  
        套件移除之前被執行。
    4. posttrans scriptlet  
        套件移除之後被執行。
### Installing RPM Packages
1. Redhat package manager (rpm)
    ```bash
    $ rpm -i <PACKAGE>
    ```
    ```bash
    $ rpm -iv <PACKAGE>
    ```
    ```bash
    $ rpm -ivh <PACKAGE>
    ```
2. Extract files from an rpm package file
    ```bash
    $ rpm2cpio <PACKAGE_FILE> | cpio -id
    ```
    ```bash
    $ rpm2cpio <PACKAGE_FILE> | cpio -tv
    ```
### Summary of RPM Query Commands
1. Redhat package manager (rpm)
    ```bash
    $ rpm --import <PUBLIC_KEY>
    $ rpm --import RPM-GPG-KEY-redhat-release
    ```
    ```bash
    $ rpm -K <PACKAGE_FILE>
    $ rpm -K zip-3.0-2.3.el8.x86_64.rpm
    ```
## Installing and Updating Software Packages with Yum
### Managing Software Package with Yum
1. Yellow dog updater, modified (yum)
    ```bash
    $ yum help
    ```
    ```bash
    $ yum list
    ```
    ```bash
    $ yum list <PACKAGE>
    ```
    ```bash
    $ yum search <NAME|SUMMARY>
    ```
    ```bash
    $ yum search all <NAME|SUMMARY|DESCRIPTION>
    ```
    ```bash
    $ yum info <PACKAGE>
    ```
    ```bash
    $ yum provides <PACKAGE>
    ```
    ```bash
    $ yum install <PACKAGE>
    ```
    ```bash
    $ yum update
    ```
    ```bash
    $ yum update <PACKAGE>
    ```
    ```bash
    $ yum remove <PACKAGE>
    ```
    ```bash
    $ yum group list
    ```
    ```bash
    $ yum group list hidden
    ```
    ```bash
    $ yum group info <GROUP_PACKAGE>
    ```
    ```bash
    $ yum group install <GROUP_PACKAGE>
    ```
    ```bash
    $ yum group remove <GROUP_PACKAGE>
    ```
    ```bash
    $ yum history
    ```
    ```bash
    $ yum history <HISTORY_ID>
    ```
    ```bash
    $ yum history undo <HISTORY_ID>
    ```
2. Unix name (uname)
    ```bash
    $ uname -r
    ```
    ```bash
    $ uname -a
    ```
## Enabling Yum Software Repositories
### Enabling Red Hat software repositories
1. Yellow dog updater, modified (yum)  
    套件庫資料存放在`/etc/yum.repos.d`目錄下檔案內容。
    ```bash
    $ yum repolist all
    ```
    ```bash
    $ yum config-manager --enable <REPOSITORY_ID>
    ```
    ```bash
    $ yum config-manager --disable <REPOSITORY_ID>
    ```
    ```bash
    $ yum config-manager --add-repo <REPOSITORY>
    $ yum config-manager --add-repo "https://dl.fedoraproject.org/pub/epel/8/Everything/x86_64/"
    ```
2. `$ cat /etc/yum.repos.d/epel.repo`
    ```bash
    [EPEL] #套件庫名稱
    name=EPEL 8 #套件庫註解
    baseurl=https://dl.fedoraproject.org/pub/epel/8/Everything/x86_64/ #套件庫位置
    enabled=1 #套件庫啟用
    gpgcheck=1 #套件庫數位簽章檢查
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-8 #套件庫數位簽章金鑰位置
    ```
3. Redhat package manager (rpm)
    ```bash
    $ rpm --import <PUBLIC_KEY>
    $ rpm --import "https://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-8"
    ```
## Managing Package Module Streams
### Introduction to Application Stream
1. Main software repositories
    1. BaseOS
    2. Application Stream
### Modules
1. Yellow dog updater, modified (yum)
    ```bash
    $ yum module list
    ```
    ```bash
    $ yum module list <PACKAGE>
    ```
    ```bash
    $ yum module info <PACKAGE>
    ```
    ```bash
    $ yum module info --profile <PACKAGE>
    ```
    ```bash
    $ yum module install <PACKAGE>
    $ yum install @<PACKAGE>
    $ yum module install perl
    $ yum install @perl
    ```
    ```bash
    $ yum module install <PACKAGE>:<STREAM>/<PROFILE>
    $ yum module install perl:5.26/common
    ```
    ```bash
    $ yum module disable <PACKAGE>
    ```
    ```bash
    $ yum module enable <PACKAGE>
    ```
    ```bash
    $ yum module remove <PACKAGE>
    ```
    ```bash
    $ yum module reset <PACKAGE>
    ```
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
