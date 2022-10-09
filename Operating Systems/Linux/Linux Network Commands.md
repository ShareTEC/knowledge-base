# Linux Network Commands

## Get IP Information
```bash 
ip address show
```
---
## Get IP Route
```bash
ip route show
```
---
## Delete All Global IPv4 and IPv6 Addresses
```bash
sudo ip-address flush dev <devicename> scope global
```
---
## Add Static IP Address
```bash
sudo ip-address add <ip address> dev <devicename>
```

**Example Usage**
```bash
sudo ip-address add 192.168.11.10/24 dev eth1
```
---
## Delete Static IP Address
```bash
sudo ip-address delete <ip address> dev <devicename>
```

**Example Usage**
```bash
sudo ip-address delete 192.168.11.10/24 dev eth1
```
---
## Add Default Gateway
```bash
sudo ip-route add default via <ip address> dev <devicename>
```

**Example Usage**
```bash
sudo ip-route add default via 192.168.11.254 dev eth1
```

