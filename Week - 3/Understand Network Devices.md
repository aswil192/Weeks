## 1. Routers

Connects **different networks** together and forward packets between them based on **IP addresses** (layer 3 of OSI)

#### Functions

- Path selection using routing tables
- **NAT** (Network Address Translation) — maps private IPs to public IPs
- Interconnects LANs, WANs, and the internet
- Often provides DHCP, DNS forwarding, and basic firewall features in home models

---
## 2. Switches

Connects devices **within the same network (LAN)** and forwards frames based on **MAC addresses** 

#### Functions

- Learns MAC address and builds a **CAM table**
- Forwards frames only to the correct port (unlike hub, which broadcast to all)
- VLANs - logically segment a network
- Layer 3 switches can also route between VLANs/subnets
- Spanning Tree Protocol (STP) prevents loops

---
## 3. Firewalls

Enforces security policy in traffic passing between networks - deciding what is **allowed or blocked**

#### Firewall types

- Packet-filtering: inspects headers (IP, port, protocol)
- Stateful: tracks connection states
- Next-generation Firewall (NGFW): adds application awareness, deep packet inspection, IPS integration

#### Functions

- ACLs / rule sets (allow / deny)
- NAT, VPN termination
- Zone-based segmentation 
- Logging and alerting

---
## 4. IDS (Intrusion Detection System)
