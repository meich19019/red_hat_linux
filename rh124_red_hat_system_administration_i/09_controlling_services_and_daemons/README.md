# 09 Controlling Services and Daemons
## Identifying Automatically Started System Processes
### Introduction to systemd
1. Systemd 
### Describing Service Units
1. Unit types
    1. Service
    2. Socket
    3. Path
### Listing Service Units
1. System control (systemctl)
    ```bash
    $ systemctl -t help
    ```
    ```bash
    $ systemctl
    $ systemctl list-units
    ```
    ```bash
    $ systemctl list-units --type=<UNIT_TYPE>
    ```
    ```bash
    $ systemctl list-units --state=<STATE>
    ```
    ```bash
    $ systemctl list-units --all
    ```
    ```bash
    $ systemctl list-unit-files
    ```
    ```bash
    $ systemctl list-unit-files --type=<UNIT_TYPE>
    ```
### Viewing Service States
1. System control (systemctl)
    ```bash
    $ systemctl status <UNIT_NAME>.<UNIT_TYPE>
    ```
    ```bash
    $ systemctl is-active <UNIT_NAME>
    ```
    ```bash
    $ systemctl is-enabled <UNIT_NAME>
    ```
    ```bash
    $ systemctl is-failed <UNIT_NAME>
    ```
## Controlling System Services
### Starting and Stopping Services
1. System control (systemctl)
    ```bash
    $ systemctl start <UNIT_NAME>.<UNIT_TYPE>
    ```
    ```bash
    $ systemctl stop <UNIT_NAME>.<UNIT_TYPE>
    ```
### Restarting and Reloading Services
1. System control (systemctl)
    ```bash
    $ systemctl restart <UNIT_NAME>.<UNIT_TYPE>
    ```
    ```bash
    $ systemctl reload <UNIT_NAME>.<UNIT_TYPE>
    ```
    ```bash
    $ systemctl reload-or-restart <UNIT_NAME>.<UNIT_TYPE>
    ```
### Listing Unit Dependencies
1. System control (systemctl)
    ```bash
    $ systemctl list-dependencies <UNIT_NAME>.<UNIT_TYPE>
    ```
### Masking and Unmasking Services
1. System control (systemctl)
    ```bash
    $ systemctl mask <UNIT_NAME>.<UNIT_TYPE>
    ```
    ```bash
    $ systemctl unmask <UNIT_NAME>.<UNIT_TYPE>
    ```
### Enabling Services to Start or Stop at Boot
1. System control (systemctl)
    ```bash
    $ systemctl enable <UNIT_NAME>.<UNIT_TYPE>
    ```
    ```bash
    $ systemctl enable <UNIT_NAME>.<UNIT_TYPE> --now
    ```
    ```bash
    $ systemctl disable <UNIT_NAME>.<UNIT_TYPE>
    ```
### Summary of systemctl Commands
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
