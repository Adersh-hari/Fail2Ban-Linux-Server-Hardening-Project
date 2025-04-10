# Fail2Ban-Linux-Server-Hardening-Project

## Introduction
This project demonstrates how to install and configure Fail2Ban on a Linux server to secure SSH against brute-force attacks. Fail2Ban scans log files for intrusion attempts and blocks IP addresses that have too many failed login attempts.

## Steps to Secure the Server:

### Step 1: Update the System
Make sure your system is up to date. Run the following command to update and upgrade your system packages:

'''bash


sudo apt update && sudo apt upgrade -y

### Step 2: Install Fail2Ban

Install Fail2Ban by running the following command:
bash


sudo apt install fail2ban -y

### Step 3: Configure Fail2Ban

Once Fail2Ban is installed, we need to configure it. Open the Fail2Ban configuration file jail.local:

Bash


sudo nano /etc/fail2ban/jail.local

Add the following configuration to protect the SSH service:
lni


[sshd]
enabled = true
port    = ssh
logpath = /var/log/auth.log
maxretry = 3
bantime = 600
findtime = 600

### Step 4: Restart Fail2Ban Service

To apply the new configuration, restart the Fail2Ban service with:
Bash


sudo systemctl restart fail2ban

### Step 5: Verify Fail2Ban Status

Check if the Fail2Ban service is running properly:
Bash


sudo systemctl status fail2ban

You should see the status of Fail2Ban as active, indicating that it's running correctly.

### Step 6: Check Fail2Ban Logs

To verify that Fail2Ban is successfully protecting your SSH service, use the following command:

sudo fail2ban-client status sshd

This command should show the status of your SSH protection, including the number of IPs that are currently banned.

### Step 7: Configuration File Upload

I have included the Fail2Ban configuration file as part of this repository. You can find the configuration file here:

(fail2ban-jail-local.txt)[https://github.com/Adersh-hari/Fail2Ban-Linux-Server-Hardening-Project/blob/main/fail2ban-jail-local.txt]


## Conclusion

This project demonstrates the installation and configuration of Fail2Ban on a Linux server to secure SSH from brute-force attacks. The configuration used in this project can be adapted to secure other services and can help improve server security.
