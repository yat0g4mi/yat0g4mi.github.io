---
title: "1337CTF"
date: 2023-11-30T02:16:50+07:00
tags: [Miscellanous]
author: [1]
---

# Solution
## 1. Warmup/Flag Extraction
-   [Challenge link](https://ctf.intigriti.io/challenges#Over%20the%20Wire%20(part%201)-42)

![Smile](/assets/posts/1337/FlagExtraction/gif.png)

-   Downloading the challenge, I get 1 rar file, then 1 string of tar files, I guess I extract 1 continuous sequence of file types. Use 7zip or whatever you can. At the end we get 1 gif file.


-   Try strings "name-file.gif" | grep "INTIGRI"
. Got flag:

    -> *INTIGRITI{fl46_3x7r4c710n_c0mpl373}*

## 2. Warmup/Over the Wire 1 
- [Challenge Link](https://ctf.intigriti.io/challenges#Over%20the%20Wire%20(part%201)-42/)
-   I get 1 pcap file. People can have many ways but I use Wireshark. As always, I use tcp containing "flags" to check the flow of the file. I noticed 1 thread has info : RETR flag.zip.
-   Quickly follow that stream and I see some important information.

    ![Smile](/assets/posts/1337/OverTheWire1/1.png)
- I was going to try File -> Export Objects, but there doesn't seem to be anything in it. The only usable thing here is the password I found above. Then I tried : strings name-file.pcap | grep "flag" and getting 2 line seems to be a clue.
    ![Smile](/assets/posts/1337/OverTheWire1/2.png)
-   The first is "flag.txt". I used the binwalk with the pcap file and actually got 1 zip file. "Foremost" file pcap to receive the zip file, but it requires a key.I tried using the original password I found to open but failed. With the line "This flag is really important so I had to encrypt it in case it falls into the wrong hands" I reopen the wireshark and check which stream it belongs to. I got 1 message :

    ![Smile](/assets/posts/1337/OverTheWire1/3.png)

-   I thought for a while and tried changing 2022 in the password to 2023 and got the flag.

FLAG: *INTIGRITI{1f_0nly_7h3r3_w45_4_53cur3_FTP}*

## 3. Warmup/Over the Wire 2
- [Challenge Link](https://ctf.intigriti.io/challenges#Over%20the%20Wire%20(part%202)-45/)

- Another pcap challenge. I did the same as season 1 but got nothing. I tried again with File -> Export Objects. This time in the IMF section I see 4 .eml files. Try saving them all and viewing each file 1 (remember to save the file with the eml extension for easier reading). The first 2 files are nothing, just normal messages. 2 files after each file have 1 photo. I tried to download each photo and used the Stegano tools to see if I got anything. And in the 2nd image, I used the "binwalk" to check and saw that there was a zlib file . Using "zsteg" to check, we get the flag:

    ![Smile](/assets/posts/1337/OverTheWire2/1.png)

FLAG: *INTIGRITI{H1dd3n_Crypt0Cat_Purr}*

## 4. Misc/ZeChat
![Smile](/assets/posts/1337/ZeChat/zechat.png)
- This was honestly one of the hardest challenges I've ever done. Only 7 teams solved this challenge, not including my team. I spent up to 8 hours solving this challenge by hand, including reading the article. You can read [Chivato's article](https://hackmd.io/@Chivato/SkN3Piyan) to solve this problem.
  The binary string that I execute is:

   `01001001 01001110 010101000 10010010 1000111 01010010 01001001 01010100 010010 0101111011 0111011100 1100110110 0011011010 0000110100 0011011101 0111110110 0100001101 0000110111 0011010001 0111110011 0011011011 1001 1000110011 0000011 001 0000110001 0110111000 1101100101 1111011001 1001110100 01 11011100 1000010010 0001001000 0101111101`

FLAG: *INTIGRITI{w3ch47_d474_3nc0d1n6_ftw!!!}*

*Note: If you're having trouble knowing where to start? And, I may have omitted some locations in the picture so my results may be a bit misleading. Please contact me if you encounter any of the above two situations or you have any other questions.