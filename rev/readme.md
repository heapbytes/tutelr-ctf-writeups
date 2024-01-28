# PrintFlag

```
Agent J knows Java a bit, so be wary of how you print the flag. Interestingly, .class file can run on any platform if you know how to.
```
### Soln

- The class print half flag, `string` will help get full flag

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/0f78eb0b-c34d-4083-9759-32e2952a2676)

- Flag : `tutelr{J@v@_i$_7h3_m0$7_p0pul4r_l4ngu4g3}`

# Run Me

```
Mr. Denis recently started learning C Language, so he often keeps his secret information in form of C programs. You are tasked with uncovering the secret he hid in this file.
```

### Soln

```bash
└─➜ strings run-me | grep -i tut                                                                                                                                                       [130]
tutelr{$33m$_lik3_y0u_kn0w_h0w_70_run_m3}
```

# Tricky

```
Inspired by Mr. Denis, Agent C also developed the habit of storing important information in form of C programs. He however, being a spy, is more sneaky in doing so. Can you uncover his tricky secret?
```

### SOln

- Running it gave a flag, but not in correct order
- Running it in ghidra, we see main functions
- going through those functions serially, we can get the actual flag in order 
- Flag: `tutelr{0bFu$[7i0n_i$_7ri[ky}`


# Trust

```
Sometimes you need to gain the trust of the security system to infiltrate into their strong hold. Use your skills, to gain the trust of the Guard.

nc 206.189.155.222 12345
```

### SOln

- A file was given (.py)
- Imp function:

```py
def get_correct_password():
	temp="RUUTPQRU"
	res=""
	for x in temp:
		res+=(chr((ord(x)-64)<<2))
	return res
```

- Running tha gives us password

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/861bffa8-8b8e-4440-871e-b63e82c0bb7c)

- (service was down, i made this, but m sure it looked like this: )
  
```bash
nc 206.189.155.222 12345
Enter Password: HTTP@DHT
Flag: tutelr{flag???} #i dont remember flag now
```









