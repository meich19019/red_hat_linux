# 16 Analyzing Servers and Getting Support
## Analyzing and Managing Remote Servers
### Describing the Web Console
### Enabling the Web Console
1. Install web console
    ```bash
    $ yum install cockpit
    ```
    ```bash
    $ systemctl enable cockpit.socket --now
    ```
    ```bash
    $ firewall-cmd --add-service=cockpit --permanent
    ```
    ```bash
    $ firewall-cmd --reload
    ```
### Logging in to the Web Console
### Changing Password
### Troubleshooting with the web Console
### Managing System Services with the Web Console
## Getting Help From Red Hat Customer Portal
### Accessing Support Resources on the Red Hat Customer Portal
### Getting Oriented to the Customer Portal
### Searching the Knowledgebase with the Red Hat Support Tool
### Managing Support Cases with Red Hat Support Tool
### Joining Red Hat Developer
## Detecting and Resolving Issues with Red Hat Insights
### Introducing Red Hat Insights
### Installing Insights Clients
### Navigating the Insights Console
## Return to [RH124 Red Hat System Administration I](/rh124_red_hat_system_administration_i/README.md)
