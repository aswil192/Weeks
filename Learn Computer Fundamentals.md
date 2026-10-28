
## 1. Define basic computer components: CPU, memory, storage.

#### i. CPU

The CPU is the "brain" of the computer - it executes instructions and performs calculations. It fetches instructions from memory, decodes them, and carries out the operations (arithmetic, logic, control).

- Cores: Modern CPU have multiple cores, allowing parallel processing.
- Clock speed: Measured in GHz; indicates how many cycles per second it can process.
- Cache: Small, fast memory on the CPU for frequently used data.
- Examples: Intel core i7, AMD Ryzen 5, Apple M-series chips.

#### ii. Memory (Ram)

Memory is volatile, short-term working storage that holds data and instructions currently in use by the CPU. It's fast but loses its contents when power is off.

- Purpose: Lets the CPU quickly access active programs and data without waiting on slower storage.
- Characteristics: Measure in GB; higher capacity allows more programs open simultaneously.
- Types: DDR4/DDR5 are common standards 

#### iii. Storage 

Storage is non-volatile, long term storage that retains data without power. It holds the operating system, applications and files.

1. Types of storage: 
	- HDD: Magnetic spinning disks; cheaper, larger capacity, slower.
	- SSD: Flash-based; much faster, more durable, more expensive per GB
	- NVMe SSDs: Fastest, connected directly via PCIe.
	
2.  Measured in GB and TB.

---

## 2. Understand what software and hardware are & how they work together

#### i. Hardware

Hardware id the physical, tangible part of a computer - the components you can touch. It's the machinery that executes instructions.

- Examples: CPU, RAM, motherboard, hard drive/SSD, monitor, keyboard, mouse, GPU, PSU
- Key trait: Physical; it can wear out, break, or be replaced.
- Role: Provides thr raw capability - processinf, storing, displayonf, and input/output.

#### ii. Software

software is the intangible set of instructions, programs, and data that tell the hardware what to do. You can't touch it, but it controls the hardware.

- Examples: Operating system (Windows,Linux), applications (Browsers, games), drivers and firmware
- Key trait: Logical; it's code and data stored on hardware but distinct from it.
- Role: Directs and coordinates hardware to perform useful tasks.

1. System software
	- Runs the machine and provides a platform (the OS and Device drivers)
	
2. Application Software
	- Performs user-facing tasks (Web Browsers, spreadsheets, games)

#### iii. How Software and Hardware work together

Hardware and software interdependent - neither is useful alone: 

- Hardware without software is like a car with no driver: capable but inert.
- Software without hardware is like instructions with nothing to carry them out: it can't run.

The operating system acts as the bridge, managing hardware resources and providing services to applications. When you click a button, the software (Application -> OS -> Driver) translates that action into signals the hardware executes.

---

## 3. Explain binary data and how computers store information

#### i. Binary Data

Binary is a base-2 number system that uses only two digits: 0 and 1. Every piece of information in a computer - text, images, sound, videos, programs - is ultimately represented as patterns of these tow values.

The reason why computer use binary is physical: electronic circuits are most reliable when distinguishing between just two states, such as: 
- Voltage high vs low
- switch on vs off
- Magnetised vs not magnetised (in storrage)

A single 0 or 1 is called a bit (short for binary digit). A group of 8 bits is a byte, which can represent 256 different values (2^8) 

#### ii. How computers physically store Bits

| Storage Type     | How a bit is Represented                                     |
| ---------------- | ------------------------------------------------------------ |
| Ram              | Tiny capacitors holding charge (charged = 1, discharged = 0) |
| SSD (flash)      | Trapped electrons in floating-gate transistors               |
| HDD (Magnetic)   | Magnetised domains on a spinning disk                        |
| Optical (CD/DVD) | Pits and lands reflecting laser light                        |
| CPU Registers    | Flip=flop circuits (Transistor states)                       |
#### iii. How it works

The power of binary is that everything reduces to the same simple representation. A computer doesn't separate hardware hardware for text, images and sound - it just process bits. software layers (operating systems, codecs, file formats) interpret those bits differently
```
Bits → Bytes → Data structures → Files → Applications
```

---

## Reference

- [TryHackMe - Data Representation](https://tryhackme.com/room/datarepresentation)
- [TryHackMe - Data Encoding](https://tryhackme.com/room/dataencoding)
- [Youtube - CPU,Ram, Storage and boot process](https://youtu.be/o5UywekZ39k)
- [Youtube - How data is stored inside a computer](https://youtu.be/cbaocBxuIOo)




