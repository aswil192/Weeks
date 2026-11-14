## 1. OSI Model

The Open Systems Interconnection model is a conceptual framework developed by ISO to standardize network communication. It divide networking into 7 layers, each with specific responsibilities.

| Layer        | Function                                       | Examples               |
| ------------ | ---------------------------------------------- | ---------------------- |
| Application  | User-facing services, network APIs             | HTTP, FTP, DNS, SMTP   |
| Presentation | Data formatting, encryption, compression       | TLS/SSL, JPEG, ASCII   |
| Session      | Establish/manage/terminate sessions            | RPC, NetBIOS, PPTP     |
| Transport    | End-to-end delivery, segmentation, reliability | TCP, UDP               |
| Network      | Logical addressing, routing                    | IP, ICMP, OSPF         |
| Data Link    | Framing, MAC addressing , error detection      | Ethernet, Wi-Fi, ARP   |
| Physical     | Bits on the wire, signaling                    | Cables, hubs, voltages |
![[0c8410d11655d3c6c0fce93dcd2653c4.webp]]

---
## 2. TCP/IP Model

The practical model the internet actually runs on. It maps to OSI as follows

| TCP/IP Layer          | Maps to OSI | Protocols            |
| --------------------- | ----------- | -------------------- |
| Application           | Layers 5-7  | HTTP, DNS, SMTP, SSH |
| Transport             | Layer 4     | TCP, UDP             |
| Internet              | Layer 3     | IP, ICMP, ARP*       |
| Network Access (Link) | Layers 1-2  | Ethernet, WiFi       |
>**Difference:** TCP/IP collapses OSI's to three layers into one Application layer and combines the bottom tow into Network Access. OSI is a reference model (teaching/design); TCP/IP is an implementation model (what runs in the real networks)

---
## 3. Layer Responsibilities

**Physical (L1):** Transmits raw bits. Defines voltage, cables specs, pin layouts, data rates. Devices: hubs, repeaters, cables.

**Data Link (L2):** Organizes bits into frames. provides MAC addressing (48 bit), error detection (FCS/CRC), and media access control. splits into LLC and MAC sub-layers. Devices: switches, bridges, NICs. Protocols: Ethernet, WiFi, PPP.

**Network (L3):** Logical addressing (IP) and routing between networks. Path selection, framentation, TTL handling, Devices: routers L3 switches. Protocols: IPv4/IPv6, ICMP, OSPF, BGP.

**Transport (L4):** End-to-end delivery between processes. Uses port numbers. Segmentation/reassembly, flow control, error recovery (TCP) or best-effort (UDP).

**Session (L5):** Opens, manages, and tears down sessions between applications (dialog control, checkpointing).

**Presentation (L6):** Translates data formats: character encoding (ASCII/Unicode), compression, encryption/decryption

**Application (L7):** Network services for end users: web browsing, email, file transfer, DNS resolution

---
## 4. Packet Flow

Encapsulation (sending host, top-down):

```
Application data
   → [L4] add TCP/UDP header        = Segment
   → [L3] add IP header             = Packet
   → [L2] add Ethernet header+trailer = Frame
   → [L1] convert to bits           = Bits on wire
```

Decapsulation (receiving host, bottom-up): Each layer strips its header and passes the payload up.

End-to-end example (PC -> Web Server):

1. Browser creates HTTP request (L7).
2. TCP adds source/dest ports, sequence number (L4).
3. IP adds source/dest MAC addresses (L3)
4. Ethernet adds source/dest MAC addresses (L2)
5. Bits transmitted (L1)
6. Each router along the path decapsulates to L3, examines the destination IP, consults its routing table, and re-encapsulates with new L2 frame for the next hop (MAC addresses change hop-by-hop; IP addresses stay end-to-end).
7. Destination host decapsulates up the stack; the web server process receives the request.

> MAC addresses are local to each link; IP address are end-to-end. TTL decrements at each router to prevent loops.

---
## 5. Troubleshooting concepts

| Layer | Check                                           | Tools                                 |
| ----- | ----------------------------------------------- | ------------------------------------- |
| L1    | Cable plugged in? Link right?                   | Physical inspection, cable tester     |
| L2    | MAC reachable? Switch port up? VLAN correct?    | `arp -a`, `show mac address- table`   |
| L3    | IP configured? Gateway reachable? route exists? | `ping`, `ipconfig`,`traceroute`       |
| L4    | Port open? Firewall blocking?                   | `telnet host port`, `netstat`, `nc`   |
| L5-7  | Service responding? DNS resolving? Cert valid?  | `curl`, `nslookup`, browser dev tools |

---
## Reference

- [THM - OSI Model](https://tryhackme.com/room/osimodelzi)
- [Youtube - OSI and TCP/IP](https://youtu.be/CRdL1PcherM)



