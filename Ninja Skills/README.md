# Walk-Through

<img src='https://user-images.githubusercontent.com/66634743/99852688-f0369900-2b9a-11eb-921c-76d0f3cd5ee4.png' height=200 width=200 align='right'>

### Try Hack Me : [THM](https://tryhackme.com/)<br/>
### Room Link   : [Ninja Skills](https://tryhackme.com/room/ninjaskills)


### These are just my approach to the problems but there are many possible ways, don't be restricted to only these. Always try to innovate and find work arounds. At the end of the day you are here to learn THE approach and not MY approach.

## Preparation
Lets create a file in the /tmp folder, this is a really good habbit to adoopt when working on a machine.

```console
[new-user@ip-10-10-182-44 /]$ mkdir /tmp/xxdil
```


## Find all the files
I will be copying all the file locations in the file **loc.txt**.Trust me this will save a lot of wasted hours in debugging. As we dont have to worry about the find command that much.

```console
[new-user@ip-10-10-182-44 /]$ find / -type f -regextype posix-extended -regex ".*/(8V2L|bny0|c4ZX|D8B3|FHl1|oiMO|PFbD|rmfX|SRSq|uqyw|v2Vb|X1Uy)" 2>/dev/null > /tmp/xxdil/loc.txt
```

A lot of things going on in this one command so lets break it down:

1) find / -type f
> search the whole machine for a file

2) -regextype posix-extended -regex
> search by using regex that we all are familiar with

3) ".*/(8V2L|bny0|c4ZX|D8B3|FHl1|oiMO|PFbD|rmfX|SRSq|uqyw|v2Vb|X1Uy)"
> it will find files with the following names

4) 2>/dev/null
> to ignore the 'Permission denied'

5) \> /tmp/xxdil/loc.txt
> finally transfer the output to loc.txt

![loc.txt](https://user-images.githubusercontent.com/66634743/99850867-94b6dc00-2b97-11eb-84e2-6cb8b74b4b75.png)

After doing this we can use ``$(cat tmp/xxdil/loc.txt)`` along with the other commands like almost like a pipe '|'. Lets see how ...

------

## Questions

#### Q) Which of the above files are owned by the best-group group(enter the answer separated by spaces in alphabetical order)
```console
[new-user@ip-10-10-182-44 /]$ find $(cat /tmp/xxdil/loc.txt) -group best-group
```

![Q1](https://user-images.githubusercontent.com/66634743/99850836-85379300-2b97-11eb-8862-8ded21b54a97.png)

---

#### Q) Which of these files contain an IP address?

[IP Regex](https://www.oreilly.com/library/view/regular-expressions-cookbook/9780596802837/ch07s16.html)
```console
[new-user@ip-10-10-182-44 /]$ find $(cat /tmp/xxdil/loc.txt) -exec grep -o -E "([0-9]{1,3}[\.]){3}[0-9]{1,3}" * {} \; 2>>/dev/null
```

![Q2](https://user-images.githubusercontent.com/66634743/99850852-8c5ea100-2b97-11eb-9029-810fcc06fc58.png)

**NOTE : Be careful of ``{} \;`` its not ``{}\;`` or ``{}\ ;`` , the position of the space matters**

Command : ``-exec <command> {} \;``

---

#### Q) Which file has the SHA1 hash of 9d54da7584015647ba052173b84d45e8007eba94
```console
[new-user@ip-10-10-182-44 /]$ sha1sum $(cat /tmp/xxdil/loc.txt) | grep '9d54da7584015647ba052173b84d45e8007eba94'
```

![Q3](https://user-images.githubusercontent.com/66634743/99850830-82d53900-2b97-11eb-8de2-e2be69eba7b7.png)

---

#### Q) Which file contains 230 lines?
This is a weird one as this file cant even be found, its probably not allowed to view this file. so there is a good elemination way.

```console
[new-user@ip-10-10-182-44 /]$ wc -l $(cat /tmp/xxdil/loc.txt)
```

![Q4](https://user-images.githubusercontent.com/66634743/99850872-984a6300-2b97-11eb-94e5-a8a4f651b8e5.png)

(THE ONLY FILE NOT IN THE LIST)

---

#### Q) Which file's owner has an ID of 502?

```console
[new-user@ip-10-10-182-44 /]$ ls -n $(cat /tmp/xxdil/loc.txt)
```

![Q5](https://user-images.githubusercontent.com/66634743/99852013-92558180-2b99-11eb-9fe0-5b9103a02a6f.png)

---

#### Q) Which file is executable by everyone?
```console
[new-user@ip-10-10-182-44 /]$ ls -la $(cat /tmp/xxdil/loc.txt)
```

![Q6](https://user-images.githubusercontent.com/66634743/99850817-7ea91b80-2b97-11eb-9d97-0455ad36df7f.png)

Executable files have atleast one  **x** as one of their permissions and also they are green in color

#### Thats all folks, CONGRATS! you made it to the end
