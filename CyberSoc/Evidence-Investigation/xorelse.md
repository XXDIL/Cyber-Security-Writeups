# Evidence Investigation - Challenge 15 (xorelse)

I am pretty confortable with XOR's as i have done many projects related to it but if you are new all you need to know is that this is a simple `single byte XOR cipher`.

### Example
This means that each letter is XORed with a specific key, so if the cipher text was '5670' and the key was suppose 't' then we would do the following :
```
5 XOR t = A
6 XOR t = B
7 XOR t = C
0 XOR t = D
```
hence the answer would be 'ABCD'.

### Brute

So we will need to brute force this, as I assumed that the key was 't'. In reality the key coulf be any of the 255 [ASCII](https://theasciicode.com.ar/) characters.

I wrote the following python script to bruteforce the answer:

```python
from pwn import *

c = "QeOhnsr{KuZu)("

for i in range(256):
	m = xor(c, i)
	print(m)
```

This works but there is a lot of noise in the output

### Optimised Brute

Notice the following from the above implementation:

- After i = 64 there is only noise
- most characters are \x.. (which cant be typed) 

```python

from pwn import *

c = "QeOhnsr{KuZu)("
for i in range(64):
	m = xor(c, i)

	if "\\x" in str(m):
		continue

	print(m)

'''
b'QeOhnsr{KuZu)('
b'PdNiorszJt[t()'
b'SgMjlqpyIwXw+*'
b'RfLkmpqxHvYv*+'
b'T`Jmkvw~Np_p,-'
b'WcInhut}Ms\\s/.'
b'VbHoitu|Lr]r./'
b'YmG`f{zsC}R}! '
b'XlFagz{rB|S| !'
b'ZnDcexyp@~Q~"#'
b"_kAf`}|uE{T{'&"
b"^j@ga|}tDzUz&'"
b'Au_x~cbk[eJe98'
b'Cw]z|a`iYgHg;:'
b'Bv\\{}`ahXfIf:;'
b'Eq[|zgfo_aNa=<'
b'DpZ}{fgn^`O`<='
b'GsY~xedm]cLc?>'
b'I}WpvkjcSmBm10'
b'H|VqwjkbRlCl01'
b'J~Tsuhi`PnAn23'
b'MyStrongWiFi54'    <-- right here
b'LxRusnofVhGh45'
b'O{QvpmleUkDk76'
b'NzPwqlmdTjEj67'
'''
```

*This is probably not the best method to solve this question its the one where you learn the most.*

### `ANSWER : MyStrongWiFi54`