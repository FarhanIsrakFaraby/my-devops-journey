# SSH Configuration Guide

## Setting Up SSH
1. Ensure SSH is installed on your local machine and server.
2. Generate an SSH key pair on your local machine (if not already done):
   ```bash
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```

## Logging into Your Server
- For local servers, use:
  ```bash
  ssh user@192.x.x.x
  ```
- For public servers, use:
  ```bash
  ssh user@<your-public-ip>
  ```

## Checking Your IP Address
- On Ubuntu, use:
  ```bash
  ip a
  ```
- On macOS, use:
  ```bash
  ifconfig
  ```

## Configuring Your Server's Network
Before using SSH, ensure your server's network is configured. Follow the instructions in [static-ip-config.md](static-ip-config.md) to set up your server's netplan for a static IP.
