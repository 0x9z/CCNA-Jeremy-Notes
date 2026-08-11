# 15. Subnetting (VLSM): Part 3

## Subnetting Class A Networks
* **Example:** Given a `10.0.0.0 /8` network, create 2000 subnets for various enterprises.
* **Calculating Subnet Bits:** 
  * `2^10 = 1024` (too small)
  * `2^11 = 2048` (enough to cover 2000 subnets) $\rightarrow$ We must borrow **11 bits** from left to right.
* **Prefix Length:** `/8` (original class) + `/11` (borrowed bits) = `/19`
* **Subnet Mask:** `255.255.224.0`
* **Hosts Per Subnet:** 13 host bits remaining ($32 - 19 = 13$). Formula: `2^13 - 2 = 8190 usable hosts per subnet`.

---

## Variable-Length Subnet Masks (VLSM)
* **FLSM vs. VLSM:** FLSM (Fixed-Length Subnet Masks) uses the exact same prefix length for all subnets. **VLSM** allows you to create subnets of **different sizes** to maximize IP address efficiency.
* **Golden Rule for VLSM:** Always start by subnetting for the **largest required host count first**, then work your way down to the smallest networks (such as point-to-point links).

---

## VLSM Practical Exercise Example
**Base Network:** `192.168.1.0 /24`
**Requirements:**
1. Tokyo LAN A (110 hosts)
2. Toronto LAN B (45 hosts)
3. Toronto LAN A (29 hosts)
4. Tokyo LAN B (8 hosts)
5. Point-to-Point Connection (2 router interfaces = needs 2 usable hosts)

### Step 1: Tokyo LAN A (Needs 110 Hosts)
* **Requirement:** Requires at least 110 usable hosts. `2^7 - 2 = 126` hosts, so we use a `/25` prefix (borrowing 1 host bit).
* **Network Address:** `192.168.1.0 /25`
* **First Usable:** `192.168.1.1 /25`
* **Last Usable:** `192.168.1.126 /25`
* **Broadcast Address:** `192.168.1.127 /25`

### Step 2: Toronto LAN B (Needs 45 Hosts)
* **Requirement:** Requires at least 45 hosts. `2^6 - 2 = 62` hosts, so we use a `/26` prefix.
* **Network Address:** `192.168.1.128 /26`
* **First Usable:** `192.168.1.129 /26`
* **Last Usable:** `192.168.1.190 /26`
* **Broadcast Address:** `192.168.1.191 /26`

### Step 3: Toronto LAN A (Needs 29 Hosts)
* **Requirement:** Requires at least 29 hosts. `2^5 - 2 = 30` hosts, so we use a `/27` prefix.
* **Network Address:** `192.168.1.192 /27`
* **First Usable:** `192.168.1.193 /27`
* **Last Usable:** `192.168.1.222 /27`
* **Broadcast Address:** `192.168.1.223 /27`

### Step 4: Tokyo LAN B (Needs 8 Hosts)
* **Requirement:** Requires at least 8 hosts. `2^4 - 2 = 14` hosts, so we use a `/28` prefix.
* **Network Address:** `192.168.1.224 /28`
* **First Usable:** `192.168.1.225 /28`
* **Last Usable:** `192.168.1.238 /28`
* **Broadcast Address:** `192.168.1.239 /28`

### Step 5: Point-to-Point Connection (Needs 2 Hosts)
* **Requirement:** Requires 2 usable hosts for router interfaces. `2^2 - 2 = 2` hosts, so we use a `/30` prefix.
* **Network Address:** `192.168.1.240 /30`
* **First Usable:** `192.168.1.241 /30`
* **Last Usable:** `192.168.1.242 /30`
* **Broadcast Address:** `192.168.1.243 /30`

---

## Recommended Subnetting Practice Sites
* `http://www.subnettingquestions.com`
* `http://subnetting.org`
* `https://subnettingpractice.com` *(Preferred site)*
