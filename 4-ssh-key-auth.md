# SSH Key-Based Authentication

SSH key-based authentication can be explained using a real-life story about a **secure vault** and a **unique key**.

---

## The Vault and Key Story

Imagine you are the owner of a high-security vault (your server). You want to allow only trusted individuals (yourself or authorized users) to access the vault. Here's how it works:

1. **The Vault (Server)**:  
   The vault has a special lock installed that can only be opened by a unique key. This lock is your **public key**, and it is installed on the vault (server).

2. **The Key (Private Key)**:  
   You have a unique key that matches the lock on the vault. This key is your **private key**, and you keep it safe in your pocket. No one else has a copy of this key.

3. **Granting Access**:  
   If you want to allow someone else to access the vault, you give them a copy of the lock (public key) to install on their vault. However, you never share your private key.

4. **Accessing the Vault**:  
   When you approach the vault, you insert your private key into the lock. The vault verifies that the key matches the lock. If it does, the vault opens, granting you access.

---

## Managing SSH Keys on Your Local Machine

### Viewing Your SSH Folder
To navigate to your SSH folder on your local machine, use:
```bash
cd ~/.ssh/
```

### Listing Files in the SSH Folder
- On Ubuntu:
  ```bash
  ll
  ```
- On macOS:
  ```bash
  ls -l
  ```

### Returning to Your Home Directory
To return to your home directory, use:
```bash
cd ~
```

---

## Creating an SSH Key Pair
To generate a new SSH key pair, use:
```bash
ssh-keygen
```
This will create a private key (`id_rsa`) and a public key (`id_rsa.pub`) in your `~/.ssh` directory.

### Verifying the Generated Keys
After generating the keys, navigate to your SSH folder:
```bash
cd ~/.ssh
ll
```
Ensure you do not share your **private key** (`id_rsa`) with anyone.

---

## Adding the Public Key to a Remote Machine

### Manual Method
You can manually copy the contents of your public key (`id_rsa.pub`) and paste it into the `~/.ssh/authorized_keys` file on the remote machine.

### Using `ssh-copy-id`
To automate the process of adding your public key to the remote machine, use:
```bash
ssh-copy-id -p <port> user@192.x.x.x
```
Replace `<port>` with the SSH port number, `user` with your username, and `192.x.x.x` with the IP address of the remote machine.

---

## SSH Custom Configuration

Now you can call your server with a name instead of specifying the IP address or port number every time. This simplifies the process of connecting to your server.

### Steps to Create a Config File
1. Navigate to your SSH folder:
   ```bash
   cd ~/.ssh/
   ```

2. Create a `config` file:
   ```bash
   vim config
   ```

3. Add the following configuration to the file:
   ```plaintext
   Host my-server
     HostName <ip address>
     User <username>
     Port 2020
     IdentityFile ~/.ssh/id_rsa
   ```
   - Replace `<ip address>` with your server's IP address.  
   - Replace `<username>` with your username.  
   - Replace `2020` with your SSH port.  
   - Ensure the `IdentityFile` points to the correct private key file.

### Accessing the Server
Once the `config` file is set up, you can log in to your server using:
```bash
ssh my-server
```

This eliminates the need to specify the IP address, username, and port every time you connect.

---

By following these steps, you can securely set up and manage SSH key-based authentication while simplifying server access with a custom configuration.
