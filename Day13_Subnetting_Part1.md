# 13. Subnetting: Part 1

## The Evolution of IP Addressing
* **Classful Addressing:** Historically, IPv4 addresses were divided into Classes A, B, and C with fixed prefix lengths (`/8`, `/16`, and `/24` respectively) assigned by the IANA based on organizational size.
* **The Problem:** Classful allocation caused massive IP address wastefulness (e.g., a company needing 5,000 addresses was assigned a Class B network supporting over 65,000 addresses, leaving tens of thousands unused).
* **CIDR Introduction:** In 1993, the IETF introduced **CIDR (Classless Inter-Domain Routing)** to eliminate class restrictions, allowing networks to be split into smaller, highly efficient **subnets** (sub-networks).

---

## Calculating Usable Hosts
To find the number of assignable host addresses within a given subnet, use the formula:
`2^n - 2` *(where **n** equals the number of host bits)*
*Note: Two addresses are always reserved in every subnet and cannot be assigned to devices: the **Network ID** (first address) and the **Broadcast Address** (last address).*

---

## CIDR Practice Examples

### Example 1: `/25` Subnet
* **Target Prefix:** `/25` means the subnet prefix spans 25 bits.
* **Binary Representation (203.0.113.0 /25):**
  `1100 1011 . 0000 0000 . 0111 0001 . 0 | 000 0000`
* **Subnet Mask:** Flipping all 25 network bits to `1` gives `255.255.255.128` (since the last octet `1000 0000` equals 128).
* **Usable Hosts:** `2^7 - 2 = 126 usable hosts`.

### Example 2: `/28` Subnet
* **Target Prefix:** `/28` means the subnet prefix spans 28 bits.
* **Binary Representation (203.0.113.0 /28):**
  `1100 1011 . 0000 0000 . 0111 0001 . 0000 | 0000`
* **Subnet Mask:** `255.255.255.240` (since the last octet `1111 0000` equals 240).
* **Usable Hosts:** `2^4 - 2 = 14 usable hosts` (`16` total block size minus 2 reserved addresses).

---

## Subnetting Cheat Sheet & Reference Table

| Group Size | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Subnet Mask** | 128 | 192 | 224 | 240 | 248 | 252 | 254 | 255 |
| **CIDR (4th Octet)** | `/25` | `/26` | `/27` | `/28` | `/29` | `/30` | `/31` | `/32` |
| **CIDR (3rd Octet)** | `/17` | `/18` | `/19` | `/20` | `/21` | `/22` | `/23` | `/24` |
| **CIDR (2nd Octet)** | `/9` | `/10` | `/11` | `/12` | `/13` | `/14` | `/15` | `/16` |
| **CIDR (1st Octet)** | `/1` | `/2` | `/3` | `/4` | `/5` | `/6` | `/7` | `/8` |

---

## Step-by-Step Subnetting Method (Magic Octet Approach)

1. **Identify the Magic Octet:** Determine which octet the given IP and prefix fall into.
2. **Find Group Size:** Count the network bits inside that octet to find the group/block size.
3. **Calculate Subnet Mask:** Subtract the group size from 256 to get the value for the magic octet (`256 - Group Size`). Any octet to the left becomes `255`, and any octet to the right becomes `0`.
4. **Find Base Network Address:** Divide the target IP's octet value by the address group size. If there is a remainder, multiply the whole integer by the group size. If there is no remainder, that value is your base. Set all remaining right-side octets to `0`.
5. **Find Broadcast Address:** `Network Base Number + Group Size - 1` in the magic octet, with all subsequent right-side octets set to `255`.

### Complete Calculation Example 1
* **Target IP/Prefix:** `154.219.154.180 /20`
* **Magic Octet:** 3rd Octet (`/20` falls in the 3rd octet range).
* **Group Size:** 16 (4 network bits in the 3rd octet).
* **Subnet Mask:** `256 - 16 = 240` $\rightarrow$ `255.255.240.0`
* **Network Calculation:** `154 / 16 = 9` (with remainder). `9 * 16 = 144`.
* **Network ID:** `154.219.144.0`
* **Broadcast Address:** `144 + 16 - 1 = 159` $\rightarrow$ `154.219.159.255`
* **Subnets:** `2^4 = 16 subnets`
* **Total Host Size:** `(2^(32 - 20)) - 2 = 4094 usable hosts`

### Complete Calculation Example 2
* **Target IP/Prefix:** `84.75.21.6 /10`
* **Magic Octet:** 2nd Octet (`/10` falls in the 2nd octet range).
* **Group Size:** 64 (2 network bits in the 2nd octet).
* **Subnet Mask:** `256 - 64 = 192` $\rightarrow$ `255.192.0.0`
* **Network Calculation:** `75 / 64 = 1` (with remainder). `1 * 64 = 64`.
* **Network ID:** `84.64.0.0`
* **Broadcast Address:** `64 + 64 - 1 = 127` $\rightarrow$ `84.127.255.255`
* **Subnets:** `2^2 = 4 subnets`
* **Total Host Size:** `(2^(32 - 10)) - 2 = 4194302 usable hosts`
