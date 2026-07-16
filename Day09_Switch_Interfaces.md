# CCNA Study Notes: Switch Interfaces

## 1. Switch Management & Configuration
Unlike Routers, Switch interfaces are **not** `shutdown` by default. Unconnected ports will show as `down/down`.

### Essential Show Commands
*   **`show ip interface brief`**: Summary of status and protocol for all interfaces.
*   **`show interfaces status`**: Detailed view including Port, Name (Description), Status, VLAN, Duplex, Speed, and Type.

### Configuration for Multiple Ports
To improve security, deactivate unused interfaces using the `interface range` command:
```bash
SW1(config)# interface range f0/5 - 12
SW1(config-if-range)# description ## not in use ##
SW1(config-if-range)# shutdown
SW1(config-if-range)# do show interface status

```

### Interface Error Counters (`show interfaces`)
Monitor these at the bottom of the `show interfaces` output:

| Term | Meaning | Likely Cause |
| :--- | :--- | :--- |
| **Runts** | Frames < 64 bytes | Duplex Mismatch / Bad Cable |
| **Giants** | Frames > 1518 bytes | MTU Mismatch |
| **CRC** | Failed CRC check | Interference / Bad Cable |
| **Frame** | Incorrect format | Physical layer errors |
| **Input Errors** | Total of above errors | Struggling to receive data |
| **Output Errors** | Failed to send data | Congestion / Local interface issues |
