# APPNOTE.TXT

## Description

Every single archive manager unpacks this to a different file...<br/>
[&darr;Attachment](https://storage.googleapis.com/gctf-2022-attachments-project/2551253642bde3066e55c9cc8e9b0b4aa77feadc00c81032da778e6f7c89907135dfc2611fd8617204720dbfadb31429ae11f6ecd202887f4ce99f2f53a3c5e8)

## Approach

Đầu tiên, unzip file `dump.zip`, thì nhận được 1 file `hello.txt` chứa nội dung

```There's more to it than meets the eye...```

By the way, [this video](https://www.youtube.com/watch?v=ld9RW3pxAKg) gives a really good overview on how to use The Sleuth Kit.

It seems that the first two partitions probably don't have anything interesting in it. Partition at index 002 begins at 2048. I used `fls -o 2048 dds2-alpine.flag.img` to check the contents of that partition.

```text
d/d 11: lost+found
r/r 12: .dockerenv
d/d 20321:      bin
d/d 4065:       boot
d/d 6097:       dev
d/d 2033:       etc
d/d 26417:      home
d/d 8129:       lib
d/d 14225:      media
d/d 16257:      mnt
d/d 18289:      opt
d/d 16258:      proc
d/d 18290:      root
d/d 16259:      run
d/d 18292:      sbin
d/d 12222:      srv
d/d 16260:      sys
d/d 18369:      tmp
d/d 12223:      usr
d/d 14229:      var
V/V 32513:      $OrphanFiles
```

I figured the `root` directory would be a good starting point. `root` has control to everything and CTFs store important things in places with admin permissions. `fls -o 2048 dds2-alpine.flag.img 18290`:

```text
r/r 18291:      down-at-the-bottom.txt
```

It took me a while to figure out how to use the `icat` command but eventually, `icat -o 2048 dds2-alpine.flag.img 18291` worked:

```text
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

## Flag

picoCTF{f0r3ns1c4t0r_n0v1c3_69ab1dc8}
