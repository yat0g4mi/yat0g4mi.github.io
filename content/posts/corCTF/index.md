--- 
title: "corCTF"
date: 2024-07-30T00:20:31+07:00
tags: [Forensics]
author: [1]
---

## 1. For/The-conspirasy
- Challenge give me 2 files : one is pcap, one is python code. I tried opening the pcap file to see what was there. At first glance, it contained TCP streams containing data in the form [x,y,z ...] with 2 types including numbers less than or equal to 100 and large numbers with 3 or more digits. 

    ![pic](/assets/posts/corCTF%202024/the-conspiracy/1.png)
    
    ![pic](/assets/posts/corCTF%202024/the-conspiracy/2.png)
- Read the python code file further. That's a way to encode and send data.

```python
import csv

sources, destinations, messages = [], [], []

with open('chatlogs.csv', mode='r') as file:
    csv_reader = csv.reader(file)
    for row in csv_reader:
        sources.append(row[0])
        destinations.append(row[1])
        messages.append(row[2])

def encrypt(message):
    messagenums = []
    for character in message:
        messagenums.append(ord(character))
    keys = []
    for i in range(len(messagenums)):
        keys.append(random.randint(10, 100))

    finalmessage = []
    for i in range(len(messagenums)):
        finalmessage.append(messagenums[i] * keys[i])

    return keys, finalmessage

for i in range(len(messages)):
    finalmessage, keys = encrypt(messages[i])
    print(finalmessage, keys)
    packet1 = IP(src=sources[i], dst=destinations[i])/TCP(dport=80)/Raw(load=str(finalmessage))
    send(packet1)
    packet2 = IP(src=sources[i], dst=destinations[i])/TCP(dport=80)/Raw(load=str(keys))
    send(packet2)
```

- The code performs three steps:

```
    1 - Read data from CSV file:

- Open chatlogs.csv.

- Read rows from CSV file and save values ​​to sources, destinations, and messages.

    2 - Encrypt function:

- Convert each character in message to ASCII code and save to messagenums.

- Create a list of keys containing random numbers from 10 to 100.

- Encrypt the message by multiplying each ASCII value in messagenums by the corresponding key in keys.

    3 - Send encrypted message and encryption key over the network:

- For each message in messages, encrypt the message.

- Create two packets:

    +  The first packet contains the encrypted message (finalmessage).

    + The second packet contains the encryption keys (keys).

- Send these packets over the network to their respective destinations using Scapy.
```
- To decode and get the original data, we do 2 steps: First, take the encrypted value and divide it by the key to get the original value, then convert the value from the corresponding ASCII value.Extract raw data from pcap file using tshark (I will find a way to filter it faster).

```
tshark -r challenge.pcap -Y "tcp" -T fields -e tcp.payload > chatlogs.csv.
```

- Then simply decode hex, filter them into 2 files and use code to decode them. This my code to filter (after decode hex value).

```python
import re

def process_lines(input_file, file_greater_than_500, file_less_than_or_equal_500):
    with open(input_file, 'r') as file:
        lines = file.readlines()

    with open(file_greater_than_500, 'w') as file1, open(file_less_than_or_equal_500, 'w') as file2:
        for line in lines:
            numbers = re.findall(r'\d+', line)

            if any(int(num) > 500 for num in numbers):
                file1.write(line)
            else:
                file2.write(line)

process_lines('chatlogs.csv', '1.txt', '2.txt')
```

- And this is decrypt code : 

```python
def decrypt(finalmessage, keys):
    original_message = []
    for i in range(len(finalmessage)):
        original_char_code = finalmessage[i] // keys[i]
        original_message.append(chr(original_char_code))
    return ''.join(original_message)

def read_numbers_from_file(filename):
    numbers = []
    with open(filename, 'r') as file:
        for line in file:
            line = line.strip()
            line = line.replace('[', '').replace(']', '').replace(' ', '')
            if line:  
                numbers.extend(map(int, line.split(',')))
    return numbers

finalmessage = read_numbers_from_file('1.txt')
keys = read_numbers_from_file('2.txt')

print(decrypt(finalmessage, keys))
```

FLAG : `corctf{b@53d_af_f0r_th3_w1n}`

## 2. For/Ilfiltration
The challenge requires answering some questions to get the flag, the challenge file is an event logs file. Since I am not familiar with using chainsaw, I only use 2 tools here, event viewer and EVTXeCMD.

```Q1: We'd like to confirm what the username of the main user on the target's computer is. Can you provide this information? ```

ANSWER: slice1 

SOLVE: Just go through some facts and we will have the answer to this question or check EID: 4798 (User's local group membership was enumerated.)

```Q2: Now, we'd like the name of the computer, after it was renamed. Ensure that it is entered in exactly how it is in the logs ```

ANSWER: lemon-squeezer 

SOVLE: We can see it in EID 4673 (A privileged service was called) or other, like Q1.

```Q3: Great work! In order to prevent their lemons from moulding, the lemonthinkers changed the maximum password age. What is this value? Please enter it as an integer number in days``` 

ANSWER: 83 

SOLVE: Check EID 4739 (Domain Policy was changed). Actually I didn't check EID 4739 immediately, I used another way which is to use EVTXeCMD to convert the evtx file to a csv file, then grep "age". You can see the 2 numbers are 42 and 83, but the correct answer is 83. Check the evtx file just to be sure.

```Q4: It seems that our targets are incredibly smart, and turned off the antivirus. At what time did this happen? Give your answer as a UNIX timestamp```

ANSWER: 1721946080 

SOLVE: This was a question that I was pretty clueless about. So when a member of my team answered it first, I knew I needed to check EID 4699 (A scheduled task was deleted)
    ![pic](/assets/posts/corCTF%202024/ilfiltration/Q4.png)
We can see here, in my local time it is 5:21:20 AM on the 26th, converted to UTC it is 22:21:20 on the 25th. Then just use Epoch Converter to convert to Unix time.

```Q5: The main lemonthinker, slice1, hasn't learnt from the-conspiracy and has (again) downloaded some malware on the system. What is the name of the user created by this malware? ```

ANSWER: notabackdoor 

SOLVE: Check EID 4672 (Special privileges assigned to new logon), we can see it in first line.
    ![pic](/assets/posts/corCTF%202024/ilfiltration/Q5.png)

```Q6: Finally, we'd like to know the name of the group that the user created by the malware is part of, which has the greatest security risk. What is this?```

ANSWER: Administrator 

SOLVE: In this ques, i use [Timeline Explorer](https://f001.backblazeb2.com/file/EricZimmermanTools/net6/TimelineExplorer.zip) and filter `Username=notabackdoor`, we can see in EID `4672 line : Administrative logon`, so the answer is Administrator.
    ![pic](/assets/posts/corCTF%202024/ilfiltration/Q6.png)

FLAG: `corctf{alw4y5_l3m0n_7h1nk_b3f0r3_y0u_c0mm1t_cr1m3}`

![meme](https://media.tenor.com/wT-64avQxegAAAAi/i-love-you-pepe.gif)