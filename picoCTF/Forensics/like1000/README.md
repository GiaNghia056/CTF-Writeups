# like1000
Category: Forensics </br>
AUTHOR: th3_bl1nd3r

## Description
This [.tar file](https://jupiter.challenges.picoctf.org/static/52084b5ad360b25f9af83933114324e0/1000.tar) got tarred a lot.</br>
## Solution
After decompresed `1000.tar` file, I get `999.tar` file. Therefore, I think it would have about 1000 tar files to decompress and I use Python to extract the files.
```python
import tarfile
for i in range(1000,-1,-1):
	filename = str(i) + ".tar"
	tar = tarfile.open(filename)
	tar.extractall()
	tar.close()
```
Another way is using Linux Bash script
```bash script
for i in {1000..1}; do tar -xf $i.tar; done
```
Then, I got this
![like1000_flag.png](https://github.com/GiaNghia056/CTF-Writeups/blob/main/picoCTF/Forensics/like1000/flag.png)

Flag:`picoCTF{l0t5_0f_TAR5}`
