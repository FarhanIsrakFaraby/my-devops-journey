# Install Ubuntu Server

To install **Ubuntu Server**, download it from the official website:  
[Download Ubuntu Server][ubuntuServerDownload]

[ubuntuServerDownload]: https://ubuntu.com/download/server


## Steps to Install Ubuntu Server

1. **Download the Ubuntu Server ISO**: [Download Ubuntu Server][ubuntuServerDownload].  
2. **Set it up on a virtual machine**: Use software like VirtualBox or VMware.  
3. **Follow the installation steps**: The installation wizard will guide you through the process.  
4. For a detailed guide, watch this [YouTube video][youtubeInstallationGuide].

[youtubeInstallationGuide]: https://www.youtube.com/watch?v=Hva8lsV2nTk

---

## Useful Commands

### Restart Your Server
To restart your server, use the following command:  
```bash
sudo init 6
```

to go to ur home directory 
cd ~

### Copy a File
To copy a file from one location to another, use:  
```bash
sudo cp /etc/<filename> /etc/<destination>
```

Replace `<filename>` with the name of the file you want to copy and `<destination>` with the target directory.

### Show File Details
To display detailed information about a file, use:  
```bash
ls -la <filename>
```

Replace `<filename>` with the name of the file you want to inspect.