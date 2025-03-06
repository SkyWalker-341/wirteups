# Another Reading between the Lines? 

## Description

**Question:** Is this another one of those hidden-in-plain-sight typical normie challenges?

**Answer:** No.

This challenge is very simple. Here, you have a file named `hidden`, and all you need to do is extract the flag. My focus for this year's CTF is not just the beginning but also ending on a high note. I won’t rely on overused "read between the lines" challenges but would rather have you do some research.


We received a text file named `hidden`. If you use `cat` or `strings` on this file, you will notice a huge amount of whitespace. To analyze these whitespaces, we can use tools like `stegsnow`, `awk`, or `cat`. 

A powerful text-processing tool for this kind of analysis is `awk`. If you need more information on the `awk` command, you can use `man awk`.

To extract the data from the `hidden` file, use the following command:

![Screenshot from 2025-03-06 11-22-12](https://github.com/user-attachments/assets/e3fbb5d9-622d-4897-ac77-6359a06a9466)


```bash
awk '{ if (index($0, "\r") > 0) { printf "1"; } else { printf "0"; } } END { print ""; }' hidden > binary_line.txt
```

### Explanation of the Command

- `awk '...code...' hidden`  
  This runs the `awk` text-processing tool on the file named `hidden`.
- `$0`  
  In `awk`, `$0` represents the entire current line being processed.
- `index($0, "\r")`  
  The `index` function searches the current line (`$0`) for the substring `\r` (the carriage return character).
  - If `\r` is found, `index` returns its position (a number greater than 0).
  - If not found, it returns `0`.
- `if (index($0, "\r") > 0) { printf "1"; } else { printf "0"; }`  
  - For each line, the script checks if `\r` exists.
  - If it does, it prints `1` (using `printf` so that it doesn't add a newline).
  - If it doesn’t, it prints `0`.
- `END { print ""; }`  
  - After processing all lines, the `END` block is executed. Here, `print ""` outputs a newline, ensuring the output file ends with a complete line.
- `> binary_line.txt`  
  - This redirects the output of the command into a file named `binary_line.txt`.

![Screenshot from 2025-03-06 12-15-12](https://github.com/user-attachments/assets/307013e5-7171-41ea-9f1f-dc081b995f6b)


After running this command, we obtain the binary representation of the flag:

```
010000010100001101000101010000110101010001000110011110110110111000110000010111110111001000110011001101000110010000110001011011100011011001011111011000100110010100110111011101110011001100110011011011100101111100110111011010000011001101011111011011000011000101101110001100110011010101111101
```

To convert this binary data to ASCII, use the following Perl command:

```bash
perl -lpe '$_=pack"B*",$_' binary_line.txt
```

![Screenshot from 2025-03-06 12-27-43](https://github.com/user-attachments/assets/dc5823ef-6b19-4d73-8359-8af122e7d745)


### Flag

```
ACECTF{n0_r34d1n6_be7w33n_7h3_l1n35}
```

