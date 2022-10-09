# Debian Linux General Commands
See: [[Linux General Commands]]

---
## Install Packages
```bash
sudo apt install <packagename>
```
  

**Example Packages**
- **openssh-server**: SSH server
- **tcpdump**: network tool to capture incoming and outgoing packets on an interface  
 
**Example Usage**
```bash
sudo apt install openssh-server
```

##### To Install SUDO
Login as *root* user or use su --login
```bash
apt install sudo
```
---
## Add a User to the sudo group
```bash
adduser <loginname> sudo
```
---
## Get Command Info
```bash
man <command>
```

**Example Usage**
```bash
man ip-address
```
---
## Download Content from Web
```bash
wget <url>
```

**Example Usage**
```bash
wget google.be
```