# Hidden in the traffic 

## Description

A whistleblower tipped us off about a secret communication between two devices. We managed to intercept the network traffic, but the flag is hidden within the data. Your task is to analyze the provided **PCAP** file, uncover the hidden message, and extract the flag.

### Submission Format
Submit your answer in the following format:
```
ACECTF{3x4mpl3_fl4g}
```

## Challenge Details

We captured network traffic during our analysis. By examining different protocols, we found that the **ICMP protocol** contains some noise data. You can extract the ICMP data using the following command:
```
tshark -r capture.pcap -Y "icmp" -T fields -e data > icmp_data.txt
```

The extracted data looks like this:
```
ABCDEFGHIJKLCABCDEFGHIJKLEABCDEFGHIJKLCABCDEFGHIJKLTABCDEFGHIJKLF{ABCDEFGHIJKLpABCDEFGHIJKL1ABCDEFGHIJKLnABCDEFGHIJKL6ABCDEFGHIJKL_ABCDEFGHIJKL0ABCDEFGHIJKLfABCDEFGHIJKL_ABCDEFGHIJKLDABCDEFGHIJKL3ABCDEFGHIJKL4ABCDEFGHIJKL7ABCDEFGHIJKLhABCDEFGHIJKL}
```

You need to decode this noisy message to retrieve the flag.

## Flag
```
ACECTF{p1n6_0f_D347h}
```

---

