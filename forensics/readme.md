# Drug

```
A drug dealer was found sending this image to one of this clients. You are tasked with finding his intentions.
```

### Soln

- Stegseek 

```bash
└─➜ stegseek drug.jpg                                                                                                                                                                    [0]
StegSeek 0.6 - https://github.com/RickdeJager/StegSeek

[i] Found passphrase: "mahalkita"
[i] Original filename: "flag.txt".
[i] Extracting to "drug.jpg.out".


└─➜ cat drug.jpg.out                                                                                                                                                                     [0]
tutelr{5+e9@no9r@phy_i+_w@5}
```


# Suspicious

```
We found a suspicious audio file, however we can't find anything interesting. Can you find something?
```

#### Soln

- Viewing it in spectogram mode in audacity gives flag

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/8f8a4143-bd14-4c1c-964a-d13c5bec5caa)


# Onion

```
Agent Z got his hands on this mysterious onion which he claims to be making him shed a lot of tears. Can you investigate the cause?
```

- At start we need to stegseek the flie to get a .zip

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/e6820b53-1a97-4936-983d-d68d26d6adc0)

- As the chall name suggest onion, we need to unzip many layers.zip
- ok after few unzip there's a password needed for flag.zip

- I used john to crack the hash of the zip

```bash
└─➜ zip2john layer.zip > hash                                                                                                                                                          [130]
ver 1.0 efh 5455 efh 7875 layer.zip/flag.txt PKZIP Encr: 2b chk, TS_chk, cmplen=34, decmplen=22, crc=5A346575


└─➜ john --wordlist=/usr/share/wordlists/rockyou.txt hash                                                                                                                                [0]
Using default input encoding: UTF-8
Loaded 1 password hash (PKZIP [32/64])
Will run 16 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
scoobydoo        (layer.zip/flag.txt)
1g 0:00:00:00 DONE (2024-01-29 10:33) 50.00g/s 1638Kp/s 1638Kc/s 1638KC/s 123456..dumbo
Use the "--show" option to display all of the cracked passwords reliably
Session completed

```

- Password : `scoobydoo`
- Flag

```bash
└─➜ unzip layer.zip                                                                                                                                                                      [0]
Archive:  layer.zip
[layer.zip] flag.txt password:
 extracting: flag.txt


└─➜ cat flag.txt                                                                                                                                                                         [0]
tutelr{y0u_p33l3d_m3}
```

# Communication

```
Mr Rabit was suspected of sending our confidential flags to a rival spy firm's webserver. So, Agent W sniffed Mr. Rabit's conversation with the webserver. Can you find out the flag he compromised?
```

- used strings and found few flag parameters

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/543b28a2-4ca2-44bc-85eb-fa3b83b6986e)

- Flag

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/a264c419-92f4-4c55-931e-2d326a517c53)

- There were many rabbit holes, but `tutelr{r488i7_i$_h3r3}` was more sensible.
- that was the flag.


# Maze

```
Confidential Data Leaks Corp. have stored their most sensitive data in the heart of their newest facility. However, that facility is rumored to be a terrifying maze. Can you get to the heart of the maze, without getting lost and retrive that sensitive data for us?
```

- this was a time CONSUMING challenge

- there were 4 zip inside maze

## Earth had key3

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/f5cba463-5bfe-4907-87d2-ca8be0e9d15e)

- Key3 was found in earth


## Fire had key 1

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/3623972c-3fa9-493f-9822-f60c43b05925)


## water had key 2

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/08b5eb10-cc5a-43d9-a09f-6e74b8afdfc0)


## Final flag (wind)

- inside wind/room-2
- we can see 2 zip, hidden-room and confidential-room.zip
- Password cracked of hidden-room.zip with john (margarita)

```bash
Instructions:
1. Get the three parts of the key
2. Stitch them together
3. Use the final key to enter the confidential-room

Example:
Key-p1 : key1_
Key-p2 : key2_
Key-p3 : key3
Final Key: key1_key2_key3
```

- we found all 3 keys
- final key : `The_Twelve_Shadows_That_Always_Watches`

- Flag
  
![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/c3ffe658-4851-47ae-9564-09b5a0a23e93)




































