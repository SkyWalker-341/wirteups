# Restaurant

I just asked for my favorite pasta, and they gave me this. Are these guys **STUPID**? Maybe in the end, they might give me something real. *(Wrap the text in `KashiCTF{}`)*

## Analyzing the Image

We received a `.jpg` file and examined its hexadecimal structure. Typically, a JPEG file ends with the hex signature `FFD9`. However, in this image, there was extra data appended after this marker. 

![Screenshot from 2025-03-07 20-19-19](https://github.com/user-attachments/assets/f47be887-8819-43df-8da3-7ba5e39ba305)


## Extracting Hidden Data

By extracting the additional data from the file, we discovered that it was encoded using the **Bacon Cipher** method. 

## Decoding the Cipher

Using a Bacon Cipher decoder, we were able to retrieve the hidden message, which contained the flag.

![Screenshot from 2025-03-07 20-22-59](https://github.com/user-attachments/assets/983cd544-9ac8-485d-8d32-9b5ff6670463)


**Flag:** kashiCTF{THEYWEREREALLLLYCOOKING}


