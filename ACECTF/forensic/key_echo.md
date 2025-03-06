#  Keyboard Echo 

## Description
We have intercepted USB traffic from a device and captured the data in a `.pcapng` file. The keystrokes are encoded and need to be decoded into readable text. Our goal is to extract the data from the captured traffic and reconstruct the original input.

### Flag Format:
```
ACECTF{3x4mpl3_fl4g}
```

## Steps to Extract Keystrokes

### 1. Export Data from Wireshark
To analyze the traffic, export the data in CSV format by following these steps:
- Go to **File** → **Export Packet Dissections** → **As CSV**.
![Screenshot from 2025-03-06 19-06-33](https://github.com/user-attachments/assets/6a71d3ad-e9a0-4bc9-981a-d6c2bcf72542)

- Save the CSV file as `hiddata.csv`.

![Screenshot from 2025-03-06 19-25-59](https://github.com/user-attachments/assets/a2f909c3-cbbf-496b-947a-3c57b2f306bd)

### 2. Extract Relevant Data
Use the `cut` command to filter the keystroke data from the CSV file:
```bash
cat hiddata.csv | cut -d "," -f 7 | cut -d "\"" -f 2 | grep -vE "leftover data" > hexoutput.txt
```

![Screenshot from 2025-03-06 19-49-05](https://github.com/user-attachments/assets/d78e070a-fd09-478e-93fc-7da3026a197d)

### 3. Map the Keystrokes
Use the following Python script to map the extracted keystroke data into readable text.

#### **Python Script for Decoding Keystrokes**
```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

newmap = {
    2: " ",
    4: "a", 5: "b", 6: "c", 7: "d", 8: "e", 9: "f",
    10: "g", 11: "h", 12: "i", 13: "j", 14: "k", 15: "l",
    16: "m", 17: "n", 18: "o", 19: "p", 20: "q", 21: 'r',
    22: 's', 23: 't', 24: 'u', 25: 'v', 26: 'w', 27: 'x',
    28: 'y', 29: 'z', 30: '1', 31: '2', 32: '3', 33: '4',
    34: '5', 35: '6', 36: '7', 37: '8', 38: '9', 39: '0',
    40: '\r\n', 41: 'ESC', 42: "del", 43: 'tab', 44: 'space',
    45: '-', 47: '{', 48: '}', 55: '*', 56: '/', 57: 'CapsLock',
    79: '>', 80: '<'
}

message = ""

with open("usbdata", "r") as myKeys:
    for line in myKeys:
        hex_line = line.strip()
        if hex_line:
            try:
                bytes_array = bytearray.fromhex(hex_line)
                for byte in bytes_array:
                    if byte != 0:
                        key_val = int(byte)
                        if key_val in newmap:
                            message += newmap[key_val]
            except ValueError:
                print(f"Invalid hex data: {hex_line}")

print("Decoded message:")
print(message)
```

![Screenshot from 2025-03-06 19-49-54](https://github.com/user-attachments/assets/510267f5-c8bf-4e53-8e2e-504e1376752b)


### 4. Reconstruct the Flag
After decoding the keystrokes, the reconstructed flag is:
```
ACECTF{y0uh4v3f0und17raataba}
```



