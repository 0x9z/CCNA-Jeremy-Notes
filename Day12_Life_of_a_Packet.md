# 12. Life of a Packet

## MAC Addresses and Header Structures
* **Unique Identification:** Each network device interface has a globally unique MAC (Media Access Control) address operating at Layer 2 (Data Link Layer).
* **TCP Header Order:** In a TCP header, the **Source IP Address** comes before the **Destination IP Address**.
* **Ethernet Header Order:** In an Ethernet header, the order is reversed—the **Destination MAC Address** comes before the **Source MAC Address**.

---

## Packet Journey Across a Network
* **End-to-End IP Stability:** When a host sends a packet to another host across a network, the **Source IP** and **Destination IP addresses remain completely unchanged** from the original sender to the final destination.
* **Layer 2 Rewriting at Routers:** Even though the IP addresses stay the same, intermediate **routers strip off the old Ethernet header and create a brand-new one** on each hop. This means the **Source and Destination MAC addresses change** at every single router hop along the path.
