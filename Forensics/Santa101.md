# X-MAS CTF 2019 – Santa's Forensics 101

* **Category:** Forensics
* **Points:** 25

## Challenge

> Santa needs the help of an experienced forensics analyst. But first, he has to make sure that you are worthy.

>Given: X-MAS_Flag2.zip

## Solution

`unzip X-MAS_Flag2.zip`

On checking the file type of the resulting png, we find that it is a zip archive as well.

`unzip X-MAS_Flag2.png`

On navigating to the extracted folder, we find an image called logo2.png

`cd hidden_data_dt`
`strings logo2.png`

This yields the flag.

```
X-MAS{W3lc0m3_t0_th3_N0rth_Pol3}
```
