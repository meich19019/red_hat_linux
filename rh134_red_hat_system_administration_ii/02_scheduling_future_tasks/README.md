# 02 Scheduling Future Tasks
## Scheduling a Deferred User Job
### Describing Deferred User Tasks
1. At (at)  
    單次排程內容存放在`/var/spool/at`。
    ```bash
    $ at <DATETIME>
    at> <SCRIPTS>
    Ctrl+D
    $ at now+1min
    at> date >> /tmp/job.txt
    Ctrl+D
    ```
    ```bash
    $ at <DATETIME> < <SCRIPTS_FILE>
    ```
    ```bash
    $ echo '<SCRIPTS>' | at <DATETIME>
    $ echo 'date >> /tmp/job.txt' | at now+5min
    ```
    ```bash
    $ at -c <JOB_NUMBER>
    ```
### Inspecting and Managing Deferred User Jobs
1. At query (atq)
    ```bash
    $ atq
    ```
2. At remove (atrm)
    ```bash
    $ atrm <JOB_NUMBER>
    ```
## Scheduling Recurring User Jobs
### Descrbing Recurring User Jobs
### Scheduling Recurring User Jobs
1. Command run on table (crontab)
    ```bash
    $ crontab -l
    ```
    ```bash
    $ crontab -r
    ```
    ```bash
    $ crontab -e
    ```
    ```bash
    $ crontab <FILE>
    ```
    ```bash
    $ crontab -u
    ```
### Describing User Job Format
## Scheduling Recurring System Jobs
### Describing Recurring System Jobs
1. Command run on table (crontab)  
    系統工作排程內容存放在`/etc/crontab`，預設載入`/etc/cron.d`目錄下檔案內容。
### Introducing Systemd Timer
## Managing Temporary Files
### Managing Temporary Files
## Return to [RH134 Red Hat System Administration II](/rh134_red_hat_system_administration_ii/README.md)
