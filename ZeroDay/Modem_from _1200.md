# Modem from 1200

Father Ted gave me this strange device. Since I’m quite smart, I tried to capture and understand what it was saying... but had no luck. Can you help me retrieve some sensitive information from it?

We were provided with a file named `challenge.wav`. Based on the challenge title **"Modem from 1200"**, we can infer that this refers to a **modem signal operating at 1200 baud** (symbols per second).

### Common Protocols at 1200 Baud

- **Bell 202** (used in early modems and telemetry systems)
- **FSK (Frequency Shift Keying)** encoding

This suggests that the `.wav` file likely contains **digitally encoded data** transmitted using FSK.

### Objective

We need to **decode the contents** of the 1200 baud modem transmission captured in audio form (`.wav`) to extract sensitive information.

### Tool: Minimodem

We'll use a tool called `minimodem`, a command-line program that functions as a general-purpose software audio FSK modem.

To decode the transmission, use the following command:

```bash
minimodem --rx 1200 -f challenge.wav
```
#Flag : ZeroDays{MiNi_m0D3m_Att4cKs_0Nc3_Aga1n}
