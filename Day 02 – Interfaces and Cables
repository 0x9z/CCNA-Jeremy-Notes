# Day 02 – Interfaces and Cables

## What Are Interfaces?

Interfaces are the **ports** on a device where you plug in cables.

A switch usually has **24 ports** (or more). These are called **RJ-45 ports** — the same shape you see on the back of your computer.

---

## What Is Ethernet?

Ethernet is a **collection of standards** that everyone agrees on so devices can talk to each other.

Think of it like a language. If you speak English and I speak Japanese, we can't communicate. Ethernet gives everyone a common language.

---

## Speed Measurement

Network speed is measured in **bits per second** (bps), not bytes.

| Size | How many bits |
|------|---------------|
| 1 kilobit (Kb) | 1,000 bits |
| 1 megabit (Mb) | 1,000,000 bits |
| 1 gigabit (Gb) | 1,000,000,000 bits |
| 1 terabit (Tb) | 1,000,000,000,000 bits |

> Quick tip: A byte = 8 bits. So a Gigabyte is 8 times bigger than a Gigabit.

---

## Copper Cable Standards (UTP)

UTP stands for **Unshielded Twisted Pair**. It's the normal copper cable with 8 wires twisted into 4 pairs.

| Speed | Common Name | Standard | Max Distance |
|-------|-------------|----------|--------------|
| 10 Mbps | Ethernet | 10BASE-T | 100 meters |
| 100 Mbps | Fast Ethernet | 100BASE-T | 100 meters |
| 1 Gbps | Gigabit Ethernet | 1000BASE-T | 100 meters |
| 10 Gbps | 10 Gigabit Ethernet | 10GBASE-T | 100 meters |

**BASE** = Baseband signaling (don't worry about it)  
**T** = Twisted pair

All copper cables have a **maximum length of 100 meters**.

---

## How Devices Send and Receive Data (10/100 Mbps)

With 10BASE-T and 100BASE-T, only **2 pairs (4 wires)** are used.

**PCs and Routers:**
- Transmit (send) on pins 1 and 2
- Receive on pins 3 and 6

**Switches (opposite):**
- Receive on pins 1 and 2
- Transmit (send) on pins 3 and 6

This is called **Full-Duplex** — both devices can send data at the same time with no collisions.

---

## Straight-Through vs. Crossover Cable

**Straight-Through Cable:**
- Pin 1 goes to Pin 1, Pin 2 to Pin 2, etc.
- Used for: PC to Switch, Router to Switch

**Crossover Cable:**
- Pins are reversed (Pin 1 to Pin 3, Pin 2 to Pin 6)
- Used for: same type devices (Switch to Switch, Router to Router, PC to PC)

> Good news: Most modern devices have **Auto MDI-X**. This means they automatically figure out the correct pins to use. You don't really need to worry about crossover cables anymore.

---

## Gigabit and 10-Gigabit (1000BASE-T / 10GBASE-T)

These use **all 4 pairs (8 wires)**.

Each pair is **bidirectional** — it can send and receive at the same time. That's why they're faster.

---

## Fiber-Optic Cables

For longer distances, we use fiber-optic cables. They send **light** through glass fibers instead of electricity through copper.

You need **SFP transceivers** (small pluggable modules) to connect fiber cables to switches or routers.

Fiber uses **two separate cables** — one to transmit, one to receive.

---

### Two Types of Fiber

**Multimode Fiber:**
- Wider core
- Light enters at multiple angles
- Cheaper (uses LED-based transmitters)
- Longer than copper (up to 400m or more)
- But shorter than single-mode

**Single-Mode Fiber:**
- Narrower core
- Light enters at a single angle (laser)
- More expensive (laser transmitters)
- Much longer distances (kilometers)

---

### Fiber Standards

| Standard | Speed | Mode | Max Distance |
|----------|-------|------|--------------|
| 1000BASE-LX | 1 Gbps | Multi or Single | 550m (Multi) / 5km (Single) |
| 10GBASE-SR | 10 Gbps | Multimode | 400 meters |
| 10GBASE-LR | 10 Gbps | Single-mode | 10 kilometers |
| 10GBASE-ER | 10 Gbps | Single-mode | 30 kilometers |

---

## UTP vs. Fiber — Quick Comparison

**UTP (Copper):**
- Cheaper
- Max 100 meters
- Can be affected by electrical interference (EMI)
- RJ-45 ports are cheap
- Leaks faint signal (security risk)

**Fiber-Optic:**
- More expensive
- Much longer distances
- No EMI interference
- SFP ports are more expensive
- No signal leak (more secure)

---

## Quick Self-Check

| If you want to... | You need a... |
|-------------------|----------------|
| Connect 30 computers in one office | UTP cable |
| Connect two buildings 150 meters apart | Multimode fiber |
| Connect two buildings 3 kilometers apart | Single-mode fiber |
| Connect a PC to a switch | Straight-through cable |
| Connect two old routers (no Auto MDI-X) | Crossover cable |
