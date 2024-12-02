--- 
title: "CTF@CIT 2024"
date: 2024-04-22T09:27:11+07:00
tags: [Forensics]
author: [1]
---

# Solution
## 1. Forensics/invoice 
- Challenge : <br>
    ![pic](/assets/posts/CIT@CTF/Forensics/Invoice/chall.png)

- Open file pdf,we can see:
    ![pic](/assets/posts/CIT@CTF/Forensics/Invoice/black.png)

- I use `pdftotext` to solve this. Just `pdftotext invoice.pdf` and we can read blacked out part.
    ![pic](/assets/posts/CIT@CTF/Forensics/Invoice/flag.png)

FLAG: *CIT{Sir_Swaggy}*

## 2. Forensics/Beep Boop
- Listening to the challenge file, a .wav file, I discovered it was morse code. Feeding it into the decoder, we get this string: INEVI63RENADIJSMFJJHKU3HKNVF4YJXHB4XOYL5. Use cyberchef, we get the flag :
    ![pic](/assets/posts/CIT@CTF/Forensics/Beep%20boop/flag.png)

FLAG: *CIT{q#@4&L*RuSgSj^a78ywa}*

## 3. Forensics/Sniff Sniff
- Challenge gave me a pcap file. I was pretty confused with the multiple streams from the pcap file. I was about to give up but I saw so many people solving it. So I went back and looked at it again, scrolled to the bottom and tried to follow the last tcp stream. I saw the password part looked like base64, tried putting it into cyberchef, I got the right result.
    ![pic](/assets/posts/CIT@CTF/Forensics/Sniff%20sniff/base64.png)

FLAG: *CIT{iJ5B9s#lAp6iBNi6JtQ8}*

## 4.Osint/I'm as cold as a wise man
- Challenge: <br>
    ![pic](/assets/posts/CIT@CTF/Osint/I'm%20as%20cold%20as%20a%20wise%20man/chall.png)

- Use GG lens, we can see some sites like this:
    ![pic](/assets/posts/CIT@CTF/Osint/I'm%20as%20cold%20as%20a%20wise%20man/GGlens.png)

- Check again by GG maps: 
    ![pic](/assets/posts/CIT@CTF/Osint/I'm%20as%20cold%20as%20a%20wise%20man/check.png)

FLAG: *CIT{coldfoot}*

## 5. Osint/Stalking 101
- Challenge: 
    ![pic](/assets/posts/CIT@CTF/Osint/Stalking%20101/chall.png)

- I was hanging around this challenge for a while, partly because I didn’t read the challenge properly. I tried searching all the social media platforms for the University of New Haven Chargers. I came up nothing, until I went to the university’s instagram, looked through the list of followers, and found him. 
    ![pic](/assets/posts/CIT@CTF/Osint/Stalking%20101/amos-insta.png)

- Searching his insta name, we get account X.
    ![pic](/assets/posts/CIT@CTF/Osint/Stalking%20101/amos-x.png)

FLAG: CIT{@mossyblack818}

## 6. Osint/Who even is that guy?
- Challenge: <br>
    ![pic](/assets/posts/CIT@CTF/Osint/Who%20even%20is%20that%20guy/chall.png)

- From Amos's insta, we can see person which Amos inspired:  
    ![pic](/assets/posts/CIT@CTF/Osint/Who%20even%20is%20that%20guy/amos-insta.png)

- The Osint challenge was the most frustrating one I have ever done. Hours spent in front of the computer, trying every angle in the photo but not a single clue about the person in the photo. I thought I would give up again. But no, I decided to try all the tools of the osintframework. And until I used Pimeyes, I was so overwhelmed, so happy that I jumped for joy. As we can see: 
    ![pic](/assets/posts/CIT@CTF/Osint/Who%20even%20is%20that%20guy/satoshi.png)

- With the blurred text, I immediately guessed that it was Satoshi - the person known as the creator of bitcoin.

FLAG: CIT{satoshi}

## 7. Osint/A conservative sandwich-heavy portfolio
- Challenge: <br>
    ![pic](/assets/posts/CIT@CTF/Osint/A%20conservative%20sandwich-heavy%20portfolio/chall.png)

- I had to wonder what the hell this challenge was. After digging through Amos' social media accounts, I suddenly remembered a picture I saw in the History section of a commit he made. I turned back to look at the picture, which I initially didn't think would be relevant, and I smiled when I saw it.

    ![pic](/assets/posts/CIT@CTF/Osint/A%20conservative%20sandwich-heavy%20portfolio/history.png)

    ![pic](/assets/posts/CIT@CTF/Osint/A%20conservative%20sandwich-heavy%20portfolio/commit.png)

- Just scan the qr code at the bottom of the book and you will get a link to the restaurant website.
    ![pic](/assets/posts/CIT@CTF/Osint/A%20conservative%20sandwich-heavy%20portfolio/scan-qr.png)

FLAG: CIT{Rubamba_restaurant}
