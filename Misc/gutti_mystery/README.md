
# Misc: Gutti Mystery
<br>
Author: [redtrib3](https://github.com/redtrib3)
<br>


**Points**: 500
**Hint:** Follow the rabbit but don't fall into the rabbit hole(s).

**Challenge description:**
```
A stranger slipped this into my mailbox. How do they know my cat's name? We need to figure out who they are.

```
### Attachments:
gutti.png


## Solve

Open the image and its an Ai generated cat named gutti.

Run exiftools to check for metadata, and you see the Author listed as 'ReezMaxwell' with the comment 'Support me in Github.'

Now check for his github account:
https://github.com/ReezMaxwell 

The github has many information:
* The User has repo named InterceptAI
* User has connected his social accounts:
	* Twitter/X -[@reezmaxwell3301](https://twitter.com/reezmaxwell3301) 
	* Reddit - [u/Reez-Che3se](https://www.reddit.com/user/Reez-Che3se/) 

Check twitter account and you don't find anything useful.
Check Reddit and  this [post](https://www.reddit.com/user/Reez-Che3se/comments/1abbs6h/old_reddit_better/) stands out. (usage of terms like 'wayback' points towards [waybackmachine](https://archive.org/web/))

Use way back machine on reddit account, and you don't find anything useful. New twitter accounts can't be scraped. 

Now check for wayback archives for https://old.reddit.com/user/Reez-Che3se/ (since user stated he uses old.reddit.com)

One of the deleted post can be seen which has the flag.

#### Flag:
```plaintext
glitch{1ike_n33dle_1n_a_hay5tack} 
```
