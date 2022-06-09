# Disk,disk,sleuth! II
Category: Forensics </br>
AUTHOR: th3_bl1nd3r

## Description
All we know is the file with the flag is named `down-at-the-bottom.txt`... Disk image: [dds2-alpine.flag.img.gz](https://mercury.picoctf.net/static/544be9762e9f9c0adcbeb7bcf27f49a2/dds2-alpine.flag.img.gz)</br>
## Solution
Unzip it!
```
gzip -d dds2-alpine.flag.img.gz
```
I try to use srch_strings but I ain't get nothing!</br>
Instead, I use `mmls`
```
mmls dds2-alpine.flag.img
```
and get this 
```
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000262143   0000260096   Linux (0x83)
```
Therefore, I use `fls -r` to find the 'down-at-the-bottom.txt'
```
fls -r dds2-alpine.flag.img -o 2048 | grep 'down-at-the-bottom.txt'
```
and get this
```+ r/r 18291:	down-at-the-bottom.txt```
</br>
Use `icat` to cat the data at offset `18291`
```icat dds2-alpine.flag.img -o 2048 18291```
Hooray!!
```
_     _     _     _     _     _     _     _     _     _     _     _     _  
  / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \ 
 ( p ) ( i ) ( c ) ( o ) ( C ) ( T ) ( F ) ( { ) ( f ) ( 0 ) ( r ) ( 3 ) ( n )
  \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/ 
   _     _     _     _     _     _     _     _     _     _     _     _     _  
  / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \ 
 ( s ) ( 1 ) ( c ) ( 4 ) ( t ) ( 0 ) ( r ) ( _ ) ( n ) ( 0 ) ( v ) ( 1 ) ( c )
  \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/ 
   _     _     _     _     _     _     _     _     _     _     _  
  / \   / \   / \   / \   / \   / \   / \   / \   / \   / \   / \ 
 ( 3 ) ( _ ) ( 6 ) ( 9 ) ( a ) ( b ) ( 1 ) ( d ) ( c ) ( 8 ) ( } )
  \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/   \_/ 
```
</br>
Flag:`picoCTF{f0r3ns1c4t0r_n0v1c3_69ab1dc8}`
