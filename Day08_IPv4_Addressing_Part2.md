# CCNA Study Notes: IPv4 Addressing & Interface Management

## 1. IPv4 Host Calculations
To calculate the number of available hosts, use the number of host bits ($N$):

*   **Formula:** $2^N - 2$
    *   **$-2$** accounts for the reserved **Network ID** (first address) and **Broadcast Address** (last address).

### Capacity by Class
| Class | Host Bits ($N$) | Calculation | Max Hosts |
| :--- | :--- | :--- | :--- |
| **C (/24)** | 8 | $2^8 - 2$ | 254 |
| **B (/16)** | 16 | $2^{16} - 2$ | 65,534 |
| **A (/8)** | 24 | $2^{24} - 2$ | 16,777,214 |

*   **First Usable Address:** Network ID + 1
*   **Last Usable Address:** Broadcast Address - 1

---

## 2. Cisco CLI: Interface Management
### Status Codes
*   **Status (Layer 1):** Physical state.
    *   *Administratively down* = `shutdown` command was used.
    *   *Note:* Routers default to `shutdown`; Switches default to `no shutdown`.
*   **Protocol (Layer 2):** Data link state. Requires Layer 1 to be "up".

### Essential Configuration Workflow
```bash
R1> enable                      # Enter Privileged EXEC mode
R1# conf t                      # Enter Global Config mode
R1(config)# int g0/0            # Select interface
R1(config-if)# ip address 10.x.x.x 255.x.x.x
R1(config-if)# no shutdown      # Enable the interface
R1(config-if)# do show ip int brief # Verify status (using 'do' to run from config mode)

```

## Useful Show Commands
*   **`show ip interface brief`**: Summary of interface IP, Status, and Protocol.
*   **`show interfaces`**: Detailed L1/L2 info (MAC address, IP, error counters).
*   **`show interfaces description`**: View custom labels for ports.
*   **`description [text]`**: Best practice to label ports for network topology documentation.

---

## 3. Speed, Duplex, & Troubleshooting
Interfaces use **Auto-negotiation** to agree on speed and duplex. If auto-negotiation is disabled on one side:

### Default Fallback Rules
*   **Speed:** Switch defaults to the slowest supported speed (10 Mbps).
*   **Duplex (10/100 Mbps):** Defaults to **Half-Duplex**.
*   **Duplex (1000 Mbps+):** Defaults to **Full-Duplex**.

### Interface Error Counters (`show interfaces`)
If you see these errors at the bottom of the `show interfaces` output, check your cabling and duplex settings:

| Term | Meaning | Likely Cause |
| :--- | :--- | :--- |
| **Runts** | Frames too small (<64 bytes) | Duplex Mismatch / Bad Cable |
| **Giants** | Frames too large (>1518 bytes) | MTU Mismatch |
| **CRC** | Corrupted data (failed check) | Electrical interference / Bad Cable |
| **Input/Output Errors** | Total failures while processing | Congestion / Port Errors |
