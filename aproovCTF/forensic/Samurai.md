# Samurai

## Description : Unveil the Lost Code of the Samurai

## Challenge Steps

1. We received a `.jpg` file. Upon analyzing the file, we noticed something suspicious in the hex values.
2. The `.jpg` chunk ends at `FFD9`, but there is additional data after this end marker. This indicates that the extra data does not belong to the image.
3. The extra data appears to be Brainfuck code.

![Screenshot from 2025-03-10 02-23-50](https://github.com/user-attachments/assets/b4da176a-fca8-4078-a880-57c832d7ffbb)

4. Decoding the Brainfuck code reveals a Google Drive link, which contains another `.jpg` file.
  you will got this link :``` https://drive.google.com/file/d/1JWqdBJzgQhLUI-xLTwLCWwYi2Ydk4W6-/view```

5. Examining the new `.jpg` file shows that the data chunks are not in the correct order.

![Screenshot from 2025-03-10 03-06-54](https://github.com/user-attachments/assets/3f0add1f-00a7-41ea-8fb4-1a834b4e4f5c)

6. The byte sequence is reversed in pairs, meaning we need to rearrange the bytes correctly.

script :

 ```
              file_path = "samurai"
              with open(file_path, "rb") as f:
                  data = f.read()
              hex_preview = data[:16].hex() 
              fixed_data = bytearray()
              for i in range(0, len(data), 2):
                  fixed_data.extend(data[i:i+2][::-1])  
              
            fixed_file_path = "samurai_fixed.jpg"
            with open(fixed_file_path, "wb") as f:
                f.write(fixed_data)
            hex_preview, fixed_file_path
```

7. Once the bytes are correctly reordered, you will obtain the flag.


### Flag : apoorvctf{ByT3s_OUT_OF_ORd3R}
