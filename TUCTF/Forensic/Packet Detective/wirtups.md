# Packet Detective

### Description
You are a security analyst tasked with analyzing a pcap file containing network traffic. Hidden among these packets is a secret flag that was transmitted. Your mission is to analyze the pcap file, filter out common traffic, and identify the packet carrying the hidden flag.

---

### Steps to Solve

1. **Analyze the Network Traffic**
   The provided file is a network traffic capture. Open the file in Wireshark to begin analysis.

2. **Filter for HTTP Protocol**
   Use Wireshark to identify the protocol used. Apply a filter for **HTTP** to narrow down the relevant packets.




3. **Inspect the Last TCP Packet**
   Look for the last TCP packet in the filtered results. This packet contains the hidden flag.

4. **Retrieve the Flag**
   Inspect the content of the packet to find the secret flag:

   ```
   TUCTF{N3tw0rk_M4st3r}
   ```

---

### Final Flag

```
TUCTF{N3tw0rk_M4st3r}
```

