# X-MAS CTF 2019 – Robin's Wish

* **Category:** Cryptography
* **Points:** 119

## Challenge

> Santa tried using public key cryptography to secure his letters, but his plan turned out to be a failure! After deleting his private keys, one of his elves found an encrypted letter from a child named Robin. Asking Robin what he wants for Christmas would be unprofessional, so the elf asked you to decrypt the letter. He also gave you access to a more basic copy of Santa's service.

>Help Santa decrypt Robin's letter and you will definitely not be on the 'naughty' list this year!

## Solution

*(Details on service set up to be added, preferrably with screenshots to demonstrate effect on certain input)*

The name of the protagonist, "Robin" and the hosted encryption oracle suggest that the Rabin's encryption algorithm is at work. We also know that decrypting Robin's encrypted letter (option 1337 of the service) gives us our flag.

We find the modulus n by narrowing down on its number of digits (by sequentially giving 10^1, 10^2, 10^3 and so on as input to the oracle, and checking when the resultant is no more the perfect square of the input) and making use of the fact that the perfect square - resultant is a multiple of n.

Now that we have n, we use fermat factorization to find its prime factors, p and q. Then using Chinese remainder theorem, we find the 4 possible plaintexts out of which one of them gives the flag using the script below.

```
import codecs
import gmpy2
from Crypto.Util.number import *

def fermat_factor(n):
    assert n % 2 != 0

    a = gmpy2.isqrt(n)
    b2 = gmpy2.square(a) - n

    while not gmpy2.is_square(b2):
        a += 1
        b2 = gmpy2.square(a) - n

    p = a + gmpy2.isqrt(b2)
    q = a - gmpy2.isqrt(b2)
    return int(p), int(q)

n = 17150948086006853589591993610767711903029749167719666894975279147137565458158322238156960171902445590052801235253045792984069360111140927413022122124794074712372666903008787076313652986830735891457266804676322092444602549744787142273336096470832931113698218899620404912992099097015038863714351384075897287966440984446042594077540591489657561322101444523900312965276873402643875552954061610698504308548301539759131150366661281651087532807818489741520557925049746199503634928208501195328273501508911193754334803125090416259379171809642283452935819219835361791073290320084884025929676790915171638558685021113076310785793
(p, q) = fermat_factor(n)

c = 5246714854725113346502630730554686769362460460024400516326377174582640581617340710826138679480295436331234207963461529282935208997428624889011546696260124285562972903578214766887742626982299066940742233276099045101758754159876941858460523496511762589246629169421146451313958152520373812386003438537883174073207043740529956867073333127369639805390764236392611481831378501794578225519437884851468056175989860754859991595520574160634748280117377466913600749771441057921368040518728100659821105472644679642632075853735222383344108215588801856832216683298621306263529594333455011123877122301231151688000552994875142333423
c_root_q = pow(c, ((q+1)//4), q)
c_root_q_neg = q - c_root_q
c_root_p = pow(c, ((p+1)//4), p)
c_root_p_neg = p - c_root_p
b1 = inverse(q, p)
b2 = inverse(p, q)
x = (c_root_p*b1*q + c_root_q*b2*p) % n
y = (c_root_p*b1*q + c_root_q_neg*b2*p) % n
z = (c_root_p_neg*b1*q + c_root_q*b2*p) % n
w = (c_root_p_neg*b1*q + c_root_q_neg*b2*p) % n
x = long_to_bytes(x)
y = long_to_bytes(y)
z = long_to_bytes(z)
w = long_to_bytes(w)
print(x)
print(y)
print(z)
print(w)
```

```
X-MAS{4cTu4lLy_15s_Sp3lLeD_r4b1n_n07_r0b1n_69316497123aaed43fc0}
```



