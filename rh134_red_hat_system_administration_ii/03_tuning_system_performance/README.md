# 03 Tuning System Performance
## Adjusting Tuning Profiles
### Tuning Systems
### Installing and enabling tuned
1. Yellow dog updater, modified (yum)
    ```bash
    $ yum install tuned
    ```
2. System control (systemctl)
    ```bash
    $ systemctl enable tuned --now
    ```
### Selecting a Tuning Profile
### Managing profiles from the command line
1. Tune administrator (tuned-adm)
    ```bash
    $ tuned-adm active
    ```
    ```bash
    $ tuned-adm list
    ```
    ```bash
    $ tuned-adm profile <PROFILE>
    ```
    ```bash
    $ tuned-adm recommend
    ```
    ```bash
    $ tuned-adm off
    ```
### Managing Profiles with Web Console
## Influencing Process Scheduling
### Linux Process Scheduling and Multitasking
### Relative Priorities
### Setting Nice Levels and Permissions
### Reporting Nice Levels
### Starting Processes with Different Nice Levels
1. Nice (nice)
    ```bash
    nice <SCRIPT>
    ```
    ```bash
    nice -n <NICE_LEVEL> <SCRIPT>
    ```
### Changing the Nice Level of an Existing Process
1. Renice (renice)
    ```bash
    renice -n <NICE_LEVEL> <PID>
    ```
## Return to [RH134 Red Hat System Administration II](/rh134_red_hat_system_administration_ii/README.md)
