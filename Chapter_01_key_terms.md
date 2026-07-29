# CCNA Study Notes: Chapter 1 Key Terms Explained

## 1. Networking Model
*   **Definition:** A conceptual framework (such as **OSI** or **TCP/IP**) that standardizes how different networking protocols, hardware, and software work together to enable communication across networks.

## 2. Encapsulation
*   **Definition:** The process of taking data from a higher layer, adding specific protocol headers (and trailers) to it, and passing it down to the next lower layer. 
*   *Flow:* Application Data $\rightarrow$ Segment (L4) $\rightarrow$ Packet (L3) $\rightarrow$ Frame (L2) $\rightarrow$ Bits (L1).

## 3. De-encapsulation
*   **Definition:** The reverse process of encapsulation. As data is received on a destination device, each layer strips away its corresponding header/trailer from the bottom up to read the payload and pass it to the next higher layer.

## 4. Segment
*   **Definition:** The Protocol Data Unit (PDU) at **Layer 4 (Transport Layer)**, primarily associated with TCP. It includes application data plus transport-layer headers (like source/destination ports and sequence numbers).

## 5. Packet
*   **Definition:** The PDU at **Layer 3 (Network Layer)**. It consists of the Layer 4 segment wrapped with an IP header, which includes the source and destination IP addresses used for routing across different networks.

## 6. Frame
*   **Definition:** The PDU at **Layer 2 (Data Link Layer)**. It encapsulates the Layer 3 packet with a Layer 2 header and trailer (including source and destination MAC addresses and a Frame Check Sequence for error detection) for physical transmission on a local link.

## 7. Same-Layer Interaction
*   **Definition:** Communication that occurs between the **same layer on two different network devices** (e.g., the Transport layer on a PC communicating virtually with the Transport layer on a server using protocols like TCP). They use headers to exchange information meant only for each other.

## 8. Adjacent-Layer Interaction
*   **Definition:** Communication and service provision between **neighboring layers within the same device** (e.g., Layer 3 requesting services from or handing data down to Layer 2). Each layer provides a service to the layer immediately above it.
