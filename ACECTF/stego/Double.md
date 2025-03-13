# Double Vision 

## Description
You have found a ZIP file named `double_vision.zip`. Upon extracting the contents, you discover two PNG images labeled `1.png` and `2.png`. While both images appear nearly identical, their file sizes differ, indicating that additional data is embedded in `2.png`. Your task is to uncover the hidden secret and retrieve the flag.

## Steps to Solve

 **Extract the ZIP File:**  
   Unzip `double_vision.zip` to get `1.png` and `2.png`.

**Compare the Images:**  
   Check the file sizes of `1.png` and `2.png`. Since `2.png` is larger, it likely contains extra hidden data.

![image](https://github.com/user-attachments/assets/010a5f9f-ef28-4d3b-922f-be99e9920ade)


**Perform XOR Analysis:**  
   Use `Stegsolve` to XOR `1.png` and `2.png`. This operation will highlight the differences between the two images.

![Screenshot from 2025-03-13 15-58-31](https://github.com/user-attachments/assets/4f9173fe-6ffb-42f7-9c2a-72ff2e1e354c)


**Identify Hidden Data:**  
   After applying the XOR function, the right-side contrast panel in `Stegsolve` reveals hidden Morse code embedded in `2.png`.

![image](https://github.com/user-attachments/assets/33565f09-1783-4f47-8173-3ab1c612ceb1)


**Decode the Morse Code:**  
   Translate the Morse code to extract the hidden message. The decoded Morse code will reveal the flag for the challenge.

## Flag : ACECTF{D07_D45H}


