## TASK 2 : TIP-OFF

Go ahead and download the file 

```console
foo@bar:~$ wget 'https://raw.githubusercontent.com/OsintDojo/OsintDojo.github.io/d846483eb41dd4fdb6d00ac84ecdb4a66be6a191/TryHackMe/Sakura/sakurapwnedletter.svg'

foo@bar:~$ ls
# sakurapwnedletter.svg
```

Then as mentioned in the Instructions tab of the question `You might find information such as when a photo was created, what software was used, author and copyright information, as well as other metadata significant to an investigation.` 

Which tool can help us do this?
Ans : `exiftool`

```console
foo@bar:~$ exiftool sakurapwnedletter.svg
```

This will give the following output : 

![exif](https://user-images.githubusercontent.com/66634743/115604105-0b483900-a2f2-11eb-94fd-b43fc0b076e0.png)


As we can see there is nothing interesting at first, but looking at it carefully we can see the following line:

`Export-filename                 : /home/SakuraSnowAngelAiko/Desktop/pwnedletter.png`

As we know the usernames can be found in the `/home` directory.

**FLAG 1 =  SakuraSnowAngelAiko**

------ 

Then just for fun I converted the binary numbers to ASCII to see what it would say.

Spolier allert : `A picture is worth 1000 words but metadata is worth far more`
