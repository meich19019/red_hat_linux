# 10 Configuring and Securing SSH
## Accessing the Remote Command Line with SSH
### What is OpenSSH
1. OpenBSD Secure Shell (OpenSSH)  
    使用SSH透過計算機網路加密通訊的實現，OpenSSH主要設定存放在`/etc/ssh/sshd_config`。
### Secure Shell Examples
1. Secure Shell (SSH) 安全外殼協定  
    一種加密的網路傳輸協定，SSH通過在網路中建立安全隧道來實現SSH客戶端與伺服器之間的連接。
    ```bash
    $ ssh <REMOTE_USER>@<REMOTE_HOST> #透過SSH以使用者(<REMOTE_USER>)遠端登入系統(<REMOTE_HOST>)
    ```
    ```bash
    $ ssh <REMOTE_USER>@<REMOTE_HOST> <COMMAND>
    ```
### Identifying Remote Users
1. Who and What (w)
    ```bash
    $ w
    ```
### SSH host keys
1. SSH key scan (ssh-keyscan)
    ```bash
    $ ssh-keyscan <REMOTE_HOST>
    ```
    ```bash
    $ ssh-keyscan <REMOTE_HOST> >> /etc/ssh/ssh_known_hosts
    ```
## Configuring SSH Key-based Authentication
### SSH Key-based Authentication
1. SSH key generate (ssh-keygen)
    ```bash
    $ ssh-keygen
    ```
    ```bash
    $ ssh-keygen -t <TYPE>
    $ ssh-keygen -t rsa
    ```
    ```bash
    $ ssh-keygen -f <PUBLIC_KEY>
    ```
    ```bash
    $ ssh-keygen -l -f <PUBLIC_KEY>
    $ ssh-keygen -l -f /etc/ssh/ssh_host_ecdsa_key.pub
    ```
2. SSH copy id (ssh-copy-id)
    ```bash
    $ ssh-copy-id -i <PUBLIC_KEY> <REMOTE_USER>@<REMOTE_HOST>
    $ ssh-copy-id -i ~/.ssh/id_rsa.pub root@serverb
    ```
3. Secure Shell (SSH) 安全外殼協定
    ```bash
    $ ssh <REMOTE_USER>@<REMOTE_HOST> #透過SSH以使用者(<REMOTE_USER>)遠端登入系統(<REMOTE_HOST>)
    ```
    ```bash
    $ ssh -i <PUBLIC_KEY> <REMOTE_USER>@<REMOTE_HOST>
    $ ssh -i ~/.ssh/id_rsa.pub root@serverb
    ```
4. SSH agent (ssh-agent)
    ```bash
    $ ssh-agent
    ```
    ```bash
    $ eval $(ssh-agent)
    ```
5. SSH add (ssh-add)
    ```bash
    $ ssh-add
    ```
    ```bash
    $ ssh-add <PUBLIC_KEY>
    ```
## Customizing OpenSSH Service Configuration
### Configuring the OpenSSH Server
1. OpenBSD Secure Shell (OpenSSH)  
    使用SSH透過計算機網路加密通訊的實現，OpenSSH主要設定存放在`/etc/ssh/sshd_config`。
### Prohibit the Superuser From Logging in Using SSH
1. `/etc/ssh/sshd_config`
    ```bash
    PermitRootLogin yes
    ```
    ```bash
    PermitRootLogin no
    ```
    ```bash
    PermitRootLogin without-password
    ```
### Prohibiting Password-Based Authentication for SSH
1. `/etc/ssh/sshd_config`
    ```bash
    PasswordAuthentication yes
    ```
    ```bash
    PasswordAuthentication no
    ```
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
