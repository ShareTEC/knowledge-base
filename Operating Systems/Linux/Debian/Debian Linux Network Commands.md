# Debian Linux Network Commands
See: [[Linux Network Commands]]

## Store IP Configuration
### Legacy way 'ifupdown'
1. Edit interfaces file. Set static IP-address and gateway

```bash
sudo nano /etc/network/interfaces
```

```text
iface <devicename> inet static
     address <ip address>
     gateway <gateway ip address>
```

**Example Usage**

```ini
# The primary network interface
allow-hotplug ens33
iface ens33 inet static
     address 192.168.11.10/24
     gateway 192.168.11.254
```

2. Use the `ifdown` and `ifup` commands to apply the changes. This will disable/enable the interface

```bash
ifdown <devicename>
```

```bash
ifup <devicename>
```

### Modern way 'networkd'
1. Create a "<2 digits preferably>-<name_of_your_choice>**.network**" config file in `/etc/systemd/network` (more info: `man systemd.network`)

```bash
sudo nano /etc/systemd/network/10-static.network
```

2. Add the name of the interfaces, static IP-address and gateway

```ini
[Match]
Name=ens33

[Network]
Address=192.168.11.10/24
Gateway=192.168.11.254
```

3. Apply the network config

```bash
sudo systemctl enable --now systemd-networkd
```

4. Reload the IP configuration after change

```bash
sudo networkctl reload
```

### Rename Network Interfaces
1. Create a "<2 digits preferably>-<name_of_your_choice>**.link**" config file in `/etc/systemd/network` (more info: `man systemd.link`)

```bash
sudo nano /etc/systemd/network/10-lan0.link
```

2. Add the original name of the interfaces, and define one or more alternative names

```ini
[Match]
OriginalName=ens33

[Link]
AlternativeName=lan0
AlternativeName=eth0
```

3. Apply after change

```bash
sudo systemctl restart systemd-udev-trigger.service
```

## List Network Interfaces

```bash
networkctl list
```

## Get Status of Network Interface (IP + Gateway)

```bash
networkctl status
```

## Check DNS Server

```bash
sudo nano /etc/resolv.conf
```

## Regenerate host keys

Host keys are located in `/etc/ssh/ssh_host_*`.
1. First remove the keys

```bash
sudo rm /etc/ssh/ssh_host_*
```

2. Regenerate the keys

```bash
sudo dpkg-reconfigure openssh-server
```

## Changing the hostname

```bash
sudo hostnamectl set-hostname "[NEWHOSTNAME]"
```

Don't forget to update the local `/etc/hosts` file

```
sudo nano /etc/hosts
```