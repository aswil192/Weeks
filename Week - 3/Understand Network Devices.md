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

Monitors network traffic for malicious activity and alerts - it is passive (detection only, does not block)

#### Detection methods

- Signature based: matches known attack patterns
- Anomaly based: flags deviations from normal behaviour

#### Deployment

- NIDS: network-based (sensor on a SPAN/mirror port)
- HIDS: host-based (agent on a server)

>An IDS sees and reports but does not stop the attack.

---
## 4. IPS (Intrusion Prevention System)

Like an IDS, but inline in the traffic path - it can block or drop malicious traffic in the real time. 

#### Functions:

- Signature and anomaly detection (same engine family as IDS)
- Active response: drop packets, packets, reset connections, block source IPs
- Often integrated into NGFWs (IPS module)

>An IPS prevents; an IDS only detects. Trade-offs: IPS can cause false-positive blocking and adds latency.

---
## Reference

- [Youtube - Router](https://youtu.be/p9ScLm9S3B4)
- [Youtube - Switch](https://youtu.be/9eH16Fxeb9o)
- [THM - Firewall Fundamentals](https://tryhackme.com/room/firewallfundamentals)
- [IDS / IPS and Firewall](https://youtu.be/l7FeR1MIRFY)

