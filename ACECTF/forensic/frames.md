#  Fractured Frames 

### Description

A forensic investigator retrieved this image from a suspect’s device, but something isn’t right. The structure shows unusual modifications. Could it be that vital information was concealed rather than erased?

Flag Format: ACECTF{3x4mpl3_fl4g}

You are given a JPG file. At first glance, the image appears normal, but checking the image chunks reveals something off about the image height.

![Screenshot from 2025-03-06 18-08-10](https://github.com/user-attachments/assets/b06b50bb-c863-48ba-9028-d7e07f4384aa)


Upon examining the image’s chunks, we notice that the SOF (Start of Frame) marker has a height of 0 bytes.

![Screenshot from 2025-03-06 18-08-29](https://github.com/user-attachments/assets/b3c1536d-da74-416a-af5a-28ff7f515a8c)

Modifying the height value properly restores the image and reveals the flag.

![Screenshot from 2025-03-06 18-09-01](https://github.com/user-attachments/assets/389977e7-4f7e-4b4c-b0ce-80b3aa62894c)

---

# Flag :  ACECTF{th1s_should_b3_en0u6h}
