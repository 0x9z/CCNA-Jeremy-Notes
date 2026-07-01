# 6. Ethernet LAN Switching: Part 2

This guide continues from Part 1, focusing on frame sizing, the Address Resolution Protocol (ARP), and ICMP (Ping) utilities.

---

## Ethernet Frame Sizing & Padding

While the total Ethernet frame structure includes the Preamble and SFD for synchronization, the actual **Header + Trailer** size for switching and routing purposes is **18 bytes**.

* **Header (14 bytes):** Dest MAC (6) + Source MAC (6) + Type/Length (2).
* **Trailer (4 bytes):** FCS (Frame Check Sequence).

### Minimum Frame Size
To ensure reliable collision detection in older Ethernet technologies, there is a minimum frame size:
* **Minimum Ethernet Frame:** 64 bytes.
* **Calculation:** 64 bytes - 18 bytes (Header/Trailer) = **46 bytes for the Data Payload**.

**Padding:** If the actual packet (payload) is smaller than 46 bytes, the switch adds **Padding Bytes** (a series of 0s) to the frame to reach the 46-byte minimum requirement.

---

## ARP (Address Resolution Protocol)

When a PC knows a destination's **IP Address** (Layer 3) but needs to find its **MAC Address** (Layer 2) to build a frame, it uses ARP.

### The ARP Process
1.  **ARP Request (Broadcast):** The source sends a broadcast (`FFFF.FFFF.FFFF`) to all hosts on the local network. It asks, "Who has this IP address? Tell me your MAC."
2.  **ARP Reply (Unicast):** The host with the matching IP address sends a direct reply back to the source containing its MAC address.

| ARP Message | Destination Type | Content |
| :--- | :--- | :--- |
| **Request** | Broadcast | Source IP, Dest IP, Source MAC, Broadcast MAC (`FFFF.FFFF.FFFF`) |
| **Reply** | Unicast | Source IP, Dest IP, Source MAC, Destination MAC |

---

## Testing Connectivity: Ping

**Ping** is a utility used to verify reachability between two devices. It uses **ICMP** (Internet Control Message Protocol).

* **Mechanism:** It sends an **ICMP Echo Request** and listens for an **ICMP Echo Reply**.
* **Communication:** This is **Unicast**.
* **Cisco IOS Defaults:**
    * Sends 5 Echo Requests.
    * Default packet size: 100 bytes.
* **Output Symbols:**
    * `!`: Successful Ping.
    * `.`: Failed Ping (Request timed out).

---

## Useful Cisco IOS Commands

| Command | Description |
| :--- | :--- |
| `show arp` | Displays the device's ARP table. |
| `show mac address-table` | Displays the switch's MAC address table (VLAN, MAC, Type, Interface). |
| `clear mac address-table dynamic` | Clears all dynamic entries from the MAC table. |
| `clear mac address-table dynamic interface <ID>` | Clears MAC table entries for a specific interface. |
