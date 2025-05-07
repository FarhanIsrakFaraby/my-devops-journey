# SSH Configuration Guide

## Setting Up SSH
1. Ensure **SSH** is installed on your local machine and server.  
   To install SSH, run the following commands:  
   ```bash
   sudo apt update
   sudo apt install openssh-server
   ```
2. **Verify your SSH service is running**:  
   Use the following command to check the status of the SSH service:  
   ```bash
   sudo systemctl status ssh
   ```
3. **Enable the SSH service** (if not already enabled):  
   This command will enable and start the SSH service immediately:  
   ```bash
   sudo systemctl enable --now ssh
   ```
4. **Generate an SSH key pair** on your local machine (if not already done):  
   Use the following command to create a secure SSH key pair:  
   ```bash
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```

---

## Logging into Your Server
- **For local servers**, use the following command, replacing `user` with your username and `192.x.x.x` with your server's IP address:  
  ```bash
  ssh user@192.x.x.x
  ```
- **For public servers**, use the following command, replacing `user` with your username and `<your-public-ip>` with your server's public IP address:  
  ```bash
  ssh user@<your-public-ip>
  ```

---

## Checking Your IP Address
- **On Ubuntu**, use the following command to display your IP address:  
  ```bash
  ip a
  ```
- **On macOS**, use the following command to display your IP address:  
  ```bash
  ifconfig
  ```

---

## Configuring Your Server's Network
Before using SSH, ensure your server's network is configured. Follow the instructions in [static-ip-config.md](static-ip-config.md) to set up your server's **netplan** for a static IP.

To check the status of your SSH service and verify if it is enabled, use:  
```bash
sudo systemctl status ssh.service
```
![SSH Service Status](<images/ssh status.png>)

---

## Changing the Default SSH Port
Changing the default SSH port can help prevent cyberattacks. Follow these steps:

1. **Backup your SSH configuration file** for safety:  
   Create a backup of the SSH configuration file to ensure you can restore it if needed:  
   ```bash
   sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config_backup
   ```
   After taking the backup, you can verify the file details:  
   ```bash
   ls -la /etc/ssh
   ```
   ![File Details](<images/ls -la.png>)

2. **Edit the SSH configuration file** to change the port:  
   Open the SSH configuration file in a text editor (e.g., `vim`) and modify the port number:  
   ```bash
   sudo vim /etc/ssh/sshd_config
   ```
   Ensure no other service is running on the same port.  
   ![Port Change](<images/port change.png>)

3. **Reconnect to the server using the new port**:  
   After changing the port, you cannot use the default SSH port to connect. Use the following command, replacing `<portnumber>` with the new port, `<username>` with your username, and `<ipaddress>` with your server's IP address:  
   ```bash
   ssh -p<portnumber> user@192.x.x.x
   ```
   ![SSH Login](<images/ssh login.png>)
