# Static IP Configuration Guide

To configure a static IP on Ubuntu, you need to set up Netplan.

## Steps to Configure
1. Open the Netplan configuration file:
   ```bash
   sudo vim /etc/netplan/50-cloud-init.yaml
   ```
   (Replace `/etc/netplan/50-cloud-init.yaml` with your desired filename if needed.)

2. Add the following configuration to the file:
```yaml
network:
   version: 2
   renderer: networkd
   ethernets:
      ens160:
         dhcp4: no
         addresses:
            - 192.168.30.77/24
         routes:
            - to: default
               via: 192.168.30.1
         nameservers:
            addresses:
               - 8.8.8.8
               - 8.8.4.4
```

3. Replace:
   - `ens33` with your Ethernet port name (use `ip a` to find it).
   - `192.168.10.245/24` with your desired static IP address.
   - `192.168.10.1` with your gateway address.

4. Apply the configuration:
   ```bash
   sudo netplan apply
   ```

5. Verify the network settings:
   ```bash
   ip a
   ```

Make sure to use your own IP addresses and Ethernet port names.

---

After completing the static IP configuration, you can now SSH into your server.  
For SSH instructions, refer to [ssh-config.md](ssh-config.md).
