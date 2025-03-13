# CrypticPixels

## Description
This image may look normal at first glance, but something important is hidden inside. The secret is carefully concealed, making it difficult to find.

Your task is to analyze the image, uncover the hidden message, and reveal what’s concealed. Do you have what it takes to crack the code and unlock the secret?

Submit your answer in the following format: **ACECTF{3x4mpl3_fl4g}**


Upon inspecting the image metadata, we notice extra data appended after the `IEND` marker. This suggests that additional content has been embedded within the image.


Using `binwalk`, we extract hidden files from the image and discover a ZIP archive. After unzipping the file, we find `flag.txt`.

![Screenshot from 2025-03-13 16-54-16](https://github.com/user-attachments/assets/7143b93b-fd13-415b-b574-12da0dc79672)


However, the flag inside `flag.txt` is encoded using the ROT cipher:
```
JLNLCO{q4q4_h0d'a3_5v4a7}
```
By applying a ROT17 cipher shift, we reveal the original flag.

![Screenshot from 2025-03-13 16-55-01](https://github.com/user-attachments/assets/1586fff9-b133-4031-b039-3973a1cdde01)


## Flag
**ACECTF{h4h4_y0u'r3_5m4r7}**

