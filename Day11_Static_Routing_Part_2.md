# 11. Static Routing: Part 2

## Quick Review: Layer 2 vs. Layer 3 Forwarding
* **Switches:** Forward traffic **within** a Local Area Network (LAN) using MAC addresses at Layer 2 (Data Link Layer).
* **Routers:** Forward traffic **between** different LANs or networks using IP addresses at Layer 3 (Network Layer).
* **WAN (Wide Area Network):** A telecommunications network that extends over a large geographic area to connect multiple LANs.

---

## Static Routes
A **static route** is a manually configured routing entry created by a network administrator. It tells the router explicitly how to reach a specific remote network.

### 1. Static Route Configuration with Next-Hop IP
The standard method of configuring a static route specifies the IP address of the neighboring router's interface (the next hop).

* **Command Syntax:**
  `Router(config)# ip route [destination_network] [subnet_mask] [next_hop_ip]`
* **Example:**
  `Router(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.2`
* **How it works:** The router looks up the destination network, sees the next-hop IP, and then performs a recursive lookup to figure out which physical exit interface leads to that next-hop IP.

### 2. Static Route Configuration with Exit-Interface
You can also configure a static route by pointing directly to the local router's outgoing interface instead of a next-hop IP address.

* **Command Syntax:**
  `Router(config)# ip route [destination_network] [subnet_mask] [exit_interface]`
* **Example:**
  `Router(config)# ip route 192.168.2.0 255.255.255.0 Serial0/0/0`
* **Use Case:** Commonly used on point-to-point serial links. However, on multi-access networks (like Ethernet), using exit-interfaces for static routes can cause issues with ARP resolution unless managed carefully, making next-hop IP configurations generally preferred.

---

## Default Route
A **default route** is a special type of static route that matches *any* destination network that is not explicitly listed in the routing table (often referred to as a gateway of last resort).

* **Command Syntax:**
  `Router(config)# ip route 0.0.0.0 0.0.0.0 [next_hop_ip | exit_interface]`
* **Example:**
  `Router(config)# ip route 0.0.0.0 0.0.0.0 10.0.0.1`
* **Why use it?** Stub routers (like a home router or a small branch office router connecting to an ISP) use a default route to forward all traffic heading toward the broader internet or corporate headquarters when no specific route exists.
