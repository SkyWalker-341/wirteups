# Virtual Hard Disk 

## Description

One of the first things I learned when I started hacking was Linux. It was fun until I hit a wall in understanding the differences between operating systems, the concept of a **Shell**, a **Kernel**, and more.

But as I got better, I developed a liking for the terminal and started comparing the Linux operating system with Windows. I realized that neither is inherently superior nor inferior to the other. This challenge will put that understanding to the test.

**Be careful, there are a lot of fake flags around!**

### Submission Format
Submit your answer in the following format:
```
ACECTF{3x4mpl3_fl4g}
```

## Challenge Details

We have obtained a **.vdi** (Virtual Disk Image) file. To analyze the virtual disk, we use **Sleuth Kit** commands.

### Step 1: Identify Partitions
Use the following command to display the partitions on the disk:
```
mmls disk.vdi
```

![Partition Output](https://github.com/user-attachments/assets/5cf9bb12-1f99-4e29-beac-cbe9fbed23a4)

### Step 2: List Files in the Disk
Use the `fls` command to read files from the disk:
```
fls -o <offset> disk.vdi
```

![Screenshot from 2025-03-05 20-49-14](https://github.com/user-attachments/assets/19f66f97-a27c-46f1-86f6-b7d1a1997527)


Upon inspection, you will find multiple files with identical names. Among them, two files contain a **flag** and a **key**.

### Step 3: Extract Files
Use the `icat` command to extract the required files:
```
icat -o <offerset_partition> .vdi file_name  <file_offset> > extracted_file
```

### Step 4: Decrypt the Flag
The extracted files contain an **encoded flag** and a **key**. You need to decrypt the flag using the provided key.

- **Encoded Flag:**
```
CTCHHW{7t3_h1hw3p3sq3_s37i33r_a0l_4li_a3}
```
- **Key:**
```
cryforme
```

After decryption, you will obtain the final flag.

## Flag
```
ACECTF{7r3_q1jr3b3be3_o37g33a_c0g_4xr_o3}
```

---


