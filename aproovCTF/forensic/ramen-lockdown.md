# Ramen-lockdown

## Description
A criminal mastermind named Larry has stolen Chef Tataka's ultimate ramen recipe and encrypted it inside a password-protected ZIP file. The file contains a sacred text that holds the secret to flavor nirvana. Our task is to crack the ZIP file and recover the recipe. No pressure!

## Initial Attempt: Brute Force
We initially attempted to brute-force the ZIP password but were unsuccessful. We then searched for alternative methods and discovered a tool called **bkcrack** that could help us extract the file using known plaintext attacks.

## Exploiting Known Plaintext with bkcrack
Since we knew that the stolen file inside the ZIP was a **PNG image**, we leveraged the fact that all PNG files start with a well-known header:

```
89 50 4E 47 0D 0A 1A 0A
```

However, for this attack to be effective, we needed at least **13 bytes** of known data. All PNG files must also contain an **IHDR chunk**, so we extended our known plaintext to:

```
89 50 4E 47 0D 0A 1A 0A 00 00 00 0D 49 48 44 52
```

## Extracting Internal Keys
Using bkcrack, we extracted the internal keys:

```
7cfefd6a 4aedd214 970c7187
```

## Cloning the ZIP File Without a Password
We then used the extracted keys to create an unprotected version of the ZIP file:

```bash
bkcrack -C recipe.zip -k 7cfefd6a 4aedd214 970c7187 -D unprotected.zip
```

This command generated a **clone** of the original ZIP file without a password.

![Screenshot from 2025-03-10 04-00-46](https://github.com/user-attachments/assets/3cc4d96d-10d2-406c-8daf-ca3a8416deba)


## Extracting and Viewing the File
Finally, we extracted the contents of the new ZIP file:

```bash
unzip unprotected.zip
```
![secret_recipe](https://github.com/user-attachments/assets/2302099f-7204-4f52-877e-543a0b70445f)


We then opened **secret_recipe.png** in an image viewer and successfully retrieved the flag!

# Flag : apoorvctf{W0rst_r4m3n_3v3r_ong}

