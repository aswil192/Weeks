
## 1. Define basic computer components: CPU, memory, storage.

#### i. CPU

The CPU is the "brain" of the computer. It executes instructions and performs calculations. It fetches instructions from memory, decodes them, and carries out operations involving arithmetic, logic, and control.

- Cores: Modern CPUs have multiple cores, allowing parallel processing.
- Clock speed: Measured in GHz; indicates how many cycles per second it can process.
- Cache: Small, fast memory on the CPU for frequently used data.
- Examples: Intel Core i7, AMD Ryzen 5, and Apple M-series chips.

#### ii. Memory (RAM)

Memory is volatile, short-term working storage that holds data and instructions currently in use by the CPU. It's fast but loses its contents when power is off.

- Purpose: Lets the CPU quickly access active programs and data without waiting on slower storage.
- Characteristics: Measured in GB; higher capacity allows more programs to be open simultaneously.
- Types: DDR4 and DDR5 are common standards.

#### iii. Storage

Storage is non-volatile, long-term storage that retains data without power. It holds the operating system, applications, and files.

1. Types of storage:
	- HDD: Magnetic spinning disks; cheaper, larger capacity, slower.
	- SSD: Flash-based; much faster, more durable, and more expensive per GB.
	- NVMe SSDs: Fastest, connected directly via PCIe.
	
2. Storage is measured in GB and TB.

---

## 2. Understand what software and hardware are & how they work together

#### i. Hardware

Hardware is the physical, tangible part of a computer: the components you can touch. It is the machinery that executes instructions.

- Examples: CPU, RAM, motherboard, hard drive/SSD, monitor, keyboard, mouse, GPU, and PSU.
- Key trait: Physical; it can wear out, break, or be replaced.
- Role: Provides the raw capabilities for processing, storing, displaying, and input/output.

#### ii. Software

Software is the intangible set of instructions, programs, and data that tell the hardware what to do. You cannot touch it, but it controls the hardware.

- Examples: Operating systems (Windows, Linux), applications (browsers and games), drivers, and firmware.
- Key trait: Logical; it's code and data stored on hardware but distinct from it.
- Role: Directs and coordinates hardware to perform useful tasks.

1. System software
	- Runs the machine and provides a platform (the OS and Device drivers)
	
2. Application Software
	- Performs user-facing tasks (Web Browsers, spreadsheets, games)

#### iii. How Software and Hardware work together

Hardware and software are interdependent; neither is useful alone:

- Hardware without software is like a car with no driver: capable but inert.
- Software without hardware is like instructions with nothing to carry them out: it can't run.

The operating system acts as the bridge, managing hardware resources and providing services to applications. When you click a button, the software (Application -> OS -> Driver) translates that action into signals the hardware executes.

---

## 3. Explain binary data and how computers store information

#### i. Binary Data

Binary is a base-2 number system that uses only two digits: 0 and 1. Every piece of information in a computer, including text, images, sound, videos, and programs, is ultimately represented as patterns of these two values.

The reason computers use binary is physical: electronic circuits are most reliable when distinguishing between just two states, such as:
- Voltage high vs low
- switch on vs off
- Magnetized vs. not magnetized (in storage)

A single 0 or 1 is called a bit (short for binary digit). A group of 8 bits is a byte, which can represent 256 different values (2^8).

#### ii. How computers physically store Bits

| Storage Type     | How a bit is Represented                                     |
| ---------------- | ------------------------------------------------------------ |
| RAM              | Tiny capacitors holding charge (charged = 1, discharged = 0) |
| SSD (flash)      | Trapped electrons in floating-gate transistors               |
| HDD (magnetic)   | Magnetized domains on a spinning disk                        |
| Optical (CD/DVD) | Pits and lands reflecting laser light                        |
| CPU registers    | Flip-flop circuits (transistor states)                       |
#### iii. How it works

The power of binary is that everything reduces to the same simple representation. A computer does not use separate hardware for text, images, and sound; it simply processes bits. Software layers (operating systems, codecs, and file formats) interpret those bits differently.
```
Bits → Bytes → Data structures → Files → Applications
```

---

## Reference

- [TryHackMe - Data Representation](https://tryhackme.com/room/datarepresentation)
- [TryHackMe - Data Encoding](https://tryhackme.com/room/dataencoding)
- [YouTube - CPU, RAM, storage, and boot process](https://youtu.be/o5UywekZ39k)
- [YouTube - How data is stored inside a computer](https://youtu.be/cbaocBxuIOo)




