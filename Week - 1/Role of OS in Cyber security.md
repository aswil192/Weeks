## 1 & 2. Write how the OS helps protect data and system resources & Identify OS security features like authentication, permissions, and logging.

The operating system (OS) acts as a trusted intermediary between users, applications, and hardware, enforcing protection through several complementary mechanisms.

1. Process and Memory Isolation
	- Separate address spaces: Each process gets its own virtual address space, so one program cannot read or write another's memory. The Memory Management Unit (MMU) translates virtual to physical addresses and enforces boundaries in hardware.
	- Kernel/user mode separation: The CPU runs in privileged (kernel) mode only for OS code; user applications run in restricted mode and must request services through system calls, which the OS validates.
	- Non-executable and read-only regions: Pages can be marked non-executable (NX bit) or read-only, blocking code injection and self-modifying attacks.
	
2. Access Control and Authentication
	- User authentication: Login credentials, tokens, or biometrics establish identity before any resources are granted.
	- File permissions and ACLs: Ownership and permission bits (read/write/execute for owner, group, others) plus access control lists restrict who can access which files.
	- Principle of least privilege: Users and processes receive only the rights they need; privilege escalation requires explicit authorization.
	
3. Resource Scheduling and Limits
	- CPU scheduling: The scheduler allocates time slices, preventing any single process from monopolising the processor.
	- Quotas and limits: The OS can cap memory, CPU time, disk usage, and open files per user or process, preventing resource exhaustion and denial of service.
	- Fair allocation: Memory and I/O are managed centrally so a misbehaving program cannot starve others.
	
4. File System Protection
	- Controlled access path: All file operations go through the kernel, which checks permissions on every open, read, write, and delete.
	- Journaling and consistency: Metadata logging and file system checks protect data integrity after crashes.
	- Backup and recovery support: Snapshots, versioning and recovery tools help restore data after corruption or attack.
	
5.  Memory Safety and Integrity Features
	- Address space layout randomization: Randomizes memory layout to make exploitation harder.
	- Stack canaries, DEP, and W^X: Compiler/OS cooperation detects buffer overflows and prevents writable-executable memory.
	- Secure Boot and code signing ensure that trusted code runs at startup and that kernel modules are authenticated.
	
6. Auditing and Monitoring
	- Logging: The OS records logins, privilege changes and access attempts, enabling detection of misuse.
	- Audit trails: System call auditing and file-access monitoring provide accountability and forensic evidence.

---

## 3. Give examples of OS security incidents and responses.

#### Windows / Active Directory: Kerberoasting & Ransomware (2024)

**Incident:** In the 2024 Ascension healthcare ransomware attack, hackers exploited Kerberoasting to crack privileged Active Directory passwords. Windows retained outdated RC4 encryption by default and did not require long passwords (14+) for service accounts, making the passwords easy to crack once initial access was gained via a malicious Bing search.

**Response:** After pressure from Senate oversight, Microsoft published guidance on Kerberoasting defenses and announced a software update to disable RC4 by default.

**Lesson:** Insecure default settings in authentication protocols can undermine the entire permission model.

#### Microsoft Exchange Server: ProxyLogon (2021)

**Incident:** Critical zero-day vulnerabilities in on-premises Exchange servers allowed unauthenticated attackers to execute arbitrary code, install web shells, and steal credentials and mailboxes. State-sponsored groups and multiple criminal actors widely exploited these vulnerabilities.

**Response:** Microsoft rushed emergency patches, released a one-click mitigation tool for organizations without dedicated security teams, and published scripts to scan for indicators of compromise. The company also introduced the Emergency Mitigation service (EEMS) to automatically apply interim defenses for future high-risk flaws.

#### WannaCry Ransomware: Unpatched SMB (2017)

**Incident:** WannaCry exploited the EternalBlue SMB vulnerability (MS17-010) to spread rapidly across unpatched Windows systems, encrypting files and crippling hospitals and businesses around the world.

**Response:** Microsoft took the unprecedented step of releasing security patches for unsupported OS versions (Windows XP, Windows 8, Server 2003).
Administrators were urged to disable the legacy SMBv1 protocol, block port 445 at firewalls, and rely on offline backups. This incident highlighted the severe risk of unpatched legacy code running with high system privileges.

---

## Reference

- [TryHackMe - Operating System Security](https://tryhackme.com/room/operatingsystemsecurity)
- [YouTube - Operating System Security](https://www.youtube.com/watch?v=07BFhXIpWmA)








