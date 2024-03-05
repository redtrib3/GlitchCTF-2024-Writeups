
# Misc: Commitment Issues
Author: [redtrib3](https://github.com/redtrib3)
<br>

**Points**: 500
**Hint:** None

**Challenge description:**
```
🔒 Keep Your Notes Secure with NotesCrypt

Tired of worrying about your notes falling into the wrong hands? Say hello to NotesCrypt – the ultimate encrypted notetaking app!

Don't trust us? run your own server. Download our source code below 👇
Note: flag format is `glitch{}`.
```

### Attachments:
notescrypt_src.zip


## Solve

Unzip the src file and you're provided with the source code of a Django Application.

LICENSE, README.md and most importantly the existence of .git/ folder shows that this is a git Repository.

#### Enumerating git:

##### Check for branches:
`git branch`
	=> returns 5 branches including main.
	
```bash
	* master
	  notescrypt-Bighetti
	  notescrypt-Dinesh
	  notescrypt-Gilfoyle
	  notescrypt-Richard
```

##### Check logs in each branch.
 ```bash
 git log <branch_name>
```

Checking the logs in master, at the end you see the commit  - **3d6b948c9978eb3b0fc3a9145e31b784fd67b7ab**

use `git show` to show the changes in that commit:

output:
`<the flag in red as its deleted>`



#### Flag:
```plaintext
glitch{1dd8d19091e360889fa107e22c3a9ead} 
```
