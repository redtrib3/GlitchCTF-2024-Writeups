
# Web: The WheelBarrow

Author: [redtrib3](https://github.com/redtrib3/)
<br>

**Points**:  400
**Hint:**  My favourite icecream is "cookies" and cream.

**Challenge description:**
```
Can you login as admin? I don't think so. 
But what if I told you about a sizzling sensation that doesn't require passwords? Step right up to WheelBarrow's BBQ.

 http://glitchctf.games:64200/
 ```


## Solve

Register for an account and login, the dashboard says 'no flag for you'.
The description hints towards privilege escalation to admin.

Checking cookies, there is an `isAdmin` cookie set with base64 encoded value.

Decode the base64: 
`eyJhZG1pbiI6MH0=`
Plaintext:
```json
{"admin":0}
```

Set the key value to 1 and re-encode the string, set the cookies to new value and reload the page to escalate to admin.

#### Flag:
```plaintext
GLITCH{h1dd3n_pr1v1lege_5f4dc}
```
