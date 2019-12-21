# X-MAS CTF 2019 – Dox the Yak

* **Category:** OSINT
* **Points:** 50

## Challenge

> Santa had some trouble getting info about a weird internet dude nicknamed yakuhito.<br>
Help him answer the following questions and you will be rewarded ;)<br>
Question #1: What's yakuhito's dream car?<br>
Question #2: What's yakuhito's real name?<br>
Question #3: What phone model is yakuhito currently using?<br>
Example flag: X-MAS{ch3vrolet_corvett3_john_doe_galaxyj7pro}<br>
Note: The car's model must be written in leetspeak<br>

## Solution

Yakuhito's Twitter has two of the answers.<br>
https://twitter.com/yakuh1t0/status/1204505279863410689?s=20<br>
This has his name - Mihai Dancaescu<br>
<br>
https://twitter.com/yakuh1t0/status/1200409467952742401<br>
This has the car's company and model already in leet speak -  T3SL@ Cyb3rtruck<br>

Googling his Name, I stumbled upon his keybase account :D <br>
https://keybase.io/yakuhito<br>
There his device is listed as an OnePlus<br>

Note:
*The flag was to be entered in lowercase (it was mentioned in the discord channel)*<br>
```
X-MAS{t3sl@_cyb3rtruck_mihai_dancaescu_oneplus7pro}
```


