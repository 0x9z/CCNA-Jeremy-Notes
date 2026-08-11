# 11. Routing Fundamentals: Part 1

## What is Routing?
**Routing** is the Layer 3 (Network Layer) process used by routers to determine the optimal path for IP packets to take across a network to reach their destination.

---

## The Routing Table
Routers maintain a **Routing Table** (a database in RAM) to store known destinations and the associated paths. When a router receives an IP packet, it performs a lookup in this table to decide how to forward the packet.

### How a Route is Defined
A route informs the router of the path to take based on the destination:
*   **Next-Hop:** If the destination is remote, the router sends the packet to a "Next-Hop" IP address (the IP of the next router in the path).
*   **Directly Connected:** If the destination network is physically connected to an interface on the router, the router sends the packet directly to the destination host.
*   **Local Delivery:** If the destination IP address matches one of the router’s own interface addresses, the router processes the packet itself (the packet is not forwarded).

---

## Main Routing Methods
Routers learn paths to destinations using two primary methods:

### 1. Dynamic Routing
*   **Definition:** Routers use **Dynamic Routing Protocols** (e.g., OSPF, EIGRP, BGP) to automatically communicate with neighbor routers.
*   **Function:** They exchange information about known networks, allowing the routing table to update automatically if the network topology changes.
*   **Benefit:** Highly scalable and self-healing; ideal for large, complex networks.

### 2. Static Routing
*   **Definition:** A network administrator manually configures routes on the router.
*   **Function:** The route remains in the table until manually removed.
*   **Benefit:** Provides security and predictable traffic patterns; uses less bandwidth and CPU overhead than dynamic protocols. Suitable for stub networks or small, simple setups.

---

## Key Terminology
*   **WAN (Wide Area Network):** A network that spans a large geographic area, connecting smaller LANs (Local Area Networks) over long distances using service provider links.
*   **Administrative Distance (AD):** The measure of "trustworthiness" of a routing source. If a router learns about the same destination from two different protocols, it chooses the one with the lower AD.
