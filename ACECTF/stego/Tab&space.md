# Tabs$sapces

## Challenge Description
A mysterious ZIP file containing a collection of images and a text file has been discovered. The task is to retrieve the flag.


Upon extracting the ZIP file, we found a file named **"whitespace_flag.txt"**. At first glance, the file appeared to be empty. However, upon closer inspection, we realized that the flag was hidden within whitespace characters.

Using the `cat` command alone showed only blank spaces:
```sh
cat whitespace_flag.txt
```
However, using `cat -A` revealed special whitespace characters:
```sh
cat -A whitespace_flag.txt
```
![Whitespace Characters](https://github.com/user-attachments/assets/b42c80b0-38cc-4e53-a32d-3c9904f35f23)

Decoding the Hidden Data
To extract the hidden message, we wrote a Python script that interprets the whitespace characters as binary data.

#### Python Script:
```python
def decode_whitespace(file_path, tab_val, space_val):
    with open(file_path, "r") as f:
        data = f.read()
    data = data.replace("\n", "")
    binary = data.replace("\t", tab_val).replace(" ", space_val)
    if len(binary) % 8 != 0:
        print("Warning: binary length not a multiple of 8, result may be off.")
    decoded = ""
    for i in range(0, len(binary), 8):
        byte = binary[i:i+8]
        try:
            decoded += chr(int(byte, 2))
        except Exception as e:
            decoded += "<?>"
    return decoded

flag1 = decode_whitespace("whitespace_flag.txt", tab_val='1', space_val='0')
flag2 = decode_whitespace("whitespace_flag.txt", tab_val='0', space_val='1')

print("Decoded with tab=1, space=0:")
print(flag1)
print("\nDecoded with tab=0, space=1:")
print(flag2)
```
![Screenshot from 2025-03-10 14-33-33](https://github.com/user-attachments/assets/ad974173-8626-4d43-a374-3526e6817b35)

Running the script revealed the hidden flag:

## Flag
```
ACECTF{n0_3xp1017_n0_g41n}
```

