# Security Rocks

### Description
I shared a super secret message. I hope it's secure.

---

### Steps to Solve

1. **Analyze the Network Traffic**
   The provided file is a network traffic capture. Use Wireshark to analyze the protocol used. The protocol identified is **EAPOL**, which is used in Wi-Fi networks. However, the packets are encrypted, so the passkey is required to decrypt them.

   ![Screenshot from 2025-01-27 13-46-52](https://github.com/user-attachments/assets/c019aea2-157b-44b0-ba31-db9875812549)

2. **Bruteforce the Passkey**
   Since the passkey is not provided, it must be brute-forced. Use the `aircrack-ng` tool, a Wi-Fi password cracker, along with the `rockyou.txt` wordlist.

   Run the following command to brute-force the passkey:

   ```bash
   aircrack-ng -w path/to/the/rockyou.txt network-file
   ```

   ![Image](https://github.com/user-attachments/assets/8506c7a5-823d-4424-a78b-b873b2d362e3)

   After running the command, the passkey is found to be:

   ```
   youwontguessit92
   ```

3. **Decrypt the Packets**
   Use the passkey to decrypt the encrypted packets in Wireshark. Add the key in Wireshark:

   - Navigate to **Edit -> Preferences -> Protocols -> IEEE 802.11 Wireless LAN**.
   - Insert the decryption key.

   ![Image](https://github.com/user-attachments/assets/9400bf2a-d1cc-4b5b-aa75-d05fa7261174)

4. **Inspect the Decrypted Protocols**
   After decryption, check the **Protocol Hierarchy** in Wireshark. You will find some **FTP** protocol packets. These packets indicate that a file was sent.

   ![Screenshot from 2025-01-27 14-37-53](https://github.com/user-attachments/assets/bd8c37f7-60c2-413d-b08e-bb3f95b62076)

5. **Extract the File**
   Inspect the FTP packets to identify the file being transferred. The file name is `secret.txt`. Export the file in Wireshark:

   - Navigate to **File -> Export Objects -> FTP**.
   - Save the file.

   ![Screenshot from 2025-01-27 14-35-15](https://github.com/user-attachments/assets/41a5552a-f3e2-41e5-9904-b5abaeb491f9)

6. **Retrieve and Decode the Flag**
   The content of the `secret.txt` file is:

   ```
   Heres my super secret flag, I made it extra secure ;)
   {1KZTi2ZV7tO6yNxslvQbjRGL54BsPVyskwv4QaR29UMKj}
   ```

   The flag is encrypted using **Base62**. Decode it using a Base62 decoder to reveal the flag:

   ```
   TUCTF{w1f1_15_d3f1n173ly_53cure3}
   ```

---

### Final Flag

```
TUCTF{w1f1_15_d3f1n173ly_53cure3}
```

