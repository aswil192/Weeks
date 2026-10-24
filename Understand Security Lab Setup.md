## 1. Virtualization Concepts

**Virtualization** is the process of creating a software-based (virtual) representation of computing resources, such as servers, storage, networks, or operating systems. It abstracts the physical hardware, allowing multiple isolated environments to run simultaneously on a single physical machine.

>**Hypervisor:** The software that creates and the virtualization is called a hypervisor. It allocates and controls the sharing of a machine's resources
>
>- Disk
>- Memory
>- CPU Cores

###  i. Type 1 Hypervisor (Bare Metal)

Type 1 hypervisor runs directly on the physical hardware of the host machine without needing an underlying operating system. It is also knows an **bare-metal hypervisor**

>**Example:** VMware ESXi, Microsoft Hyper-V, Citrix XenServer

### ii. Type 2 Hypervisor (Hosted)

Type 2 hypervisor runs on top of an existing operating system (OS) on the host machine, It is also called a **Hosted Hypervisor** 

>**Example:** Oracle VirtualBox, VMware Workstation, Microsoft Virtual PC 

---

## 2. Virtual Machines

A **Virtual Machine (VM)** is a software emulation of a physical computer. It runs its own operating system and applications, behaving exactly like a separate physical machine, but it relies on the host system's physical resources (CPU, memory, storage) managed by a hypervisor.

> **Example:** Using software like VirtualBox or VMware on your Windows laptop to run a completely separate installation of Kali Linux in a window, allowing you to practice hacking tools without affecting your main Windows OS.

---

## 3. Isolated Lab Environments

**Isolated lab environments** are controlled, segregated network and computing setups used for testing, development, or training. They are intentionally disconnected from production networks and the public internet to prevent accidental damage, malware spread, or unauthorized access during experiments.

---

## 4. Snapshot Management

**Snapshot management** is the practice of capturing the exact state of a virtual machine or system at a specific point in time. This allows administrators to quickly revert the system back to a previous, known-good state if an update, configuration change, or test causes a failure.

---

## 5. Safe Security Testing Practices

**Safe security testing practices** involve conducting vulnerability assessments, penetration tests, or malware analysis in a controlled and ethical manner. This includes using isolated environments, obtaining proper legal authorization, and ensuring that testing activities do not disrupt production systems or compromise data integrity.

---

## Reference

- [TryHackMe - Virtualisation Basics](https://tryhackme.com/room/virtualisationbasics)
- [Virtualization explained in Malayalam | Fetlla | Malayalam Explanation](https://www.youtube.com/watch?v=B4f-BkAFTc0)
- [TryHackMe - Virtualization and Containers](https://tryhackme.com/room/virtualizationandcontainers)