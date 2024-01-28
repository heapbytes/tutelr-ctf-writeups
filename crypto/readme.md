# Spoon

```
Agent S has a special spoon which can make this binary mess understandable. Find it and use it to understand what it says
```

### Soln

- the chall name also was a big hint

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/7fd11e05-f2ed-463f-b521-facc74de4649)


# invisible

```
Agent X was able to steal the flag from the Evil Corp. However the file seems to be empty. Help Agent R see the invisible flag
```

## Soln

- tried with stegsnow but no luck
- found the whitespace lang

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/ebc94690-1ec5-4e65-8be5-5920654e1694)


# Lorenz

```
Mr Lorenz, a member of MIG, was sending an encrypted message to prevent the message to be understood by Hitler. Agent B sniffed that message. However, he cannot decrypt it. Help Agent B uncover the truth.
```

### Soln

- It was morse code at start

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/42985516-4788-4d9a-b260-caa7304af419)

- The chall name again was a big hint

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/3304d40d-70a1-449a-a99c-88bd9e1f81d6)



# Colors

```
Agent H loves reporting to us in a weird cipher that only he and Agent C understands. However, currently Agent C is out on a mission. So, can you try deciphering the secret message he sent with all these colors?
```

### Soln

- it was hexahue cipher (did this a lot in many ctfs): https://www.dcode.fr/hexahue-cipher
- (it's a lengthy process so not doing it again, but i had copy buffer)
  - ```bash
    char(79)char(82)char(50)char(88)char(73)char(90)char(76)char(77)char(79)char(74)char(53)char(87)char(73)char(78)char(68)char(79)char(76)char(78)char(85)char(87)char(52)char(90)char(50)char(55)char(78)char(85)char(90)char(87)char(52)char(88)char(51)char(74)char(71)char(53)char(80)char(88)char(79)char(78)char(66)char(69)char(80)char(85)
  ```
- later it was base32

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/a22df799-e7a6-4e8a-a646-40c0d5e6621a)


















