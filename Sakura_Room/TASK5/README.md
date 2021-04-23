# TASK 5 : TAUNT

### 1) What is the attacker's current Twitter handle?

From the [image](https://github.com/XXDIL/Try-Hack-Me/blob/main/Sakura_Room/TASK5/taunt.png) provided we can see that there is a handel called `@AikoAbe3` a quick google seearch leads us to this twitter page:

![AikoAbe3](https://user-images.githubusercontent.com/66634743/115868096-f92edd80-a44c-11eb-9d4d-2bcd4308b9f7.png)

### 2) What is the URL for the location where the attacker saved their WiFi  SSIDs and passwords?

This one is a little tricky, there are many dead ends to this but i'll share my approach.

Scrolling to the bottom of her page we see the following inage: ![img](https://pbs.twimg.com/media/EsdhaUSVkAAM803?format=png&name=small)

I spent a long time looking into:
- what are AP's? (found out its actually Access Points)
- How to store files in the Deep web?
- How to store passwords safely on the Deep web?

But no luck so far. Then I took a minute and decided to review all the material that I had.

If we read the comment that Aiko tweeted, we see that there are 2 words that are capatalized, at first i dont think too much of it but then after failing a lot I gave `DEEP PASTE` a shot on TOR browser. This lead me to the following site:

<img src="https://user-images.githubusercontent.com/66634743/115863547-a94d1800-a446-11eb-8d82-35f6cd3b0ce1.jpg" height=500 width=250>

As we can see, the first link has the title as **DEEP PASTE** (PROGRESS! 😃). After visiting the site and filling out the required details we get the following:

| Creating the Message | Result of the Text Saved |
| - | - |
| <img src="https://user-images.githubusercontent.com/66634743/115863559-ad793580-a446-11eb-91de-e92c29cbc903.png" height=382 width=443> | <img src="https://user-images.githubusercontent.com/66634743/115863558-ace09f00-a446-11eb-8a0a-8feb672538dd.png" height=150 width=400> <br/> This looks a lot like what Aiko had posted too. |

After pasting the link on another tab I get this:

<img src="https://user-images.githubusercontent.com/66634743/115870259-0ac5b480-a450-11eb-886e-b563e212ca99.jpg" height=214 width=529>

This means that all i have to change is the hash at the end of the url to get what Aiko had saved. (More on this in the next task)

### 3) What is the BSSID for the attacker's Home WiFi?

<img src="https://user-images.githubusercontent.com/66634743/115866371-a05e4580-a44a-11eb-8b9d-e5a64f47744b.png" height=334 width=538>
