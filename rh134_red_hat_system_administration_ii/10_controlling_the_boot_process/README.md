# 10 Controlling the Boot Process
## Selecting the Boot Target
### Describing the Red Hat Enterprice Linux 8 Boot Process
### Rebooting and Shutting Down
1. System control (systemctl)
    ```bash
    $ systemctl poweroff
    ```
    ```bash
    $ systemctl reboot
    ```
### Selecting a Systemd Target
1. System control (systemctl)
    ```bash
    $ systemctl cat <TARGET>
    ...
    AllowIsolate=yes
    ...
    ```
    ```bash
    $ systemctl isolate <TARGET>
    $ systemctl isolate multi-user.target
    $ systemctl isolate graphical.target
    ```
    ```bash
    $ systemctl get-default
    ```
    ```bash
    $ systemctl set-default <TARGET>
    $ systemctl set-default multi-user.target
    $ systemctl set-default graphical.target
    ```
2. Selecting a different target at boot time
    1. Reboot the system
    2. Interrupt the boot loader countdown by pressing any key, except `Enter`
    3. Move the cursor to the kernel entry to boot
    4. Press `e` to edit the selected entry
    5. Move the cursor to the kernel command line (the line that starts with `linux`)
    6. Append `systemd.unit=<TARGET>.target`
    7. Press `Ctrl+x` to boot with the changes
## Resetting the Root Password
### Resetting the Root Password from the Boot Loader
1. Reboot the system
2. Interrupt the boot loader countdown by pressing any key, except `Enter`
3. Move the cursor to the kernel entry to boot
4. Press `e` to edit the selected entry
5. Move the cursor to the kernel command line (the line that starts with `linux`)
6. Append `rd.break`
7. Press `Ctrl+x` to boot with the changes
8. Remount `/sysroot` as read/write
    ```bash
    switch_root:/\# mount -o remount,rw /sysroot
    ```
9. Switch into a `chroot` jail, where `/sysroot` is treated as the root of the file-system tree
    ```bash
    switch_root:/\# chroot /sysroot
    ```
10. Set a new root password
    ```bash
    sh-4.4\# passwd
    ```
11. Make sure that all unlabeled files, including `/etc/shadow` at this point, get relabeled during boot
    ```bash
    sh-4.4\# touch /.autorelabel
    ```
12. Type `exit` twice
### Inspecting Logs
### Repairing Systemd Boot Issues
## Repairing File System Issues at Boot
### Diagnosing and Fixing File System Issues
## Return to [RH134 Red Hat System Administration II](/rh134_red_hat_system_administration_ii/README.md)
