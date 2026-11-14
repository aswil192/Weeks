## 1. IPv4

**IPv4 (Internet Protocol version 4)** is the fourth version of the Internet Protocol and the most widely used addressing system. It uses **32-bit addresses**, giving a total address space of **2³² ≈ 4.3 billion** unique addresses.

Format: Dotted decimal notation - four octets separated by periods (`198.162.1.1`). Each octets is 8 bits (0-255).

Structure: An IPv4 address has two parts:

- Network portion - identifies the network
- Host portion - identifies the device on that network

The split is defined by the subnet mask (`255.255.255.0` or`/24`)

#### Address class (historical)

| Class | Range                       | Default Mask | Purpose             |
| ----- | --------------------------- | ------------ | ------------------- |
| A     | 1.0.0.0 - 126.255.255.255   | /8           | Very large networks |
| B     | 128.0.0.0 - 191.255.255.255 | /16          | Medium networks     |
| C     | 192.0.0.0 - 233.255.255.255 | /24          | Small networks      |
| D     | 244.0.0.0 - 239.255.255.255 |              | Multicast           |
| E     | 240.0.0.0                   |              | Experimental        |
>Key limitations: Address exhaustion (mitigated by NAT and CIDR), no-built-in security (IPsec is optional), and complex header structure.

---
## 2. IPv6

**IPv6 (Internet Protocol version 6)** was developed to solve IPv4 exhaustion. It uses **128-bit addresses**, providing **2¹²⁸ ≈ 3.4 × 10³⁸** addresses — effectively unlimited.

**Format:** Eight groups of four hexadecimal digits separated by colons, e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`

**Address types:**

- **Unicast** — one-to-one (global, link-local `fe80::/10`, unique local `fc00::/7`)
- **Multicast** — one-to-many (`ff00::/8`)
- **Anycast** — one-to-nearest

#### Improvements over IPv4

- Vastly larger address space
- Simplified, fixed-length header (40 bytes) for faster routing
- Built in IPsec support 
- Stateless address autoconfiguration (SLAAC) - no DHCP required
- No NAT needed
- No broadcast (replaced by multicast)

---
## 3. Public IPs

**Public IP addresses** are globally unique, routable addresses assigned by **IANA** and its Regional Internet Registries (RIRs: ARIN, RIPE, APNIC, LACNIC, AFRINIC) to ISPs, who allocate them to customers.

Characteristics:

- Reachable over the internet 
- Must be globally unique 
- Typically assigned to routers/firewalls (the internet-facing interface)
- Can be static (fixed, common for servers) or dynamic (changes, common for home connections via DHCP from ISP)

---
## 4. Private IP

**Private IP addresses** are reserved for use within internal networks and are **not routable on the public internet**. Defined in **RFC 1918** for IPv4

| Range                         | CIDR           | Class |
| ----------------------------- | -------------- | ----- |
| 10.0.0.0 - 10.255.255.255     | 10.0.0.0/8     | A     |
| 172.16.0.0 - 172.31.255.255   | 172.16.0.0/12  | B     |
| 192.168.0.0 - 192.168.255.255 | 192.168.0.0/16 | C     |
`127.0.0.1` - loopback

>NAT allows many private hosts to share one public IP, which is why private addressing works. Private IPs provide security (Internal hosts aren't directly reachable) and conserve public address space.

---
## 5. Subnetting Fundamentals

**Subnetting** is the process of dividing a larger network into smaller, more manageable **subnets**. It improves performance (smaller broadcast domains), security (segmentation), and address efficiency.

#### Concepts:









