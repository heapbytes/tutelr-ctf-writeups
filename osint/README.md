# From The Past

```
We have some strong intel that a Ex-employee of The Helpers Company has got involved with the Drug Cartel. Find out who is the person?

Misson info - The Helpers company upload details of there employees on there website and if they removed his details you need to find it, cause what once uploaded onto the web can never be completly removed.

http://137.184.248.161
```
### Soln

- As the title suggest from the past, the first thing that comes into mind is wayback machine

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/8b8e52fb-bc25-4cf6-8403-6fa4cae8bee2)


# Commit

```
There has been a case - company information was leaked on our github repo find out who did it, also find their social media handles so that it will be easy to catch them

Mission - Find who leaked the information, also find other social media handles through osint.

https://github.com/l3urk/ourCompany
```

- Upon visiting the github repo, we find some website server stuff
- There were 3 branches and so manyyyyy commits, i read the desc again and saw that we need to find socials of the contributors
- Socials found
    - https://twitter.com/elisa_olsen2
    - https://instagram.com/elisa_olsen2
- The twitter had nothing, but instagram had nice post of flag
- It had youtube link

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/5f3d1bfe-9fb0-4856-95aa-26a35f80d328)


# RevSearch

```
Haruto Tanaka Just posted a picture of restaurant on his social media (he goes by the name of haruto_tanaka12 ) find out the name and place of the restaurant.

Note - The flag is available in full form i.e. tutelr{flag} you just need to paste it here.
```

## soln

- Social found: https://www.instagram.com/haruto_tanaka12
- If you are on chrome you can right click and search image with google
- Tbh, i was stuck at this link: https://tabelog.com/osaka/A2701/A270206/27078842/dtlrvwlst/B447145537/
- Anyway that website didn't had any reviews that was good to me
- Went to google reviews
- https://www.google.com/maps/place/Joryuken/@34.6525249,135.5055374,20z/data=!4m8!3m7!1s0x6000e70748b44bdf:0xe067473bf9a9c8ae!8m2!3d34.6524376!4d135.5055933!9m1!1b1!16s%2Fg%2F11glt67kml?hl=en-US&entry=ttu

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/f6613cc4-0106-43cc-b37c-6b41e0da90dd)

# In the Dark

```
We have found these two files on the computer of one of the biggest drug dealer. One of the file is encrypted can you decrypt it?
```
- There were 2 files given (bookmark.json, cipher.bin)

 ![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/22045c37-7f7a-4601-ab35-6db3fd494801)

- Many onion links
- One of the links (http://y3yhzvcqkwysmd6jajxtchnpxkit6ypyrvo4sv4udso3ijhk2hbojuad.onion) gives you rsa priv key

- priv key:

```bash

-----BEGIN PRIVATE KEY-----
MIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQDmTcvBlBNWUCZ+
49JkTBgUGx5H/sR6xZonMCKV/vQclJOMe4qVWeJ5UBM5Ya0aElB2t6IDQqstQUnc
C4BoPHBbZTcxEQqGGeQVeBMXix4ygRbb0P9QOkOdmqr4eHuJQrnzDGV7irUJq8JR
myucZrBjKA00TUF292586YscUSp/CUglz9YlqWnxrI8MB9m1SUklg1mU0E9yyAIF
K2CcuhfaF6D5dMNohCff7AVb+1FXxNtAj5THgwz+VgGXf2Wnow9ExqAKrXYjlxNm
XjqCROQEDeEeY6WCSIt95W1oWHGLUE97gFfYAMcjioOX9KzCKhAAIYHytdkXAeVF
HmQ8vU/xAgMBAAECggEABLlNR93x7JgNxhYFs311E/p/a0IgRRVnBU1BNFrrpmds
xFmnXMtgcBUSo99rRcjg4iJ/nfoA2VeIvIz22Ax/UHyZvnWnRdtjmIYjPB0kJCyO
K7mUdxCO4P1yatDL1eOqvT/AmCFe98EQZgyc/yMDFLGWXb+E63wFReYjbpQCn2Ln
I0xGg+9Jqctm14cUEPn+EQ1jCpfnwcERJcZ7NkXgVQtNKP0LJ7csyquuXokv/bQP
RNddsAQY5iYpENxUtl7U+/p8i2lXWZZ0otcshN6bkUtQ7qm1VF1jF1g26qBwwgqA
OpmFAQiCMnrCIpHQJ0SdG1JcYZkmq/RAeeKxrPD3fQKBgQD5UgAHNqbyhUb3h4S/
pIdNlQXFCp7eJ5+6qZ/+6RhbHvAT18+gyiTcQ6uynoQJRhFwijUaGfEBBCMKQCAM
QtCt5tnwhnoJx8v/4Maj4LTaa1w5d/LZwaHNAOXSxMDthEB2uq2lBZVpUlNebtBq
0LfyVCNoh99M93I5syhtSIrYvQKBgQDseV5vuIiQ1OOK3eRBnntqiQZMgmUs/X21
y7CFH3O5y103eR0iF9uzDJGiQWIK0Mxq37+lN2U208QvFrzLSWPPPV1f4kzkfhwQ
8S4EB/KyoZ6FIwJ8CgZmvwXvITb79hA5SZt/oYV16Qdq/XICmyw/fMT53AyIlIGj
c0R2VT9JRQKBgDebY2g4d0nWEfr5XdFEh+z01OGauc5Ati5y0L2RDZ6dKtyyIJvz
Gf+KlEv1cOuEljUsjiVxLcCVRJ9vp/Y0HMj8mRU9WRC/YC+E2akJYCzrDxm+OAr7
VfQcRCYbPhB7k8knX71TnnxsIS4JtzBrtus0euVAkLxg4DggTl75dAZdAoGBAOQd
IFA9ft/XvbiT3EDAlOVsUTs0/kysK7xXRWzlrkkoOD/vAX+F7FWIZmRTFjTAvrDK
LqE+EtEU70dNc8nWfgXIeG6qaupwDLr7LRyOXjybU8Oyxg7JzOsIkrzfGZ9s+rGI
pAw2z/uyU4mN+5EwBzsnLQyqjRyjxXrbEsvj6CzRAoGAFjRt5KBeJoa1/TzvKnas
xbDT1DCyEWGEI/dR1ipaUiHoJytnI/lGG13zOH/N3WQd1P7lzymjkowgf3SKoqcM
ybzN8UO1cVb3rgl+6KkzBvDGKzG+kQDG4hGOCnvDcJJCrq+b/E76cfuP105yGN4K
OZ19KB8bgzi6/YHBh0VExc4=
-----END PRIVATE KEY-----
```

- rest is pretty easy, the other file was cipher.bin
- Decrypt it with the rsa key

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/2765a6c7-99f0-494f-81f7-260d7eeb5db3)

# Bar Evolution

```
We have unauthorized access to a bar's live cctv footage steam. Find the location where the bar is situated and its old name before it got its current name.

Mission - Look at the footage, find the bar name, locate it, find its old name.

flag format -tutelr{the_old_name}

http://206.189.86.110

```

- Visiting the url, it says website is down
- Had to ffuf the website
- Found `/backups` dir
- ffuf'd again, nothing found, ffuf'd again with `.mp4, mkv, .php, .tar.gz, .zip, .html, .txt`
- Found a hit at `http://206.189.86.110/backups/backup.php`
- Googled: `yawcam default password`
![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/9f843858-329d-416e-9940-f7a556e61d4a)

- We find a zip, downloaded it, there was a video, took ss of it and google image search, found a twitch live stream
  
 ![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/38d6bd67-5323-4ae3-8f0a-1623ab560c71)

- Got the location
- The desc to submit old name of the bar
- I went through manyyyy websties before finding the answer

  ![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/0525dc37-6703-4187-a5e2-49116c0900aa)





















