# Life Online - Challenge 6 (narcissism)

Again we need to workout who is **George**??

![george](https://user-images.githubusercontent.com/66634743/115957719-1dee8800-a515-11eb-9d1b-4e1886e09084.png)

Found him.🙂

Looking into his profile (the usual scroll to the bottom and work your way up). Look at all his tweets etc. Then I found this.

![base64](https://user-images.githubusercontent.com/66634743/115957723-23e46900-a515-11eb-94a0-bed8347f3bde.png)

Looks like he is soo confident that he tweeted his encrypted password on the internet.😆

At first i was looking too deep into it, trying to findout the hash type used:

![Hashid](https://user-images.githubusercontent.com/66634743/115957866-fcda6700-a515-11eb-8a98-ee58dac3fb9d.png)

I tried both these hashtypes:
```console
foo@bar:~$ hashcat -a0 -m2400 'aW1hbWF6aW5nMTIz' /usr/share/wordlists/rockyou.txt --force
foo@bar:~$ hashcat -a0 -m2410 'aW1hbWF6aW5nMTIz' /usr/share/wordlists/rockyou.txt --force
```
But no luck, then I went back to the basics(I was giving George too much credit) I tried `ceasar`, `base32` and then finally `base64`.

![base64](https://user-images.githubusercontent.com/66634743/115957989-6b1f2980-a516-11eb-9be3-229974b8e0c4.png)

### `ANSWER : imamazing123`
