Network security is the practice of protecting the integrity, confidentiality, and availability  of data and systems as they communicate across networks.

## 1. Secure communication

Secure communication ensures that data traveling between parties cannot be read, altered, or spoofed by unauthorized entities. It rests on three pillars (CIA)

#### Technologies

- TLS/SSL — encrypts web traffic (HTTPS). Uses asymmetric crypto for key exchange and symmetric crypto for bulk data.
- IPsec — secures IP packets at the network layer (used in VPNs).
- SSH — encrypted remote administration.
- HTTPS, SFTP, SMTPS — application-layer secure protocols.
- Perfect Forward Secrecy (PFS) — ensures past sessions stay secure even if long-term keys are compromised.

---
## 2. Network Segmentation

Segmentation divides a network into isolated zones so that a compromise in one area cannot spread freely to others — a key defense-in-depth and least-privilege principle.

#### Approaches

- Physical segmentation — separate hardware/switches.
- VLANs — logical Layer 2 separation.
- Subnetting — Layer 3 separation with routing controls.
- Firewalls / ACLs between segments.
- Microsegmentation — fine-grained, per-workload policies (common in data centers/cloud, e.g., software-defined networking).
- DMZ — a buffer zone for internet-facing services.
- Zero Trust — "never trust, always verify," treating every segment as untrusted.

>**Benefits:** limits lateral movement, reduces attack surface, contains breaches, aids compliance (e.g., PCI-DSS isolating cardholder data), and improves performance/traffic control.

---
## 3. Access Control

Access control determines who can access what and how. It's built on AAA: Authentication (verify identity), Authorization (grant permissions), Accounting (log activity).

#### Models

- DAC (Discretionary) — owner sets permissions (e.g., file ACLs).
- MAC (Mandatory) — system-enforced labels (e.g., military classification).
- RBAC (Role-Based) — permissions tied to job roles.
- ABAC (Attribute-Based) — decisions based on attributes (user, resource, context).
- Least Privilege — minimum access needed to do the job.
- Zero Trust / Just-in-Time access — grant access only when needed, briefly.

**Threats addressed**: credential theft, privilege escalation, insider misuse, unauthorized device access.

---
## 4. VPN Concepts

A Virtual Private Network creates an encrypted tunnel over an untrusted network (like the internet), extending a private network securely.

#### Tow main types

- Site-to-site VPN — connects entire networks (e.g., branch office to HQ).
- Remote-access VPN — connects individual users to a corporate network.

#### Concepts

- Tunneling — encapsulates one protocol inside another (e.g., IPsec, GRE, L2TP).
- Encryption — protects payload confidentiality.
- Authentication — verifies endpoints (certificates, pre-shared keys, MFA).
- Split tunneling — routes only some traffic through the VPN (trade-off: convenience vs. security).
- Protocols: IPsec (AH/ESP, IKE), SSL/TLS VPNs (clientless or client-based), WireGuard (modern, lightweight), OpenVPN.

**Threats addressed:** interception on public networks, unauthorized remote access, site-to-site data protection.

---
## 5. Security Monitoring

Monitoring provides **visibility** — detecting, alerting on, and responding to threats in real time. It's the operational backbone of incident detection and response.

#### Components

- Log collection & SIEM (Security Information and Event Management) — aggregates and correlates logs (e.g., Splunk, Elastic, Sentinel).
- IDS/IPS — intrusion detection/prevention (signature and anomaly-based).
- NTA/NDR — network traffic analysis for anomalous behavior.
- EDR/XDR — endpoint and extended detection & response.
- SOAR — automated response playbooks.
- Threat intelligence feeds and honeypots.
- SOC (Security Operations Center) — the team/process running 24/7 monitoring.

#### Practices to prevent

- Baseline normal behavior to spot anomalies.
- Alert triage and incident response workflows.
- Log retention for forensics and compliance.
- Metrics like MTTD (mean time to detect) and MTTR (mean time to respond).

**Threats addressed:** intrusions, malware, data exfiltration, insider threats, advanced persistent threats (APTs).

---
## Quick Table

| Layer                | Function                         |
| -------------------- | -------------------------------- |
| Secure communication | Protects data in transit         |
| Segmentation         | Limits where attackers can go    |
| Access control       | Controls who gets in             |
| VPN                  | Securely extends the perimeter   |
| Monitoring           | Provides visibility and response |



