# Disk,disk,sleuth! II
Category: Forensics </br>
AUTHOR: th3_bl1nd3r

## Description
Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: [dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/f63e4eba644c99e92324b65cbd875db6/dds1-alpine.flag.img.gz)</br>
## Solution
Unzip it!
```
gzip -d dds2-alpine.flag.img.gz
```
Use srch_strings
```
srch_strings dds1-alpine.flag.img | grep picoCTF
```
Then, I got this
`  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_ad5c96c0}`</br>
Flag:`picoCTF{f0r3ns1c4t0r_n30phyt3_ad5c96c0}`
