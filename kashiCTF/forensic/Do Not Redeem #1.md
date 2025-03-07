# Do Not Redeem #1

Uh oh, we’re in trouble again. Kitler’s Amazon Pay wallet got emptied by some scammer. Can you figure out the OTP sent to Kitler right before that happened, as well as the time (Unix timestamp in milliseconds) at which Kitler received that OTP?

## Objective

Your task is to extract the OTP and its corresponding timestamp from an Android forensic dump.

**Flag Format:** `KashiCTF{OTP_TIMESTAMP}`

Example: `KashiCTF{XXXXXX_XXXXXXXXXXXXX}`

## Analyzing the Android Dump

We need to analyze the extracted Android dump, specifically looking for SMS messages that may contain OTPs. The SQLite database often stores SMS data, making it a primary target for investigation.

### Steps to Extract the OTP:
1. Examine the SQLite databases within the Android dump.
2. Locate the database that stores SMS messages.
3. Query the relevant tables to find messages related to OTPs.
4. Extract the OTP and the timestamp from the records.
5. I am use Aleapp tool to use analyzing the data base 

![image](https://github.com/user-attachments/assets/ad86cd69-1619-4160-9578-052b2ad5f2c6)

## Reference
For more details on Android forensics, check out this guide:
[Hackers Arise - Mobile Forensics (Android)](https://hackers-arise.net/2023/11/30/digital-forensics-part-10-mobile-forensics-android/)

By carefully examining the SQLite database, we can recover the OTP message and its timestamp, leading us to the correct flag.


## Flag : KashiCTF{839216_1740251608654}
