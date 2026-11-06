## 1. DoS Attacks

A denial-of-service attack aims to make a service unavailable to legitimate users by exhausting its resources, such as bandwidth, CPU, memory, connections, or application threads.

Common types:

| Type                   | Mechanism                       | Example                                          |
| ---------------------- | ------------------------------- | ------------------------------------------------ |
| Volumetric             | Flood bandwidth with traffic    | UDP/ICMP floods, DNS amplification               |
| Protocol               | Exhaust connection state tables | SYN flood (half-open TCP connections)            |
| Application-layer (L7) | Abuse legitimate requests       | HTTP flood, Slowloris (slow, incomplete requests) |

A single-source DoS originates from one machine/IP. It is easier to block (for example, through IP filtering), but it can still be effective against under-provisioned targets.

---
## 2. DDoS Attacks

A distributed denial-of-service attack uses **many geographically dispersed sources** simultaneously, often thousands to millions of compromised devices, making it far harder to mitigate than a single-source DoS.

#### Why DDoS is more dangerous:
- Traffic comes from many legitimate-looking IPs, so simple IP blocking fails.
- Overwhelms mitigation capacity, not just the target
- Can be rented cheaply ("booter"/stresser services) or launched via botnets

---
## 3. Botnets

A botnet is a network of compromised devices ("bots" or "zombies") controlled remotely by an attacker via command-and-control (C2) infrastructure.

#### How devices get recruited
- Malware (Trojans, worms), phishing, and exploit kits.
- Exploitation of default credentials (routers, IP cameras, DVRs)
- Unpatched vulnerabilities

#### C2 architectures
- Centralized (IRC, HTTP): easy to take down.
- Peer-to-peer: resilient and harder to disrupt.
- Domain generation algorithms (DGAs): rotate domains to evade blocklists.

---
## 4. Attack Impact

1. Direct impact
	- Service downtime -> revenue loss
	- Reputation damage and customer churn
	- Incident response costs (staff, mitigation services, forensics)
	- Ransom DDoS (RDDoS) -> Attackers demand money to stop
	
2. Indirect / technical impacts
	- collateral damage to shared infrastructure (ISPs, cloud neighbours)
	- Smokescreen effect: A DDoS attack distracts defenders while attackers exfiltrate data or breach systems.
	- resource exhaustion cascading to dependent services
	
3. Business/legal
	- Regulatory and contractual penalties (uptime obligations).
	- Insurance implications.
	- Potential safety consequences for critical infrastructure (healthcare, finance, and utilities).

---
## 5. Mitigation Approaches

1. Architectural / preventive
	- Redundancy & load balancing: distribute traffic, avoid single points of failure
	- Anycast and CDN absorption: Spread attack traffic across global edge nodes.
	- Rate limiting and connection caps: Throttle abusive patterns at the edge.
	- Scrubbing centers: Filter malicious traffic and pass clean traffic through.
	- Upstream ISP coordination: Use blackhole routing, RTBH, or traffic diversion.
	
2. Detection & Response
	- Traffic monitoring/baselining: anomaly detection to spot flood early
	- DDoS protection services (Cloudflare, Akamai, AWS Shield): always-on or on-demand.
	- Incident response playbooks: Define escalation, communication, and failover procedures.
	
3. Hardening the target
	- SYN cookies, connection timeouts: resist protocol floods
	- Application-layer defenses: CAPTCHAs, WAF rules, and request validation.
	- Patch management: Prevent botnet recruitment of your own assets.

---
## Reference

- [Youtube - DoS and DDoS](https://youtu.be/mMtRcWStrfw)
- [Youtube - Mitigation](https://youtu.be/E6t_jrk3LUs)



