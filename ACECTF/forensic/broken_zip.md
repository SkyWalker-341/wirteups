# Broken Secrets

## Description

You've found a suspicious file, but it appears to be broken and cannot be opened normally. Your goal is to uncover its secrets.

### Submission Format
Submit your answer in the following format:
```
ACECTF{3x4mpl3_fl4g}
```

## Challenge Details

You will receive an archive file compressed using the **7z** method. To extract the contents, use the following command:
```
7z x zip_file_name
```

After extraction, you will find a document containing a folder named **word**. Inside this folder, you will see a file named:
```
not_so_suspicious_file
```

Open this file in **hexedit** or **ghex**. Upon examination, you will realize that it is actually a **PNG file**, but its **magic number** has been altered.

![Screenshot from 2025-03-05 19-24-51](https://github.com/user-attachments/assets/f5632755-7bd5-4477-b968-0d8288ed1974)


### Fixing the Magic Number
A valid PNG file starts with the following magic number:
```
89 50 4E 47 0D 0A 1A 0A
```

![Screenshot from 2025-03-05 19-28-45](https://github.com/user-attachments/assets/77756ecd-b21a-4738-8c7e-cc2d50f4d15f)


Modify the file's magic number accordingly. Once corrected, you will be able to view the image, which contains the flag.

## Flag
```
ACECTF{h34d3r_15_k3y}
```

