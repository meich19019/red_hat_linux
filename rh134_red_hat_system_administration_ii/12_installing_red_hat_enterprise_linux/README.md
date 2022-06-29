# 12 Installing Red Hat Enterprise Linux
## Installing Red Hat Enterprise Linux
### Selecting Installation Media
### Installing Red Hat Enterprise Linux Manually
## Automating Installation with Kickstart
### Creating a Kickstart Profile
### Kickstart File commands
### Example Kickstart File
### Kickstart Installation Steps
### Creating a Kickstart File
### Publish the Kickstart File to Anaconda
### Boot Anaconda and Point it to the Kickstart File
## Installing and Configuring Virtual Machines
### Introducing KVM Virtualization
### Configuring a Red Hat Enterprise Linux Physical System as a Virtualization Host
1. Yellow dog updater, modified (yum)
    ```bash
    $ yum module list virt
    ```
    ```bash
    $ yum module install virt
    ```
    ```bash
    $ yum install virt-manager
    ```
2. Virtualization host validate (virt-host-validate)
    ```bash
    $ virt-host-validate
    ```
3. Virtual shell (virsh)
    ```bash
    $ virsh list
    ```
    ```bash
    $ virsh list --all
    ```
    ```bash
    $ virsh shutdown <VIRTUAL_MACHINE>
    ```
    ```bash
    $ virsh start <VIRTUAL_MACHINE>
    ```
    ```bash
    $ virsh reboot <VIRTUAL_MACHINE>
    ```
    ```bash
    $ virsh destroy <VIRTUAL_MACHINE>
    ```
    ```bash
    $ virsh dumpxml <VIRTUAL_MACHINE> <FILE>
    ```
    ```bash
    $ virsh define <FILE>
    ```
4. QEMU image (qemu-img)
    ```bash
    $ qemu-img create -f <IMAGE_TYPE> <IMAGE_NAME> <MAX_SIZE>
    $ qemu-img create -f qcow2 rhel8.qcow2 50G
    ```
    ```bash
    $ qemu-img info <IMAGE>
    $ qemu-img info rhel8.qcow2
    ```
    ```bash
    $ qemu-img resize <IMAGE> <MAX_SIZE>
    $ qemu-img resize rhel8.qcow2 100G
    ```
    ```bash
    $ qemu-img create -f <IMAGE_TYPE> -b <IMAGE> <IMAGE_NAME>
    $ qemu-img create -f qcow2 -b rhel8.qcow2 web.qcow2
    ```
    ```bash
    $ qemu-img convert -f <SOURCE_IMAGE_TYPE> -O <IMAGE_TYPE> <SOURCE_IMAGE> <IMAGE_NAME> 
    $ qemu-img convert -f qcow2 -O vmdk rhel8.qcow2 rhel8.vmdk
    $ qemu-img convert -f raw -O qcow2 /dev/sda rhel8.qcow2
    ```
### Managing Virtual Machines with Cockpit
## Return to [RH134 Red Hat System Administration II](/rh134_red_hat_system_administration_ii/README.md)
