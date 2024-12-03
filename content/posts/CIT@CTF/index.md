--- 
title: "CTF@CIT"
date: 2024-04-22T09:27:11+07:00
tags: [Forensics]
author: [1]
---

## 1. Forensics/invoice 
- Challenge :
    ![pic](https://live.staticflickr.com/65535/54179423817_805cdbb0d4_o.png)

- Open file pdf,we can see:
    ![pic](https://live.staticflickr.com/65535/54180307111_66dec1503e_b.jpg)

- I use `pdftotext` to solve this. Just `pdftotext invoice.pdf` and we can read blacked out part.
    ![pic](https://live.staticflickr.com/65535/54180307091_23088dbe35_b.jpg)

FLAG: `CIT{Sir_Swaggy}`

## 2. Forensics/Beep Boop
- Listening to the challenge file, a .wav file, I discovered it was morse code. Feeding it into the decoder, we get this string: INEVI63RENADIJSMFJJHKU3HKNVF4YJXHB4XOYL5. Use cyberchef, we get the flag :
    ![pic](https://live.staticflickr.com/65535/54180579323_7fe9536f1b_b.jpg)

FLAG: `CIT{q#@4&L*RuSgSj^a78ywa}`

## 3. Forensics/Sniff Sniff
- Challenge gave me a pcap file. I was pretty confused with the multiple streams from the pcap file. I was about to give up but I saw so many people solving it. So I went back and looked at it again, scrolled to the bottom and tried to follow the last tcp stream. I saw the password part looked like base64, tried putting it into cyberchef, I got the right result.
    ![pic](https://live.staticflickr.com/65535/54180579563_95a86a283f_b.jpg)

FLAG: `CIT{iJ5B9s#lAp6iBNi6JtQ8}`

## 4.Osint/I'm as cold as a wise man
- Challenge: <br>
    ![pic](https://live.staticflickr.com/65535/54179424427_3668f4f91c_o.png)

- Use GG lens, we can see some sites like this:
    ![pic](https://live.staticflickr.com/65535/54179424452_3751f829e4_b.jpg)

- Check again by GG maps: 
    ![pic](https://live.staticflickr.com/65535/54180746640_f865089a7b_b.jpg)

FLAG: `CIT{coldfoot}`

## 5. Osint/Stalking 101
- Challenge: 
    ![pic](https://live.staticflickr.com/65535/54180580138_1dac82ede0_o.png)

- I was hanging around this challenge for a while, partly because I didn’t read the challenge properly. I tried searching all the social media platforms for the University of New Haven Chargers. I came up nothing, until I went to the university’s instagram, looked through the list of followers, and found him. 
    ![pic](https://live.staticflickr.com/65535/54180580113_36ca64cecf_b.jpg)

- Searching his insta name, we get account X.
    ![pic](https://live.staticflickr.com/65535/54180307831_68242def00_b.jpg)

FLAG: `CIT{@mossyblack818}`

## 6. Osint/Who even is that guy?
- Challenge: <br>
    ![pic](https://live.staticflickr.com/65535/54179461537_907c6012df_o.png)

- From Amos's insta, we can see person which Amos inspired:  
    ![pic](https://live.staticflickr.com/65535/54179461552_294f2dbe28_b.jpg)

- The Osint challenge was the most frustrating one I have ever done. Hours spent in front of the computer, trying every angle in the photo but not a single clue about the person in the photo. I thought I would give up again. But no, I decided to try all the tools of the osintframework. And until I used Pimeyes, I was so overwhelmed, so happy that I jumped for joy. As we can see: 
    ![pic](https://live.staticflickr.com/65535/54180616583_e6533438f5_b.jpg)
- With the blurred text, I immediately guessed that it was Satoshi - the person known as the creator of bitcoin.

FLAG: `CIT{satoshi}`

## 7. Osint/A conservative sandwich-heavy portfolio
- Challenge: <br>
    ![pic](https://live.staticflickr.com/65535/54180579873_53e5afdb6a_o.png)

- I had to wonder what the hell this challenge was. After digging through Amos' social media accounts, I suddenly remembered a picture I saw in the History section of a commit he made. I turned back to look at the picture, which I initially didn't think would be relevant, and I smiled when I saw it.

    ![pic](https://live.staticflickr.com/65535/54180307546_f41562d314_b.jpg)

    ![pic](https://live.staticflickr.com/65535/54179424277_0e2539c275_o.png)

- Just scan the qr code at the bottom of the book and you will get a link to the restaurant website.
    ![pic](https://live.staticflickr.com/65535/54179424242_297f05517e_b.jpg)

FLAG: `CIT{Rubamba_restaurant}`

![meme](https://media.tenor.com/wT-64avQxegAAAAi/i-love-you-pepe.gif)