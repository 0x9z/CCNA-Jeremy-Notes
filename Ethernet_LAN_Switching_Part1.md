# 5. Ethernet LAN Switching: Part 1

This guide covers the fundamental concepts of Local Area Networks (LANs) and the structure of Ethernet frames as part of CCNA exam preparation.

---

## LANs (Local Area Networks)

* **Definition:** A network contained within a relatively small area.
* **Connectivity:** Routers are required to connect separate LANs.

---

## The Ethernet Frame

Think of an Ethernet frame as the vessel for your data. Its total header and trailer size is 26 bytes.

### Frame Structure
`[Ethernet Header] --- [PACKET] --- [Ethernet Trailer]`

### Ethernet Header (5 Fields)

| Field | Length | Description |
| :--- | :--- | :--- |
| **Preamble** | 7 bytes | 56 bits of alternating 1s and 0s (10101010) used to synchronize receiver clocks. |
| **SFD** | 1 byte | "Start Frame Delimiter" (10101011); marks the end of the preamble and start of the frame. |
| **Destination** | 6 bytes | The MAC address of the receiving device. |
| **Source** | 6 bytes | The MAC address of the sending device. |
| **Type/Length**| 2 bytes | Identifies the protocol or packet length. |

#### Understanding the Type/Length Field:
* **Value <= 1500:** Indicates the **LENGTH** of the encapsulated packet.
* **Value >= 1536:** Indicates the **TYPE** of the encapsulated packet (protocol used).
    * **IPv4:** `0x0800` (2048)
    * **IPv6:** `0x86DD` (34525)

---

## Ethernet Trailer

* **FCS (Frame Check Sequence):** 4 bytes used to detect corrupted data.
* **CRC (Cyclic Redundancy Check):** The algorithm run over the data to verify integrity.

---

## MAC Address (Media Access Control)

A 48-bit (6-byte) physical address assigned to a device during manufacturing.

* **AKA:** Burned-In Address (BIA).
* **Properties:** Globally unique.
* **Structure (12 Hex Characters):**
    * **OUI (First 3 bytes):** Assigned to the vendor/company.
    * **Unique Device ID (Last 3 bytes):** Specific to the device.
* **Example:** `E8:BA:70 : 11:28:74` (OUI : Unique ID)

---

## Switch Operation

### Interface Naming
* **F0/1, F0/2, etc.**
* **F:** Fast Ethernet (100 Mbps).

### MAC Address Table
Switches maintain a dynamically learned table based on the **Source MAC Address** of incoming frames.

1. **Unknown Unicast:** If the destination MAC is unknown, the switch **FLOODS** the frame out of all ports (except the incoming port).
2. **Known Unicast:** If the MAC is in the table, the switch **FORWARDS** the frame to the specific destination port.
3. **Table Maintenance:** Dynamic entries are purged after **5 minutes of inactivity**.
