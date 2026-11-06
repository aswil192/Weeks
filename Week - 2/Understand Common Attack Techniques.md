## 1. Phishing

Phishing is a **fraudulent message** (email, SMS/smishing, voice/vishing, QR code) designed to trick a recipient into revealing credentials, clicking a malicious link, or opening an infected attachment. Variants include spear phishing (targeted at specific individuals), Whaling (targeted executives), and business email compromise (BEC).

---
## 2. Social Engineering

Social engineering is the broader **manipulation of people** to divulge information or perform actions. It includes phishing across various channels, as well as pretexting (fake scenarios), tailgating (following someone through a door), baiting (infected USB drives), and quid pro quo (fake IT support calls).

---
## 3. Credential Attacks

- Brute force/password spraying: trying many passwords on one account, or one common password across many accounts.
- Credential stuffing - replaying breached username/password pairs.
- Pass-the-hash / pass-the-ticket - reusing captured authentication material without cracking it.
- Kerberoasting/LLMNR poisoning: extracting or relaying credentials in Windows environments.
- Weaknesses exploited: reused passwords, lack of MFA, and excessive account privileges.

---
## 4. Malware Delivery

Malware delivery is the process of getting malware onto a system, often as the payload stage of phishing or social engineering. Common methods include malicious attachments, drive-by downloads, exploit kits, malicious ads (malvertising), supply-chain compromise (trojanized software updates), and USB drops.

---
## 5. Reconnaissance Activities

The pre-attack phase where adversaries gather intelligence:
- Passive: OSINT, social media scraping, DNS/WHOIS lookups, and job postings (which may reveal a technology stack).
- Active: Port scanning, service enumeration, vulnerability scanning, and network mapping.

---
## Reference

- [TryHackMe - PhishingBasics](https://tryhackme.com/room/phishingbasics)

