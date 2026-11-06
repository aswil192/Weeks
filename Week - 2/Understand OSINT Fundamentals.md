## 1. Open-Source Intelligence

OSINT is intelligence **produced from publicly available information** that is collected, validated, and analyzed to answer a specific question or support a decision.

#### Key definition points
- Open source: legally and publicly accessible.
- Intelligence: the analysis layer. Raw data isn't intelligence; it becomes intelligence when contextualized, corroborated, and turned into an actionable insight.
- Legal/ethical boundary: OSINT relies on information that is lawfully accessible. It does not include hacking, credential abuse, pretexting, or accessing private systems.

---
## 2. Public Information Gathering

OSINT draws from a wide spectrum of public sources: 

| Source Category          | Examples                                                                     |
| ------------------------ | ---------------------------------------------------------------------------- |
| Web & search engines     | Google, Bing, etc.                                                           |
| Social Media             | Profiles, posts, connections, geolocation metadata                           |
| Public records           | Company registries, court records, property/land records, SEC filings        |
| Government sources       | Sanctions lists, watchlists, FOIA responses, procurement data                |
| Technical / network data | DNS records, WHOIS, certificate transparency logs, IP/ASN data, Shodan/Censys |
| Code repositories        | GitHub, GitLab, leaked code                                                  |
| Media                    | News archives, images, video                                                 |

---
## 3. Search Techniques

Effective OSINT depends on **search operators and structured querying.**
- Google Dorking
- Shodan / Censys / FOFA
- Have I Been Pwned
- Certificate Transparency (crt.sh): subdomain discovery via TLS certs
- WHOIS / DNS history (SecurityTrails, ViewDNS): infrastructure attribution
- Reverse Image search (Google Lens, TinEye, Yandex)
- Metadata extraction (ExifTool)

---
## 4. Threat Research

OSINT powers threat intelligence.

| Activity                        | Description                                                                                  |
| ------------------------------- | -------------------------------------------------------------------------------------------- |
| Threat actor profiling          | Attribution, TTPs (tactics, techniques, and procedures), motivations, targeting              |
| IOC enrichment                  | Contextualizing indicators (IPs, hashes, domains) with reputation, history, and related campaigns |
| Infrastructure mapping          | Pivoting on domains / certs / ASNs to find related C2 or phishing infrastructure             |
| Malware leak analysis           | Public sandbox reports, forum chatter, and breach disclosures                                |
| Vulnerability intelligence      | KEV, EPSS, exploit availability, PoC repos                                                   |
| Brand/attack surface monitoring | Phishing domains, typosquatting, exposed assets, leaked credentials                          |
#### Frameworks and standards
- MITRE ATT&CK: adversary TTP knowledge base
- MITRE D3FEND: defensive countermeasures mapping 
- Diamond model: adversary/capability/infrastructure/victim analysis

#### Threat intel tiers
- Strategic: big-picture trends for leadership
- Operational: campaign-level insight for defenders
- Tactical: IOCs and TTPs for SOC/IR

> **Caution:** Public threat intelligence is noisy and sometimes deliberately deceptive (false flags, poisoned IOCs). Validate it before acting, especially before blocking IOCs at scale.

---
## 5. Investigation Workflows

A disciplined OSINT investigation follows a **repeatable, documented process.**

1. **Define scope & objectives**
	- What question are we answering? What's in/out of scope?
    - Legal review: jurisdiction, privacy laws (GDPR, CFAA), terms of service, authorization
2. **Plan collection**
	- Source list, tooling, OPSEC posture, timeline
	- Identify collection constraints (passive only? disclosure requirements?)
3. **Collect and preserve**
	- Capture artifacts with timestamps, hashes, screenshots, archived URLs
	- Maintain a **chain-of-custody log** if findings may be used legally
4. **Process & organize**
	- Normalize data (dedupe, structure, tag)
	- Build link charts / entity relationship maps (Maltego, Gephi, or manual)
5. **Analyze**
	- Corroborate, identify contradictions, assess confidence
	- Apply structured analytic techniques (ACH — Analysis of Competing Hypotheses; key assumptions checks)
	- Separate **fact / inference / speculation** explicitly
6. **Produce Intelligence**
	- Report with findings, confidence levels, sourcing, and caveats
	- Actionable recommendations, not just raw data dumps
7. **Disseminate & Feedback**
	- Deliver to stakeholders with appropriate TLP marking
	- Capture lessons learned; update source lists and tooling

---
## Summary

OSINT is the discipline of turning **lawfully public information** into **analyzed, actionable intelligence**. It spans a broad source spectrum (web, records, technical data, social media), relies on **structured search techniques** (dorking, pivoting, specialized engines), powers **threat research** (actor profiling, IOC enrichment, ATT&CK mapping), and is governed by **repeatable investigation workflows** with strict documentation, corroboration, and legal/ethical boundaries. The value is in the **analysis and verification**, not the collection volume.

---
## Reference

- [THM - OhSINT](https://tryhackme.com/room/ohsint)
- [THM - Search Skills](https://tryhackme.com/room/searchskills)
- [THM - Searchlight - IMINT](https://tryhackme.com/room/searchlightosint)
- [OSINT framework](https://osintframework.com/)


