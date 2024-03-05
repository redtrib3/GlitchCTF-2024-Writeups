
# Forensics: Sniff
Author: [redtrib3](https://github.com/redtrib3)
<br>

**Points**: 300
**Hint:** `http.request.method=="POST"`

**Challenge description:**
```
Some script kiddie keeps harassing us with his silly bruteforce attacks.
```

#### Attachments:
capture.pcapng


## Solve

We are provided with a pcapng file, Use wireshark/tshark to analyze the packets.

The packets are mostly HTTP packets inside an internal network. with some ICPM packets. Looking through each packets, we find that there are many GET Packets (directory bruteforce) with only two POST requests at the end.

The POST is a login to login.php, check tcp stream data and the flag is used as password for login.

```http
POST /login.php HTTP/1.1
Host: ecorpbank.co
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:102.0) Gecko/20100101 Firefox/102.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://ecorpbank.co/login.php
Content-Type: application/x-www-form-urlencoded
Content-Length: 72
Origin: http://ecorpbank.co
DNT: 1
Connection: keep-alive
Upgrade-Insecure-Requests: 1
 
user=administrator&pass=GLITCH%7Bth3_g00d_0ld_sn1ff_1ba27%7D&login=Login

```

URL decode the password, or replace the `%7B` with the brackets and submit the flag!

#### Flag:
```plaintext
GLITCH{th3_g00d_0ld_sn1ff_1ba27}
```
