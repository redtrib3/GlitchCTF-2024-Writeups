# Forensics: It's Deeper than that
Author: [some1hing](https://github.com/SOME-1HING)
<br>

**Points**: 200
**Hint:** https://www.mezzacotta.net/garfield/?comic=34


**Challenge description:**
```
Garfield: As a cat, I love to explore the unknown.  
Garfield: {looks behind himself} Nothing behind me..  
Garfield: That's enough exploring for one day..
```

### Attachments: 
challenge.jpg
passwords.txt

## Solve

You're provided the image of a random garfield comic.

Trying to extract hidden files using steghide, you don't know the password.

```bash

└──╼$ steghide extract -sf challenge.jpg
Enter passphrase: 
steghide: could not extract any data with that passphrase!

```

The attachment of passwords.txt files hints towards bruteforce.

use the `stegseek` tool (or any other steg bruteforcing tool) to bruteforce the password of the stego file.
  
  ```bash
└──╼ $stegseek challenge.jpg -wl passwords.txt 
StegSeek 0.6 - https://github.com/RickdeJager/StegSeek

[i] Found passphrase: "sobaka"

[i] Original filename: "challenge.zip".
[i] Extracting to "challenge.jpg.out".

└──╼ $file challenge.jpg.out 
challenge.jpg.out: Zip archive data, at least v2.0 to extract, compression method=deflate

```

Unzipping the zip file, you get the same zip file again, this is a loop. use a script (or manually for around ~ 30 times) to unzip it.

script:
```bash
#!/bin/bash

mv challenge.jpg.out challenge.zip

# 100 cause we don't exactly know how many times.(high num)
for i in {1..100}; do
    unzip -o challenge.zip
done

```

After executing the script, you get the flag.txt in the current directory.

#### Flag:
```plaintext
GLITCH{L3t_It_Burn}
```
