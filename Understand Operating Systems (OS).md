
## 1. What is an operating system

An operation system is the core software that coordinates everything happening on a computer. It sits between the user, applications and the system's physical hardware, acting as the invisible manager that keeps the entire machine running as one unified system.

![[operating system.svg]]

---

## 2. Explain the role of an OS in managing computer hardware and software

We need an operating system because it provides this all-important job of coordination and structuring that makes modern computing possible. Without an OS, each application would need direct control over the CPU, memory, files, devices and security. This would quickly cause conflicts and the OS handles this by acting as the central organiser.

Inside an modern computer, differnet parts of the system operate at various permission levels. Some components can communicate directly with the hardware, While regular applications run in a safer, restricted environment. This separation is intentional and helps prevent conflicts and security issues.

![[Software and hardware.png]]

---

## 3. Describe how an OS contributes to cybersecurity (access control, user management, security).

An operating system (OS) is the foundation of cyberseucrity on any computing device. It sits between users, applications and hardware, and enforces the rules that determine who can do what.

#### Access Control

Access control is the OS's way of deciding *who* can access *which resources* and *how*. The OS enforces this at the kernel level, so applications and users cannot bypass it.

1. Core Models:
	- Discretionary Access control (DAC): The resource owner decides permissions like` rwx---rwx`. Flexible but relies on user judgement.
	- Mandatory Access Control (MAC): The OS enforces system-wide policy labels. Even root can be constrained. Used in high-security environments.
	- Role-Based Access Control (RBAC): Permissions are tied to roles, not individuals -- common in enterprise Windows AD Environments
	- Attribute-Based Access control (ABAC): Decisions based on attributes (user, resource, context, time).
	
2. How the OS enforces it:
	- Reference monitor: A kernel component that meditates every access request and checks it against policy, it must be tamper-proof, always invoked, and verifiable.
	- Privilege separation: Processes run with the least privilege needed. The kernel distinguishes user mode from kernel mode, so user code cannot directly touch protected memory or hardware.
	- Capabilities and tokens: Fine-grained rights let the OS grant only specific privileges instead of all-or-nothing root/admin.
	- sandboxing: The OS isolates applications so a compromised app cannot reach other data.

3. Why it matters: 
	- Access control contains the blast radius of a compromise. If malware runs as a low-privilege user, DAC/MAC limits what it can read, modify, or execute.

#### User Management

User management is how the OS identifies, authenticates and accounts for users and services. Without reliable identity, access control has nothing to enforce against.

1. Identification and Authentication:
	- Accounts and credentials: The OS stores user accounts and verifies credentials (password hashed with salted, slow algorithms like bcrypt/Argon2; or via PAM on Linux, WIndows Hello/LSA on Windows)
	- Multi-factor authentication: Modern OSes integrate MFA (eg: Windows Hello, Bio-metrics/PIN, smart cards)
	- Service and system accounts: The OS provides dedicated low-privilege accounts for daemons/services, so a compromised services doesn't as a full user.
	
2. Authorization and  separation:
	- Groups and roles: Users are organized into groups to manage permissions at scale
	- Separation of duties: The OS distinguishes standard users from administrators, enforcing elevation ( UAC on windows and sudo/Polkit on Linux ) so privileged actions require explicit, auditable consent.
	- Session management: Login sessions, timeouts, lock screens, and logout policies limit exposure of active sessions.
	
3. Accountability
	- Audit trails: The OS logins, privilege escalations, and account changes (windows event logs, Linux auditd, syslog). This supports forensics and intrusion detection.
	- Account lifecycle: The OS supports disabling, locking, and expiring account -- critical for offboarding and limiting stale credentials.
	
4. Why it matters: 
	- Weak user management (shared accounts, excessive admin rights, no MFA) is a leading cause of breaches. The OS provides the primitives to enforce strong identity hygiene.

#### Security Mechanisms

The OS provide layered defenses: 
- Memory protection: Address space layout randomization (ASLR), non-executable memory (NX/DEP), stack canaries, and kernel/user memory isolation make exploitation harder.
- Secure Boot: UEFI secure boot, code signing and measured boot (TPM) ensure only trusted code runs at startup and tampering
- Encryption: full-disk encryption (bitlocker, LUKS), file-level encryption (EFS), and key management protect data at rest if a device is lost or stolen.
- Patch management and updates: The OS delivers security patches for vulnerabilities -- timely updates are a primary defense
- Firewall: Built-in firewalls restrict network exposure.
- Isolation and Virtualisation: Namespaces, control groups, hypervisors, and containers isolate workloads so compromise of one doesn't spread.
- Logging and monitoring: Centralised event logging, integrity monitoring and anomaly detection.
- Trusted Platform Module Integration: Stores keys and measurements for disk encryption and attestation.

---

## List common operating systems (Windows, Linux, macOS).

| OS                                   | Vendor        | Notes                                                               |
| ------------------------------------ | ------------- | ------------------------------------------------------------------- |
| Windows 10/11                        | Microsoft     | Most widelu used desktop OS; Closed source; domainant in enterprise |
| Windows Server (2016/2019/2022/2025) | Microsoft     | Server variant; Active Directory, Hyper-V, IIS                      |
| macOS                                | Apple         | Unix-based (Darwin), closed source; runs only on Apple hardware     |
| Linux Distributions                  | Various       | Open Source                                                         |
| Chrome OS                            | Google        | Linux Based; Cloud-centric; common in education                     |
| FreeBSD / OpenBSD / NetBSD           | BSD Community | Unix-like; Strong Security reputation.                              |

#### Common Linux Distributions

- Debain-Based -> Ubuntu, Zorin, Kali Linux, Linux Mint
- Red Hat Based -> RHEL, Fedora, RockyLinux
- SUSE-Based -> SUSE Linux Enterprise, openSUSE
- Arch-Based -> Garuda OS,Arch Linux, BlackArch
- Others -> Alpine (containers), Gentoo, Amzon Linux

---

## Reference

- [TryHackMe - Operating system introduction](https://tryhackme.com/room/operatingsystemsintroduction)


