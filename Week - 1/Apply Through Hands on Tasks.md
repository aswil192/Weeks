
## 1. Build a Personal Cybersecurity Lab

![img](IMG/lab.png)


---

## 2. Analyze  recent Cyber Incidents

#### i. [PHP2Shell (20 Oct 2026)](https://en.wikipedia.org/wiki/PHP2Shell)

PHP2Shell is a pair of high-impact computer vulnerabilities (CVE-2026-109618 and CVE-2026-109619) concerning memory-safety flaws in PHP versions 5.4–8.5. They allow a malicious user to execute code remotely (RCE) and potentially gain control of the website host. The vulnerabilities were discovered with the help of AI in August 2026, and their existence was publicly announced on 20 October 2026. An emergency patch for versions 8.2, 8.3, 8.4, and 8.5, along with details about the vulnerabilities, was released the following day. Numerous websites were temporarily taken offline to apply the patches before the vulnerabilities could be exploited.

#### ii. [Storm-0940 (AI-Assisted Attack)](https://expel.com/blog/storm-0940-artex-attacks-connectwise-app-abuse-and-okta-sign-ups/#1)

Microsoft reported that a threat actor named Storm-0940 used an AI attack framework called ARTEX to target hundreds of organizations. Beyond the ConnectWise incident, this group was also observed abusing Okta self-service registration to create rogue accounts and conduct password spraying.

#### iii. [Plex Media Server](https://blog.senthorus.ch/posts/weekly_reviews/26_10_2026/)

A chain of four vulnerabilities was weaponized almost immediately after technical details became public, allowing unauthenticated remote code execution. Attackers were observed deploying cryptocurrency miners on exposed servers.

---

## 3. Common Attack Types

1. Social Engineering Attacks
	- Phishing: Fraudulent emails/messages that impersonate trusted entities to steal credentials or deliver malware. Variants include **spear phishing** (targeted), **whaling** (executives), **vishing** (voice), and **smishing** (SMS).
	- Pretexting: Fabricating a scenario to manipulate victims into revealing information.
	- Baiting: Luring victims with infected USB drives or fake downloads.
	
2. Malware Based Attacks
	- Ransomware: Encrypts data and demands payment.
	- Trojans: Malware disguised as legitimate software.
	- Worms: Self-replicating malware spreading across networks.
	- Spyware/keyloggers: Covertly capture keystrokes, screenshots, and data.
	- Rootkits: Hide deep in the OS to maintain persistent access.
	- Botnets: Networks of compromised devices used for DDoS or spam.
	
3.  Network Infrastructure attacks
	 - DDoS: Overwhelming services with traffic.
	- MitM: Intercepting communications, such as through ARP spoofing or DNS poisoning.
	- DNS spoofing/cache poisoning: Redirecting traffic to malicious sites.
	 - SQLi: Injecting malicious SQL into input fields to access databases.
	 - XSS: Injecting scripts into web pages viewed by others.
	 - CSRF: Tricking authenticated users into executing unwanted actions.
	 
4. Credential & Authentication attacks
	- Brute-force / credential stuffing: Repeated login attempts using leaked password lists.
	- Password spraying: Trying common passwords across many accounts.
	- Credential dumping: Extracting hashes/passwords from memory, for example, using Mimikatz.
	- Session hijacking: Stealing session cookies and tokens.
	- Pass-the-hash: Reusing captured NTLM hashes for authentication.
	
5. Exploitation & Application attacks
	- Zero-day exploits: Attacking previously unknown vulnerabilities.
	- Buffer overflow: Overwriting memory to execute arbitrary code.
	- Privilege escalation: Gaining higher-level permissions.
	- Directory Traversal: Accessing files outside intended directories.
	- Insecure deserialization: Exploiting object deserialization to execute code.
	
6. Advanced Persistent Threats (APTs) & Supply Chain
	- APTs: Long-term, stealthy intrusions by nation-state or organised groups.
	- Supply chain attacks: Compromising trusted software/vendors.
	- Watering hole attacks: Infecting sites frequented by a target group.
	
7. Wireless and Physical attacks
	- Evil twin/rogue AP: Fake Wi-Fi access points used to intercept traffic.
	- WPA cracking: Breaking wireless encryption.
	- Bluetooth attacks (bluejacking, bluesnarfing).
	
8. AI/LLM Era Attacks
	- Prompt Injection: Manipulating LLM inputs to bypass safeguards.
	- Deepfakes: Synthetic media used for fraud/social engineering.
	- AI-generated phishing: Highly convincing, personalized lures at scale

---

## 4. [Threat Landscape Report](Threat%20Landscape%20Report.md)

---

## 5. Compare Cybersecurity Domains

| Domain                                             | Primary Focus                             | Typical Roles                                  | Core Skills                                                 |
| -------------------------------------------------- | ----------------------------------------- | ---------------------------------------------- | ----------------------------------------------------------- |
| **Governance, Risk & Compliance (GRC)**            | Policy, risk, audit, regulatory alignment | GRC analyst, risk manager, compliance officer  | Risk assessment, policy writing, audit, NIST/ISO/PCI        |
| **Security Architecture & Engineering**            | Designing secure systems                  | Security architect, security engineer          | Network/system design, threat modeling, cryptography        |
| **Network Security**                               | Protecting network infrastructure         | Network security engineer, firewall admin      | Firewalls, IDS/IPS, segmentation, VPN, routing              |
| **Application Security (AppSec)**                  | Securing software/SDLC                    | AppSec engineer, product security              | Secure coding, SAST/DAST, OWASP Top 10, threat modeling     |
| **Cloud Security**                                 | Securing cloud environments               | Cloud security engineer/architect              | IAM, CSPM, shared responsibility, container security        |
| **Identity & Access Management (IAM)**             | Authentication/authorization              | IAM engineer, identity architect               | SSO, MFA, RBAC/ABAC, PAM, directory services                |
| **Security Operations (SecOps/SOC)**               | Detection, response, and monitoring       | SOC analyst, incident responder, threat hunter | SIEM, EDR, log analysis, IR playbooks                       |
| **Threat Intelligence & Vulnerability Management** | Understanding threats and finding weaknesses | Threat intel analyst, vuln manager, pentester | CVSS, scanning, OSINT, exploit analysis                     |
| **Offensive Security / Pentesting**                | Attack simulation                         | Pentester, red teamer, bug bounty hunter       | Exploitation, reconnaissance, privilege escalation, reporting |
| **Digital Forensics & Incident Response (DFIR)**   | Investigate and contain incidents         | Forensic analyst, IR lead                      | Evidence handling, memory/disk forensics, timeline analysis |
| **Physical Security**                              | Protecting facilities/assets              | Physical security specialist                   | Access control, CCTV, environmental controls                |









