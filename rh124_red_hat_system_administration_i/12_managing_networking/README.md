# 12 Managing Networking
## Describing Networking Concepts
### TCP/IP Network Model
### Describing Network Interface Names
### IPv4 Networking
### IPv6 Networking
### Host Names and IP Addresses
## Validating Network Configuration
### Gathering Network Interface Information
1. IP (ip)
    ```bash
    $ ip link show
    ```
    ```bash
    $ ip link show dev <NETWORK_INTERFACE>
    $ ip link show dev eth0
    ```
    ```bash
    $ ip -s link show
    ```
    ```bash
    $ ip link set dev <NETWORK_INTERFACE> down
    ```
    ```bash
    $ ip link set dev <NETWORK_INTERFACE> up
    ```
    ```bash
    $ ip address show
    ```
    ```bash
    $ ip address show dev <NETWORK_INTERFACE>
    ```
    ```bash
    $ ip address add <IPV4_ADDRESS>/<IPV4_SUBNET_MASK> dev <NETWORK_INTERFACE>
    $ ip address add 192.168.1.100/24 dev eth0
    ```
### Checking Connectivity Between Hosts
1. Ping (ping)
    ```bash
    $ ping <IPV4_ADDRESS>
    ```
    ```bash
    $ ping -c <COUNT> <IPV4_ADDRESS>
    ```
2. Ping ipv6 (ping6)
    ```bash
    $ ping6 <IPV6_ADDRESS>
    ```
    ```bash
    $ ping6 <IPV6_ADDRESS>%<NETWORK_INTERFACE>
    ```
    ```bash
    $ ping6 -c <COUNT> <IPV6_ADDRESS>
    ```
### Troubleshooting Routing
1. IP (ip)
    ```bash
    $ ip route
    $ ip route show
    ```
    ```bash
    $ ip route add <IPV4_ADDRESS>/<IPV4_SUBNET_MASK> via <IPV4_GATEWAY>
    $ ip route del 192.168.1.100/24 via 192.168.1.1
    $ ip route add default via 192.168.1.1
    ```
    ```bash
    $ ip route del <IPV4_ADDRESS>/<IPV4_SUBNET_MASK>
    $ ip route del 192.168.1.100/24
    $ ip route del default
    ```
    ```bash
    $ ip -6 route
    $ ip -6 route show
    ```
2. Traceroute (traceroute)
    ```bash
    $ traceroute <IPV4_ADDRESS>
    ```
    ```bash
    $ traceroute -6 <IPV6_ADDRESS>
    ```
3. Tracepath (tracepath)
    ```bash
    $ tracepath <IPV4_ADDRESS>
    ```
4. Tracepath ipv6 (tracepath6)
    ```bash
    $ tracepath6 <IPV6_ADDRESS>
    ```
5. My traceroute (mtr)
    ```bash
    $ mtr <IPV4_ADDRESS>
    ```
### Troubleshooting ports and services
1. Socket statistics (ss)
    ```bash
    $ ss
    ```
    ```bash
    $ ss -ta
    ```
2. Network statistics (netstat)
    ```bash
    $ netstat
    ```
    ```bash
    $ netstat -ta
    ```
## Configuring Networking from the Command Line
### Describing NetworkManager Concepts
1. NetworkManager  
    網路設定存放在`/etc/sysconfig/network-scripts`目錄下檔案內容。
    1. Device
    2. Connection
### Viewing Networking Information
1. NetworkManager command-line interface (nmcli)
    ```bash
    $ nmcli device status
    ```
    ```bash
    $ nmcli connection show
    ```
    ```bash
    $ nmcli connection show --active
    ```
### Adding a network connection
1. NetworkManager command-line interface (nmcli)
    ```bash
    $ nmcli connection add con-name <CONNECTION_NAME> type <TYPE> ifname <NETWORK_INTERFACE>
    $ nmcli connection add con-name "Wired connection 1" type ethernet ifname eth0
    ```
    ```bash
    $ nmcli connection add con-name <CONNECTION_NAME> type <TYPE> ifname <NETWORK_INTERFACE> ipv4.method <IPV4_METHOD> ipv4.address <IPV4_ADDRESS>/<IPV4_SUBNET_MASK> ipv4.gateway <IPV4_GATEWAY>
    $ nmcli connection add con-name "Wired connection 1" type ethernet ifname eth0 ipv4.method manual ipv4.address 192.168.1.100/24 ipv4.gateway 192.168.1.1
    ```
    ```bash
    $ nmcli connection add con-name <CONNECTION_NAME> type <TYPE> ifname <NETWORK_INTERFACE> ipv6.method <IPV6_METHOD> ipv6.address <IPV6_ADDRESS>/<IPV6_SUBNET_MASK> ipv6.gateway <IPV6_GATEWAY> ipv4.method <IPV4_METHOD> ipv4.address <IPV4_ADDRESS>/<IPV4_SUBNET_MASK> ipv4.gateway <IPV4_GATEWAY>
    $ nmcli connection add con-name "Wired connection 1" type ethernet ifname eth0 ipv6.method manual ipv6.address 2001:db8:0:1::c000:207/64 ipv6.gateway 2001:db8:0:1::1 ipv4.method manual ipv4.address 192.168.1.100/24 ipv4.gateway 192.168.1.1
    ```
### Controlling network connections
1. NetworkManager command-line interface (nmcli)
    ```bash
    $ nmcli connection down <CONNECTION_NAME>
    $ nmcli connection down "Wired connection 1"
    ```
    ```bash
    $ nmcli connection up <CONNECTION_NAME>
    $ nmcli connection up "Wired connection 1"
    ```
    ```bash
    $ nmcli device disconnect <NETWORK_INTERFACE>
    $ nmcli device disconnect eth0
    ```
### Modifying Network Connection Settings
1. NetworkManager  
    網路設定存放在`/etc/sysconfig/network-scripts`目錄下檔案內容。
2. NetworkManager command-line interface (nmcli)
    ```bash
    $ nmcli connection show <CONNECTION_NAME>
    $ nmcli connection show "Wired connection 1"
    ```
    ```bash
    $ nmcli connection modify <CONNECTION_NAME> ipv4.address <IPV4_ADDRESS>/<IPV4_SUBNET_MASK> ipv4.gateway <IPV4_GATEWAY>
    $ nmcli connection modify "Wired connection 1" ipv4.address 192.168.1.100/24 ipv4.gateway 192.168.1.1
    ```
    ```bash
    $ nmcli connection modify <CONNECTION_NAME> ipv6.address <IPV6_ADDRESS>/<IPV6_SUBNET_MASK> ipv6.gateway <IPV6_GATEWAY>
    $ nmcli connection modify "Wired connection 1" ipv6.address 2001:db8:0:1::c000:207/64 ipv6.gateway 2001:db8:0:1::1
    ```
    ```bash
    $ nmcli connection modify <CONNECTION_NAME> +ipv4.dns <IPV4_DNS>
    $ nmcli connection modify "Wired connection 1" +ipv4.dns 8.8.8.8
    ```
### Deleting a network connection
1. NetworkManager command-line interface (nmcli)
    ```bash
    $ nmcli connection delete <CONNECTION_NAME>
    $ nmcli connection delete "Wired connection 1"
    ```
### Who Can Modify Network Settings?
1. NetworkManager command-line interface (nmcli)
    ```bash
    $ nmcli general permissions
    ```
### Summary of Commands
## Editing Network Configuration Filees
### Describing Connection Configuration Files
1. NetworkManager  
    網路設定存放在`/etc/sysconfig/network-scripts`目錄下檔案內容。
2. NetworkManager command-line interface (nmcli)
    ```bash
    $ nmcli connection reload
    ```
### Modifying network configuration
1. NetworkManager command-line interface (nmcli)
    ```bash
    $ nmcli connection reload
    ```
    ```bash
    $ nmcli connection down <CONNECTION_NAME>
    $ nmcli connection down "Wired connection 1"
    ```
    ```bash
    $ nmcli connection up <CONNECTION_NAME>
    $ nmcli connection up "Wired connection 1"
    ```
## Configuring Host Names and Name Resolution
### Changing the system host name
1. Hostname (hostname)  
    主機名稱存放在`/etc/hostname`。
    ```bash
    $ hostname #查看完整主機名稱
    ```
    ```bash
    $ hostname -s #查看簡短主機名稱
    ```
2. Hostname control (hostnamectl)
    ```bash
    $ hostnamectl status
    ```
    ```bash
    $ hostnamectl set-hostname <HOSTNAME>
    ```
### Configuring name resolution
1. Local hosts  
    本地主機資料存放在`/etc/hosts`。
1. Domain information groper (dig)
    ```bash
    $ dig
    ```
2. Host (host)
    ```bash
    $ host <HOSTNAME>
    ```
    ```bash
    $ host <IPV4_ADDRESS>
    ```
3. Name server lookup (nslookup)
    ```bash
    $ nslookup
    ```
4. Get entries from administrative database (getent)
    ```bash
    $ getent hosts <HOSTNAME>
    ```
5. NetworkManager command-line interface (nmcli)  
    名稱伺服器資料存放在`/etc/resolv.conf`。
    ```bash
    $ nmcli connection modify <CONNECTION_NAME> ipv4.dns <IPV4_DNS>
    $ nmcli connection modify "Wired connection 1" ipv4.dns 8.8.8.8
    ```
    ```bash
    $ nmcli connection modify <CONNECTION_NAME> +ipv4.dns <IPV4_DNS>
    $ nmcli connection modify "Wired connection 1" +ipv4.dns 8.8.8.8
    ```
    ```bash
    $ nmcli connection modify <CONNECTION_NAME> +ipv6.dns <IPV6_DNS>
    $ nmcli connection modify "Wired connection 1" +ipv6.dns 2001:4860:4860::8888
    ```
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
