## 🔧 Dynamic Routing Lab – RIP Configuration Summary

# 🖧 Network Topology

# <img width="604" alt="Screenshot 2025-05-25 142947" src="https://github.com/user-attachments/assets/93286cbd-0e5a-4161-936f-1b7d4931d0d5" />



# 🛠 Router Configurations

# 📍 Router1
interface GigabitEthernet0/0

ip address 198.168.2.3 255.255.255.0

no shutdown

interface GigabitEthernet0/1
 
 
ip address 198.168.1.2 255.255.255.0
 
no shutdown


router rip

version 2

network 198.168.1.0

network 198.168.2.0

no auto-summary


# 📍 Router2
interface GigabitEthernet0/0

 ip address 198.168.3.3 255.255.255.0

no shutdown

interface GigabitEthernet0/1

 ip address 198.168.1.4 255.255.255.0

no shutdown


router rip

 version 2
 
 network 198.168.1.0
 
 network 198.168.3.0
 
 no auto-summary

## 💻 PC Configurations

Device	   Interface	       IP Address	     Subnet Mask	    Default Gateway

PC0	       FastEthernet0	   198.168.2.7	   255.255.255.0	  198.168.2.3

PC1	       FastEthernet0	   198.168.2.9	   255.255.255.0	  198.168.2.3

## 🧠 Key RIP Configuration Notes
✅ RIP Version 2 is used – it supports subnetting and classless routing.

✅ no auto-summary prevents classful boundary summarization.

✅ 198.168.1.0/24 is the common link between R2 and R3, allowing RIP route exchange.

# ⚠️ Note
IP addressing like 198.168.x.x is non-standard (not reserved for private use). Consider using private IP ranges like:

192.168.0.0/16

172.16.0.0/12

10.0.0.0/8

For labs, it's fine, but in real networks use RFC1918 private IPs.
