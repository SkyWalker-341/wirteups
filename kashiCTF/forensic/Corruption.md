# Corruption

A corrupt drive, I see…

![Screenshot from 2025-03-07 20-07-49](https://github.com/user-attachments/assets/e98ef38a-1e38-4688-9642-c1bfd45aa3a1)

By simply using the `strings` command, we were able to retrieve the flag.

**Flag:** `KashiCTF{FSCK_mE_B1T_by_b1t_Byt3_by_byT3}`

## Explanation of `strings` Command

The `strings` command is used to extract human-readable text from binary files, disk images, or any file containing non-text data. It is particularly useful in forensic investigations and reverse engineering.

### Usage:
```bash
strings corrupted_drive.img
```
This command scans the binary file and extracts readable ASCII and Unicode strings. In this case, we found the flag hidden within the output.

