# Memories Bring Back

A collection of images, a digital time capsule—preserved in this file. But is every picture really just a picture? A photographer once said, *“Every image tells a story, but some stories are meant to stay hidden.”* Maybe it’s time to inspect the unseen and uncover what has been left behind.

## Extracting the Hidden Data

Using forensic tools like `mmls`, `fls`, and `icat`, we were able to extract an image from the disk image file (`disk.img`). 

![Screenshot from 2025-03-07 19-56-05](https://github.com/user-attachments/assets/a16432f7-a668-4bca-93f8-ef30321bf565)


One particular image contained a message stating *"not to hide"*, which made it suspicious. We extracted the file using the `icat` command and examined its contents using `cat`. 

![Screenshot from 2025-03-07 19-56-19](https://github.com/user-attachments/assets/41091ffe-5996-420d-b7e4-67088744a0a2)

Then we got the flag ..

![Screenshot from 2025-03-07 19-56-30](https://github.com/user-attachments/assets/9e7b613e-8d0c-4790-89e2-a2b3b7e3f9ea)


## Explanation of Commands Used

### 1. `mmls`
The `mmls` (media management list) command is used to display partition information from a disk image. It helps forensic analysts identify partitions and locate where file systems start.

**Usage:**
```bash
mmls disk.img
```
This command outputs the partition table of the disk image, showing details like starting sector, partition type, and size.

### 2. `fls`
The `fls` command lists files and directories within a file system present in a disk image. It helps locate files that are deleted but still recoverable.

**Usage:**
```bash
fls -o <partition_offset> disk.img
```
Replace `<partition_offset>` with the correct value obtained from `mmls`.

### 3. `icat`
The `icat` command is used to extract and display the contents of a file from a disk image without modifying it.

**Usage:**
```bash
icat -o <partition_offset> disk.img <inode_number>
```
Replace `<inode_number>` with the inode value of the file obtained using `fls`.

**Flag: KashiCTF{DF1R_g03555_Brrrr}**
