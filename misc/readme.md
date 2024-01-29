# Print It

```
nc 137.184.248.161 12345
```

### Soln

- It's a gcode
- https://ncviewer.com/
  
![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/9b781d98-e528-4f09-9284-a132c620d944)



# Russian Nesting Box

- A file was given

### Soln

- We had to use foremost many times

```bash
4648  unzip zip/00000613.zip
 4649  foremost box.jpg
 4650  ls
 4651  cd output
 4652  ls
 4653  unzip zip/00000613.zip
 4654  ls
 4655  foremost box.jpg
 4656  unzip zip/00000613.zip
 4657  ls
 4658  cd output
 4659  ls
 4660  unzip zip/00000613.zip
 4661  ls
 4662  unzip zip/00000613.zip
 4663  ls
 4664  foremost box.jpg
 4665  cd output
 4666  unzip zip/00000613.zip
 4667  ls
 4668  foremost box.jpg
 4669  ls
 4670  cd output
 4671  ls
 4672  tree
 4673  unzip zip/00000613.zip
 4674  ls
 4675  cat 000283
 ```
 
 - Flag

```bash
┌─[ ~/stuff/ctf/tutuelr/misc/russian/output/output/output/output/output] 
└─➜ cat 000283                                                                                                                                                                           [0]
tutelr{7h3r3_w3r3_2_m4ny_b0x35}
```


# Plotting

- 2 files were given
- .bmp and password file

#### Soln

- Passphrase had password to extract things from the flag.bmp

```bash
└─➜ cat passphrase.txt.txt | base64 -d 
101P455w0rd101_f0r_thE_F1L3
```

- Extract with steghide

```bash
└─➜ steghide extract -sf flag.bmp
Enter passphrase:
wrote extracted data to "values.txt".
```

- Looks like values from values.txt are some graph plot (also the chall name was plotting)
- Let's use gnu plot
- But it wasn't working with values `48, 47`
- Need to replace `,` with `' '`

- Python script

```py
with open('./values.txt', 'r') as file:
    lines = file.readlines()

for line in lines:
    modified_line = line.replace(',', ' ')
    print(modified_line.strip())  
   
```

- Run and save it in a file

```bash
 python3 p.py | tee try.txt   
 ```
 
 - Use gnuplot to plot the graph points
 
 ![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/be8a344a-1dee-4aac-a82f-22e429a84a3a)


- Scan the qr code to get the flag


# Extract The Flag

- A pcapng file was given

#### Soln

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/8a641410-59b0-40fc-8a84-954cbe279e72)

- We can see many get request with /flag parameter
- If we look out, they are unicode char
  - https://www.compart.com/en/unicode/U+0030    : for 0
  - https://www.compart.com/en/unicode/U+0031    : for 1
 
 ```bash
 └─➜ strings flag.pcapng | grep flag | cut -d "=" -f2 | cut -d " " -f1| awk '{print substr($0,length,1)}' | tr -d "\n"   
0111010001110101011101000110010101101100011100100111101100110001010111110110101101101110001100000111011101011111011000100011000101101110001101000111001001111001010111110111010101101110001100010110001100110000011001000011001101111101
```

- BInary to ascii

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/1e2a134e-8a70-4559-ab41-337d3d2841e9)


# Hidden Track

```
You need to find the flag and input it in format - tutelr{your-found-flag}
```

- As the title suggest, hidden track
- There's something hidden inside the video.
- mkvinfo

```bash
└─➜ mkvinfo edit.mkv                                                                                                                                                                     [0]
+ EBML head
<<--SNIP-->>
| + Track
|  + Track number: 2 (track ID for mkvmerge & mkvextract: 1)
|  + Track UID: 5593364456160941937
|  + Track type: audio
|  + Language: und
|  + Codec ID: A_AAC
|  + Codec's private data: size 16
|  + Default duration: 00:00:00.023219954 (43.066 frames/fields per second for a video track)
|  + Language (IETF BCP 47): und
|  + Audio track
|   + Sampling frequency: 44100
|   + Channels: 2
| + Track
|  + Track number: 3 (track ID for mkvmerge & mkvextract: 2)
|  + Track UID: 14698057073838088646
|  + Track type: audio
|  + Language: und
|  + Codec ID: A_PCM/INT/LIT
|  + Default duration: 00:00:00.040000000 (25.000 frames/fields per second for a video track)
|  + Language (IETF BCP 47): und
|  + Audio track
|   + Sampling frequency: 48000
|   + Channels: 2
|   + Bit depth: 16
|+ EBML void: size 1183
|+ Cluster
```

- So there are 2 tracks, 1- the song, and 2- our challenge imp file
- After extracting the 2nd audio
 - `mkvextract edit.mkv tracks 2:./2nd.wav`

- Opening in audacity, we find nothing, no spectogram, the audio was toooo low, so i amplified the audio
- `audactiy -> effect -> volume & compression -> amplify`

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/de7796ef-beee-4fa7-ab03-066a905a44f5)

- hearing it we can say it's a morse code
- Export audio and give it to morse code audio decoder
- `file -> export`

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/6ec56d41-f84a-4a8d-bdf6-6b5872396e68)


- Flag 

![image](https://github.com/heapbytes/tutelr-ctf-writeups/assets/56447720/4aba7ca2-afa8-4a31-9303-cbf89acc95f8)



