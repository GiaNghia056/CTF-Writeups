# Pitter, Patter, Platters!
Category: Forensics </br>
AUTHOR: th3_bl1nd3r

## Description
'Suspicious' is written all over this disk image. Download [suspicious.dd.sda1](https://jupiter.challenges.picoctf.org/static/47f3cb40aed42fbd74fd644e11d08007/suspicious.dd.sda1)</br>
## Solution
Use [Autospy](https://www.autopsy.com/) and you will get this
![Autospy GUI](https://github.com/GiaNghia056/CTF-Writeups/blob/main/picoCTF/Forensics/Pitter%2C%20Patter%2C%20Platters/Screenshot1.png)
If you don't see the "-slack" file, do this first [view slack file in Autospy](https://security.stackexchange.com/questions/139479/uncover-data-in-file-slack)</br>

Click on `suspicious-file.txt` and I saw this
```
}61d907ec_3<_|Lm_111t5_3b{FTCocip
```
Reverse it and we got the flag!

Flag:`picoCTF{b3_5t111_mL|_<3_ce709d16}`
