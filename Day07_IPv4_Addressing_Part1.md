# CCNA Study Notes: IPv4 Addressing (Part 1)

## 1. Network Layer Fundamentals (Layer 3)
*   **Purpose:** Provides logical addressing (IPs), path selection, and connectivity between different networks.
*   **Devices:** Routers operate at Layer 3; Switches (Layer 2) connect devices within the same LAN.
*   **Routing:** Routers connect different networks. Each interface on a router requires a unique IP address based on the network it connects to.
*   **Broadcasts:** Routers **do not** forward broadcasts; they stay within the local LAN.

## 2. Binary, Decimal, and Hex Conversion
IPv4 addresses are 32-bit values divided into four 8-bit **octets**.

### Binary to Decimal
*   **Method:** Assign powers of 2 to each bit position (128, 64, 32, 16, 8, 4, 2, 1).
*   **Example (10001111):** 128 + 8 + 4 + 2 + 1 = **143**

### Decimal to Binary
*   **Method:** Subtract the largest possible value (starting from 128) from your number, placing a "1" in that slot if it fits, and "0" if it doesn't.
*   **Example (221):** 128(1) + 64(1) + 32(0) + 16(1) + 8(1) + 4(1) + 2(0) + 1(1) = **11011101**

## 3. IPv4 Address Classes
Class is determined by the **first octet**:

| Class | Range | Usage |
| :--- | :--- | :--- |
| **A** | 0–126 | Large networks |
| **B** | 128–191 | Medium networks |
| **C** | 192–223 | Small networks |
| **D** | 224–239 | Multicast |
| **E** | 240–255 | Experimental |

*   **Note:** 127.x.x.x is reserved for **Loopback** (testing the local network stack).

## 4. Subnetting & Addressing
*   **Prefix Length (/x):** Indicates the number of bits in the **Network Portion**.
*   **Netmask:** A dotted-decimal representation of the prefix.
    *   `/8` = 255.0.0.0 (Class A)
    *   `/16` = 255.255.0.0 (Class B)
    *   `/24` = 255.255.255.0 (Class C)

### Reserved Addresses
*   **Network Address:** All host bits are **0**. (The network identifier; cannot be assigned to a host).
*   **Broadcast Address:** All host bits are **1**. (Used to reach all hosts in the network; cannot be assigned to a host).
*   **Usable Range:** Always `Network Address + 1` to `Broadcast Address - 1`.
