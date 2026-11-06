
## 1. What is an operating system

An operating system is the core software that coordinates everything happening on a computer. It sits between the user, applications, and the system's physical hardware, acting as the invisible manager that keeps the entire machine running as one unified system.

![img](IMG/operating%20system.svg)

---

## 2. Explain the role of an OS in managing computer hardware and software

We need an operating system because it provides the all-important coordination and structure that make modern computing possible. Without an OS, each application would need direct control over the CPU, memory, files, devices, and security. This would quickly cause conflicts, so the OS handles this by acting as the central organiser.

Inside a modern computer, different parts of the system operate at various permission levels. Some components can communicate directly with the hardware, while regular applications run in a safer, restricted environment. This separation is intentional and helps prevent conflicts and security issues.

![img](IMG/Software%20and%20hardware.png)

---

## 3. Describe how an OS contributes to cybersecurity (access control, user management, security).

An operating system (OS) is the foundation of cybersecurity on any computing device. It sits between users, applications, and hardware, and enforces the rules that determine who can do what.

#### Access Control

Access control is the OS's way of deciding *who* can access *which resources* and *how*. The OS enforces this at the kernel level, so applications and users cannot bypass it.

1. Core models:
	- Discretionary Access Control (DAC): The resource owner decides permissions like `rwx---rwx`. This is flexible but relies on user judgment.
	- Mandatory Access Control (MAC): The OS enforces system-wide policy labels. Even root can be constrained. This is used in high-security environments.
	- Role-Based Access Control (RBAC): Permissions are tied to roles, not individuals. This is common in enterprise Windows AD environments.
	- Attribute-Based Access Control (ABAC): Decisions are based on attributes (user, resource, context, and time).
	
2. How the OS enforces access control:
	- Reference monitor: A kernel component that mediates every access request and checks it against policy. It must be tamper-proof, always invoked, and verifiable.
	- Privilege separation: Processes run with the least privilege needed. The kernel distinguishes user mode from kernel mode, so user code cannot directly touch protected memory or hardware.
	- Capabilities and tokens: Fine-grained rights let the OS grant only specific privileges instead of all-or-nothing root/admin.
	- Sandboxing: The OS isolates applications so a compromised app cannot reach other data.

3. Why it matters:
	- Access control contains the blast radius of a compromise. If malware runs as a low-privilege user, DAC/MAC limits what it can read, modify, or execute.

#### User Management

User management is how the OS identifies, authenticates, and accounts for users and services. Without reliable identity, access control has nothing to enforce.

	1. Identification and authentication:
	- Accounts and credentials: The OS stores user accounts and verifies credentials (for example, passwords hashed with salted, slow algorithms like bcrypt/Argon2, or credentials verified via PAM on Linux and Windows Hello/LSA on Windows).
	- Multi-factor authentication: Modern OSes integrate MFA (e.g., Windows Hello, biometrics/PIN, and smart cards).
	- Service and system accounts: The OS provides dedicated low-privilege accounts for daemons/services, so a compromised service does not run with the privileges of a full user.
	
	2. Authorization and separation:
	- Groups and roles: Users are organized into groups to manage permissions at scale.
	- Separation of duties: The OS distinguishes standard users from administrators, enforcing elevation (UAC on Windows and sudo/Polkit on Linux) so privileged actions require explicit, auditable consent.
	- Session management: Login sessions, timeouts, lock screens, and logout policies limit the exposure of active sessions.
	
3. Accountability:
	- Audit trails: The OS logs logins, privilege escalations, and account changes (Windows Event Logs, Linux auditd, and syslog). This supports forensics and intrusion detection.
	- Account lifecycle: The OS supports disabling, locking, and expiring accounts, which is critical for offboarding and limiting stale credentials.
	
4. Why it matters:
	- Weak user management (shared accounts, excessive admin rights, no MFA) is a leading cause of breaches. The OS provides the primitives to enforce strong identity hygiene.

#### Security Mechanisms

The OS provides layered defenses:
- Memory protection: Address space layout randomization (ASLR), non-executable memory (NX/DEP), stack canaries, and kernel/user memory isolation make exploitation harder.
- Secure Boot: UEFI Secure Boot, code signing, and measured boot (TPM) ensure that only trusted code runs at startup and detect tampering.
- Encryption: Full-disk encryption (BitLocker, LUKS), file-level encryption (EFS), and key management protect data at rest if a device is lost or stolen.
- Patch management and updates: The OS delivers security patches for vulnerabilities; timely updates are a primary defense.
- Firewall: Built-in firewalls restrict network exposure.
- Isolation and virtualization: Namespaces, control groups, hypervisors, and containers isolate workloads so a compromise of one does not spread.
- Logging and monitoring: Centralized event logging, integrity monitoring, and anomaly detection.
- Trusted Platform Module Integration: Stores keys and measurements for disk encryption and attestation.

---

## List common operating systems (Windows, Linux, macOS).

| OS                                   | Vendor        | Notes                                                               |
| ------------------------------------ | ------------- | ------------------------------------------------------------------- |
| Windows 10/11                        | Microsoft     | Most widely used desktop OS; closed source; dominant in enterprise |
| Windows Server (2016/2019/2022/2025) | Microsoft     | Server variant; Active Directory, Hyper-V, IIS                      |
| macOS                                | Apple         | Unix-based (Darwin), closed source; runs only on Apple hardware     |
| Linux distributions                  | Various       | Open source                                                         |
| Chrome OS                            | Google        | Linux-based; cloud-centric; common in education                     |
| FreeBSD / OpenBSD / NetBSD           | BSD Community | Unix-like; strong security reputation                               |

#### Common Linux Distributions

- Debian-based: Ubuntu, Zorin, Kali Linux, Linux Mint
- Red Hat-based: RHEL, Fedora, Rocky Linux
- SUSE-based: SUSE Linux Enterprise, openSUSE
- Arch-based: Garuda OS, Arch Linux, BlackArch
- Others: Alpine (containers), Gentoo, Amazon Linux

---

## Reference

- [TryHackMe - Operating system introduction](https://tryhackme.com/room/operatingsystemsintroduction)


