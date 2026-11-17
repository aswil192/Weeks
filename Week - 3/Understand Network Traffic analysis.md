Network Traffic Analysis (NTA) is the practice of inspecting, monitoring, and analyzing network communications to detect threats, troubleshoot performance, and maintain visibility.

## 1. Packets

The atomic unit of network communication. A packet is a formatted block of data carrying:

- Header — source/destination IP, ports, protocol, flags, TTL, checksums
- Payload — the actual application data (HTTP, DNS queries, etc.)
- Trailer — often frame check sequence at Layer 2

#### Why they matter

- Ground truth — packets are the raw evidence; everything else (flows, logs, alerts) is derived from them
- Deep inspection — full packet capture (PCAP) enables payload analysis, protocol decoding, file carving, and retrospective forensics
- Limitations — at scale, storing every packet is expensive (storage, CPU, privacy); most organizations sample or retain only headers

---
## 2. Traffic Flows

Aggregated summaries of packets sharing common attributes — typically the 5-tuple (src IP, dst IP, src port, dst port, protocol) plus metadata: byte/packet counts, timestamps, TCP flags, durations.

#### Why they matter

- Scalability — flow records (NetFlow, IPFIX, sFlow) are orders of magnitude smaller than PCAP, enabling retention of weeks/months of data
- Behavioral baselining — "who talks to whom, how much, how often" reveals anomalies (beaconing, data exfiltration, lateral movement)
- Efficient hunting — flow analysis narrows the haystack before pulling full packets

---
## 3. Network Visibility

The degree to which you can observe traffic across your environment — the coverage problem.

#### Dimensions 

- Placement — taps/SPAN ports at perimeter, core, data center, cloud VPCs; east-west (internal) vs. north-south (external) traffic
- Encryption — TLS 1.3 and ECH increasingly blind payload inspection; visibility shifts to metadata, JA3/JA4 fingerprints, SNI, and endpoint telemetry
- Blind spots — encrypted traffic, cloud-native workloads, remote/VPN users, IoT/OT segments
- Cloud & hybrid — VPC flow logs, mirroring, and agent-based collection replace physical taps

---
## 4. Log Generation

Producing structured records of network and security events from sensors and infrastructure.

#### Sources

- Network sensors — firewall logs, IDS/IPS alerts (Suricata, Snort), DNS logs, proxy logs, flow exporters
- Endpoints — EDR telemetry, OS event logs
- Identity & cloud — auth logs, cloud audit trails (CloudTrail, VPC flow logs)

#### Best practices:

- Normalize to a common schema (e.g., ECS, OCSF) for cross-source correlation
- Time sync — NTP everywhere; skewed timestamps break correlation
- Retention tiers — hot (searchable) vs. cold (compliance) storage
- Signal vs. noise — log events worth investigating, not everything; tune at the source

>**Pipeline:** Collection → parsing/normalization → enrichment (GeoIP, asset context, threat intel) → SIEM/datalake → detection & hunting.

---
## 5. Threat Indicators

Observable artifacts suggesting malicious activity.

| Type                | Examples                                                                   | Durability                           |
| ------------------- | -------------------------------------------------------------------------- | ------------------------------------ |
| Atomic (IoC)        | IPs, domains, file hashes, URLs                                            | Low — easily changed by attacker     |
| Behavioral          | Beaconing patterns, unusual data volumes, lateral SMB scans, DNS tunneling | High — costly for attacker to change |
| TTPs (MITRE ATT&CK) | Techniques like credential dumping, C2 over HTTPS                          | Highest — structural                 |

---
## Reference

- 