# Phantom Connection

Like a fleeting dream, a connection once existed but has faded into the void. Only shadows of its presence remain. Can you bring it back to light?

## Challenge Steps

1. Extract the provided ZIP file. Inside, you will find two files: one with a `.bin` extension and another with a `.bmc` extension.
2. The `.bmc` file is a tool used to extract data or images from the `.bin` file.
3. The source of the `bmc` tool is available at: [bmc-tools](https://github.com/ANSSI-FR/bmc-tools).

4. Clone the repository and use the `bmc-tools.py` script to extract data from the `.bin` file using the following command:

   ```bash
   python bmc-tools.py -s /path/to/bin_file -d output_directory
   ```
![Screenshot from 2025-03-10 01-49-26](https://github.com/user-attachments/assets/fa684f87-2d45-403a-a2f1-35775c317182)


5. Navigate to the extracted folder. You will find a bitmap file inside.


![Screenshot from 2025-03-10 02-00-09](https://github.com/user-attachments/assets/83cae979-6576-4334-a86a-797451d58ee7)

6. Open the bitmap file to reveal the flag.

### Flag : apoorvctf{CAcH3_Wh4T_YoU_sE3}
