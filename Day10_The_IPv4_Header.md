# CCNA Study Notes: The IPv4 Header

The IPv4 Header is a Layer 3 structure used to encapsulate TCP/UDP segments for routing across networks. The standard header length ranges from 20 to 60 bytes.

## Header Fields Breakdown

| Field | Bits | Description |
| :--- | :--- | :--- |
| **Version** | 4 | Identifies protocol version (IPv4 = 0100). |
| **IHL** | 4 | Internet Header Length (in 4-byte increments). Min: 5 (20 bytes), Max: 15 (60 bytes). |
| **DSCP** | 6 | Quality of Service (QoS); prioritizes delay-sensitive traffic (voice/video). |
| **ECN** | 2 | Explicit Congestion Notification; handles congestion without dropping packets. |
| **Total Length** | 16 | Total size of packet (Header + Segment) in bytes. Max: 65,535. |
| **Identification** | 16 | Unique ID for fragments of the same original packet. |
| **Flags** | 3 | Controls fragmentation: 1=Don't Fragment (DF), 2=More Fragments (MF). |
| **Fragment Offset**| 13 | Position of fragment in the original packet (helps in reassembly). |
| **TTL** | 8 | Time to Live; prevents routing loops by decreasing count by 1 at each router hop. |
| **Protocol** | 8 | Identifies the L4 protocol (1: ICMP, 6: TCP, 17: UDP, 89: OSPF). |
| **Header Checksum**| 16 | Validates the integrity of the **IPv4 Header only**. |
| **Source/Dest IP** | 32ea | IPv4 address of the sender and intended receiver. |
| **Options** | 0-320 | Optional/rarely used; if present, IHL > 5. |

---

## Key Concepts
*   **Routing:** The primary function of the IPv4 header is to facilitate the transfer of data between different networks.
*   **Fragmentation:** Occurs if a packet exceeds the MTU (Maximum Transmission Unit), typically **1500 bytes** on Ethernet. 
*   **Loop Prevention:** The **TTL** field acts as a "hop count." If a router receives a packet with a TTL of 0, it drops the packet.
*   **Error Detection:** The **Header Checksum** detects errors in the header. Error detection for the payload (data) is handled by the higher-layer protocols (TCP/UDP checksums).
