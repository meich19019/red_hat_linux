# 11 Analyzing and Storing Logs
## Describing System Log Architecture
### System Logging
1. Syslog
    1. `/var/log/messages`
    2. `/var/log/secure`
    3. `/var/log/maillog`
    4. `/var/log/cron`
    5. `/var/log/boot.log`
## Reviewing Syslog Files
### Logging Events to the System
1. Syslog priorities
### Sample Rules of Rsyslog
1. Rocket-fast system for log (rsyslog)  
    此設定存放在`/etc/rsyslog.conf`，預設載入`/etc/rsyslog.d`目錄下檔案設定內容。
2. `/etc/rsyslog.conf`
    ```bash
    *.info;mail.none;authpriv.none;cron.none    /var/log/messages
    123   4                                     5
    ```
    1. 類型
    2. 連結符號
        1. .
        2. .=
        3. .=!
    3. 記錄等級
    4. 邏輯運算子
        1. ;
        2. ,
    5. 處理方式
### Log File Rotation
1. Log rotate (logrotate)  
    此設定存放在`/etc/logrotate.conf`，預設載入`/etc/logrotate.d`目錄下檔案設定內容。
2. `/etc/logrotate.conf`
    ```bash
    weekly
    ```
    ```bash
    rotate 4
    ```
### Analyzing a Syslog Entry
1. `/var/log/messages`
    ```bash
    Jun 26 05:41:08 workstation systemd[1]: Started dnf makecache.
    1               2           3           4
    ```
    1. Log記錄的時間
    2. 記錄的主機
    3. 記錄的程序
    4. 記錄的Log內容
### Monitoring Logs
3. Tail (tail)
    ```bash
    $ tail <FILE> #查看檔案(<FILE>)內容後10行
    ```
    ```bash
    $ tail -n <NUMBER> <FILE> #查看檔案(<FILE>)內容後(<NUMBER>)行
    ```
    ```bash
    $ tail -f <FILE> #持續查看檔案(<FILE>)內容後10行
    ```
### Sending Syslog Messages Manually
1. Logger (logger)
    ```bash
    $ logger <MESSAGE>
    ```
    ```bash
    $ logger -p <PRIORITY> <MESSAGE>
    $ logger -p user.notice "Hello World!"
    ```
## Reviewing System Journal Entries
### Finding Events
1. Journal control (journalctl)
    ```bash
    $ journalctl
    ```
    ```bash
    $ journalctl -n <NUMBER>
    ```
    ```bash
    $ journalctl -f
    ```
    ```bash
    $ journalctl -p <PRIORITY>
    $ journalctl -p err
    ```
    ```bash
    $ journalctl --since <DATETIME>
    ```
    ```bash
    $ journalctl --until <DATETIME>
    ```
    ```bash
    $ journalctl -o <OUTPUT_FORMAT>
    $ journalctl -o verbose
    ```
    ```bash
    $ journalctl _SYSTEMD_UNIT=<UNIT_NAME>.<UNIT_TYPE>
    ```
    ```bash
    $ journalctl _PID=<PID>
    ```
## Preserving the System Journal
### Storing the System Journal Permanently
1. System journal (systemd-journald)  
    此設定存放在`/etc/systemd/journald.conf`。
2. `/etc/systemd/journald.conf`
    ```bash
    Storage=persistent
    ```
    ```bash
    Storage=volatile
    ```
    ```bash 
    Storage=auto
    ```
    ```bash
    Storage=none
    ```
3. Journal control (journalctl)
    ```bash
    $ journalctl -b
    ```
    ```bash
    $ journalctl -b <BOOT_ID>
    ```
## Maintaining Accurate Time
### Setting Local Clocks and Time Zones
1. Network time protocol (NTP)
2. Time date control (timedatectl)
    ```bash
    $ timedatectl
    ```
    ```bash
    $ timedatectl list-timezones
    ```
    ```bash
    $ timedatectl set-timezone <TIME_ZONE>
    ```
    ```bash
    $ timedatectl set-time <DATETIME>
    ```
    ```bash
    $ timedatectl set-ntp true
    ```
3. Timezone select (tzselect)
    ```bash
    $ tzselect
    ```
### Configuring and Monitoring Chronyd
1. Chrony (chronyd)
    此設定存放在`/etc/chrony.conf`。
2. `/etc/chrony.conf`
    ```bash
    server classroom.example.com iburst
    ```
3. Chrony command-line (chronyc)
    ```bash
    $ chronyc sources -v
    ```
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
