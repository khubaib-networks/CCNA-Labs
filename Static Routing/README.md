## 📚 Static Routing Lab

This lab demonstrates **Static Routing** in a multi-router, multi-VLAN topology using Cisco Packet Tracer.



### 🏗️ Topology Overview

![Static Routing Topology](Static%20Routing%20lab.png)



### 🌐 IP Addressing Scheme

| Router   | Interface | IP Address    | Subnet Mask      |
|----------|-----------|---------------|------------------|
| Router1  | Gig0/0    | 10.0.0.1      | 255.255.255.0    |
| Router1  | Gig0/1    | 11.0.0.1      | 255.255.255.0    |
| Router2  | Gig0/0    | 12.0.0.1      | 255.255.255.0    |
| Router2  | Gig0/1    | 11.0.0.2      | 255.255.255.0    |
| Router2  | Gig0/2    | 13.0.0.1      | 255.255.255.0    |
| Router3  | Gig0/0    | 14.0.0.1      | 255.255.255.0    |
| Router3  | Gig0/1    | 13.0.0.2      | 255.255.255.0    |
| Router3  | Gig0/2    | 15.0.0.1      | 255.255.255.0    |
| Router4  | Gig0/0    | 16.0.0.1      | 255.255.255.0    |
| Router4  | Gig0/1    | 15.0.0.2      | 255.255.255.0    |
| Router4  | Gig0/2    | 17.0.0.1      | 255.255.255.0    |
| Router5  | Gig0/0    | 18.0.0.1      | 255.255.255.0    |
| Router5  | Gig0/1    | 17.0.0.2      | 255.255.255.0    |

PCs are assigned in corresponding subnets:
- **10.0.0.0/24**
- **12.0.0.0/24**
- **14.0.0.0/24**
- **16.0.0.0/24**
- **18.0.0.0/24**

---

### 🔧 Static Route Configuration

Here’s an example of **static route configuration** on each router:

# Router1


hostname Router1

interface Gig0/0

 ip address 10.0.0.1 255.255.255.0
 
 no shutdown

!

interface Gig0/1

 ip address 11.0.0.1 255.255.255.0
 
 no shutdown
!

ip route 12.0.0.0 255.255.255.0 11.0.0.2

ip route 14.0.0.0 255.255.255.0 11.0.0.2

ip route 16.0.0.0 255.255.255.0 11.0.0.2

ip route 18.0.0.0 255.255.255.0 11.0.0.2


#### Router2

hostname Router2

interface Gig0/0

 ip address 12.0.0.1 255.255.255.0
 
 no shutdown
!


interface Gig0/1

 ip address 11.0.0.2 255.255.255.0
 
 no shutdown
!


interface Gig0/2

 ip address 13.0.0.1 255.255.255.0
 
 no shutdown
!


ip route 10.0.0.0 255.255.255.0 11.0.0.1

ip route 14.0.0.0 255.255.255.0 13.0.0.2

ip route 16.0.0.0 255.255.255.0 13.0.0.2

ip route 18.0.0.0 255.255.255.0 13.0.0.2





#### Router3





hostname Router3

interface Gig0/0

 ip address 14.0.0.1 255.255.255.0
 
 no shutdown
!


interface Gig0/1

 ip address 13.0.0.2 255.255.255.0
 
 no shutdown
!


interface Gig0/2

 ip address 15.0.0.1 255.255.255.0
 
 no shutdown
!


ip route 10.0.0.0 255.255.255.0 13.0.0.1

ip route 12.0.0.0 255.255.255.0 13.0.0.1

ip route 16.0.0.0 255.255.255.0 15.0.0.2

ip route 18.0.0.0 255.255.255.0 15.0.0.2





#### Router4





hostname Router4

interface Gig0/0

 ip address 16.0.0.1 255.255.255.0
 
 no shutdown
!


interface Gig0/1

 ip address 15.0.0.2 255.255.255.0
 
 no shutdown
!


interface Gig0/2

 ip address 17.0.0.1 255.255.255.0
 
 no shutdown
!


ip route 10.0.0.0 255.255.255.0 15.0.0.1

ip route 12.0.0.0 255.255.255.0 15.0.0.1

ip route 14.0.0.0 255.255.255.0 15.0.0.1

ip route 18.0.0.0 255.255.255.0 17.0.0.2





#### Router5





hostname Router5


interface Gig0/0

 ip address 18.0.0.1 255.255.255.0
 
 no shutdown
!


interface Gig0/1

 ip address 17.0.0.2 255.255.255.0
 
 no shutdown
!


ip route 10.0.0.0 255.255.255.0 17.0.0.1

ip route 12.0.0.0 255.255.255.0 17.0.0.1

ip route 14.0.0.0 255.255.255.0 17.0.0.1

ip route 16.0.0.0 255.255.255.0 17.0.0.1


# 🚀 How to Use This Lab

1. Clone this repository:

  
   git clone  👉 https://lnkd.in/dYbuSBrT
   
2. Open the `StaticRouting.pkt` file in **Cisco Packet Tracer**.
3. Review the static route configurations.
4. Test connectivity by pinging across the network.
5. Reference the topology image `Static Routing lab.png` for guidance.



### 📸 Topology Screenshot

![Static Routing Topology]![Static Routing lab](https://github.com/user-attachments/assets/076504ac-0e72-4b63-9899-d53d1e30fe3e)




### 📚 Learning Outcomes

* Configure and verify **Static Routes** across multiple routers
* Understand routing across **multiple subnets**
* Build hands-on skills for the **CCNA Certification**
* Improve troubleshooting and logical thinking for complex topologies



### 📬 Contribute

Want to improve this lab or add new ones? Feel free to open a Pull Request or share feedback!



### 🌟 Stay Connected

This repository is a growing collection of labs—perfect for CCNA students and those looking to impress recruiters with practical networking skills!



