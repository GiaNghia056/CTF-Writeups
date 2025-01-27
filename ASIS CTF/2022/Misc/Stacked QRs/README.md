# Stacked QRS

## Description

My printer went crazy and printed a lot of [random QRs](https://asisctf.com/tasks/stacked_qrs_2cea284164de58de695f550ee25f1550a53cb4b4.txz) over each other. Luckily no important part of QRs is damaged. See if you can recover their data.

## Approach
- We have an image with many partially-visible QR Codes. You can search on Google "how to decode a partially visible QR code" and found a number of interesting articles such as [this](https://medium.com/@r00__/decoding-a-broken-qr-code-39fc3473a034) and [this](https://aioo.be/2015/07/28/Decoding-a-partial-QR-code.html).
- The most important thing we need to know to solve this challenge : Each QR Code must have 3 big squares(aka position markers) at the corner so that the QR scanner can determine the orientation of the QR Code. 
- I am aware that most of the QR Code in the only have  1 or 2 big squares, that means we have to create the position markers and insert those at the correct position.
  
After searching and fixing QR Codes, I found 3 QR Codes that weren't give us randomized characters strings.

- The first one is at the centre of the top
![](First.png)
```
ASIS{7iM3_70_f
```
- The second is at the centre of the image
![](Second.png)
```
ix_7Hi5_0ld_di
```
- The last is at the bottom right corner
![](Third.png)
```
R7y_PRin73R!!}
```
![](stacked_qrs.png)

Flag : `ASIS{7iM3_70_fix_7Hi5_0ld_diR7y_PRin73R!!}`