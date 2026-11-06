## 1. Defence in Depth

This principle assumes that any single security control can eventually fail or be bypassed, so it relies on **multiple, overlapping layers** of protection. If an attacker breaches one layer (such as a firewall), other independent controls (such as access control or encryption) still stand in the way.

---
## 2. Least Privilege

This principle dictates that users, processes, and programs should receive only the **minimum permissions** necessary to perform their functions. Its main goals are to reduce the attack surface (the number of entry points for attackers) and limit the blast radius (the extent of damage) if an account or system is compromised.

---
## 3. Zero Trust Concepts

Zero trust rejects the traditional "castle and moat" idea that anything inside the corporate network is safe. Instead, it operates on the principle of "never trust, always verify." It requires continuous validation of identity, device health, and context before granting access to any specific resource, regardless of where the request originates.

---
## 4. Security Layers

Defense in depth is implemented through distinct layers, each targeting different attack vectors:

- Physical: Locked facilities, badge readers, and guards protect hardware.
- Identity & access: Multi-factor authentication (MFA) and RBAC.
- Perimeter: Firewalls and DDoS protection at the network boundary.
- Network: Segmentation and micro-segmentation to prevent lateral movement.
- Compute: Patching operating systems and hardening servers/containers.
- Application: Secure coding practices and input validation help prevent exploits.
- Data: Encryption and classification to protect the information itself.

---
## 5. Risk Reduction Strategies

These principles translate directly into concrete risk-reduction measures:

- Containment: Least privilege ensures that a compromised account cannot easily be used to pivot to critical systems or exfiltrate sensitive data.
- Resilience: Defence in depth ensures that a single misconfiguration or zero-day vulnerability does not lead to a total breach.
- Visibility: Zero trust architectures often enforce logging and monitoring at every access point, making anomalous behaviour easier to detect.

---
## Reference

- [TryHackMe - Security Principles](https://tryhackme.com/room/securityprinciples)



