# Whipering waves

## Description
Alex, a passionate linguist and culture enthusiast, frequently visits the website Francophonie.org to learn about the French-speaking world. Known for their love of cryptography and steganography, Alex often hides messages in unsuspecting places.


**Extract the ZIP File:**  
   The provided ZIP file is locked, and we do not have the password.

**Attempt to Crack the ZIP File:**  
   Typically, we use a wordlist like `rockyou.txt` to brute-force ZIP passwords. However, in this case, `rockyou.txt` fails.

**Generate a Custom Wordlist:**  
   Since the challenge description mentions the French-speaking world, we generate a custom wordlist using the `cewl` command:
   ```
   cewl -w custom_wordlist.txt http://www.francophonie.org
   ```

![Screenshot from 2025-03-13 16-20-46](https://github.com/user-attachments/assets/192cf5f1-4b50-4f79-9318-087e0d372776)

**word list**
![Screenshot from 2025-03-13 16-21-28](https://github.com/user-attachments/assets/a904a1f4-fb77-495d-86cd-219c3b3dd89e)



**Crack the ZIP File Using fcrackzip:**  
   We use `fcrackzip` to brute-force the ZIP file with our custom wordlist:
   ```
   fcrackzip -u -D -p path/to/custom_wordlist.txt path/to/zipfile
   ```
   The correct password retrieved from the wordlist is: `Vierges`.

 **Extract and Analyze the WAV File:**  
   After extracting the ZIP file, we find a `.wav` file. Open the file using **Audacity** or **Sonic Visualizer**.

![Screenshot from 2025-03-13 16-37-45](https://github.com/user-attachments/assets/7e6c31a8-3355-4035-90d1-84a941a608d8)


**Reveal Hidden Morse Code:**  
   Use the spectrogram view in Audacity or Sonic Visualizer to detect the embedded Morse code. Translate the Morse code to retrieve the hidden flag.

Flag : 
