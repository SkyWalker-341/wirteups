# Broken Tooth Challenge

## Challenge Overview
The challenge involved analyzing a Bluetooth network capture (`.pcap`) file to extract an embedded flag hidden within an audio stream. The captured data contained **HCI-VT, HCI-CMD**, and **SBC (Subband Codec) encoded audio packets**, transmitted over the **A2DP (Advanced Audio Distribution Profile)** protocol.

## Extracting SBC Data from the Capture File
We identified the relevant **Bluetooth packets** that contained SBC-encoded audio data. To extract these packets from Wireshark, we used the following Python script:

```python
from scapy.all import rdpcap

class Pinfo:
    def __init__(self, number):
        self.number = number

class TVB:
    def __init__(self, data):
        self._data = data

    def bytes(self):
        return self

    def raw(self):
        return self._data

class TapListener:
    def __init__(self, output_filename):
        self.filename = output_filename
        try:
            self.file = open(output_filename, "wb")
        except Exception as e:
            raise Exception(f"Failed to open {output_filename}: {e}")

    def packet(self, pinfo, tvb):
        # Get the entire raw packet data.
        raw_data = tvb.bytes().raw()
        if len(raw_data) > 22:
            trimmed_data = raw_data[22:]
            if self.file:
                self.file.write(trimmed_data)
                self.file.flush()
                print(f"Packet {pinfo.number}: Written {len(trimmed_data)} bytes to {self.filename}")
            else:
                print("Error: File handle is None")
        else:
            print(f"Packet {pinfo.number}: Packet too short (<22 bytes), skipped")

    def reset(self):
        print("Processing reset")

if __name__ == "__main__":
    input_filename = "Blackbeard.pcapng"
    packets = rdpcap(input_filename)
    tap = TapListener("output.bin")

    # Process each packet.
    for i, packet in enumerate(packets, start=1):
        pinfo = Pinfo(i)
        tvb = TVB(bytes(packet))
        tap.packet(pinfo, tvb)
    tap.reset()
```

### Steps in the Script:
1. **Reads the `.pcap` file** using Scapy.
2. **Extracts the raw SBC-encoded data** from Bluetooth packets.
3. **Writes the extracted data** to a binary file (`output.bin`).

## Converting SBC Data to Audio
Once the raw SBC data was extracted, we used the **FFmpeg** tool to convert it into an audio file:

```bash
ffmpeg -f sbc -i output.bin -ar 44100 -ac 2 flag.wav
```

## Final Outcome
After converting the SBC data to an audio file, we listened to `flag.wav` and successfully retrieved the flag.

# Flag : apoorvctf{billie_eilish-birds_of_a_feather}



