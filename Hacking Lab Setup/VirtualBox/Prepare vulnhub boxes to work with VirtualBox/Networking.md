
---
Add your vulnhub box to VirtualBox

---

File
Tools
Network Manager
NAT Networks tab
Create
It will be called NatNetwork
Rename it to Vulnhub Network
IPv4 Prefix: `192.168.97.0/24`
Check "Enable DHCP"
Apply.

---
Kali Linux vm
Settings
Network
Adapter 1
Attached to: "NAT Network"
Name: "Vulnhub Network"
NOTE: You can only change these settings if the machine is turned off.

---

Vulnhub vm
Settings
Network
Attached to: "NAT Network"
Name: "Vulnhub Network"
