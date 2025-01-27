# Mystery Presentation

### Description
We recently got this absolutely non-sensical presentation from a confidential informant, along with a note that said:

> "The truth hurts boomers, but it's what on the inside that counts <3"

We can't make heads or tails of it, but it has to be important! Can you help us out?

---

### Steps to Solve

1. **Check the File Type**
   Use the `file` or `exiftool` command to check the file type. The output will indicate that the file is a zip archive.

   ```bash
   file file-name
   ```

2. **Unzip the File**
   Extract the zip archive using the `unzip` command:

   ```bash
   unzip file-name
   ```

   During extraction, you will notice another archive file named `secret_data.7z`.

   ![Screenshot from 2025-01-27 13-43-43](https://github.com/user-attachments/assets/f58acb76-3e52-436e-97cf-236558f20472)

3. **Extract the `.7z` File**
   Use the `7z` command to extract the contents of `secret_data.7z`:

   ```bash
   7z x file-name
   ```

   This will extract a folder named `secret_data`.

   ![Screenshot from 2025-01-27 13-46-52](https://github.com/user-attachments/assets/ad90f90a-a912-4ca9-acbe-8d38e4201651)

4. **Retrieve the Flag**
   Inside the `secret_data` folder, you will find a file named `flag.txt`. Use the `cat` command to reveal the flag:

   ```bash
   cat flag.txt
   ```

   The flag is:

   ```
   TUCTF{p01yg10+_fi1e5_hiddin9_in_p1@in_5i9h+}
   ```

