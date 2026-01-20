---
layout: post
title: "Easter Egg Hunt Game"
date: 2022-03-04 00:00:00 +0530
tags: blog
---

> Got inspired enough to build a game, still ranks as the most creative work I've done I think

---
# Easter egg hunt - Inspired by Ready Player One

**Update**: Due to a third party interest, made the app single player without backend and put it up on github pages. You can see the [live version](https://moonblade.github.io/Easter-egg-hunt-game/#!/app/game) here 

~~**Update**: The app is no longer live. The mlab instance it was connected to for db went down and is no longer accessible. So took down the heroku app. I didn't have a db backup so the existing scoreboard information got wiped. Lesson learned. Take backup of your db and put that with your project. Not just the models for the backend. I figured I'd go ahead and deploy it again without the db, but apparently google has cors error on updating autorized domains. So figured was a good time to take it down.~~

~~A [live version](https://dry-reaches-67526.herokuapp.com/) of the game is uploaded to heroku. Sign in and create an avatar to start playing.~~

---

This project marks some firsts. The first time I added test cases to any of my projects, and used any build pipelines to automate workflows. Its one of the few projects that I completed all the way. 

Years later, looking back on it. I can't help but be blown away by how much creativity is crammed into this project.

## Conception
Back in college, a friend, V, introduced me to the book Ready Player One by Earnest Cline. It deals with Easter eggs, creators of a game or software hiding little features for the end users to find. It tells the story of the protagonist finding a series of increasingly harder easter eggs, solving the puzzles it gives and finally ending victorious.

The true genius of the book was that, there was an easter egg hidden in it (I found this out much later), which led to a series of increasingly challenging games, setup by the author, the winner of which would receive an original Delorean. By the time I got to it, only the [first level](http://anoraksalmanac.com/gate1/stacks/) was still up. I played it till I eventually found the easter egg in that game, directing players to the second gate, which was no longer active. Here's a [hand drawn map](https://imgur.com/a/STRSH#9hsHyBh) I used when playing the game.

The book hooked me immediately, I was inspired by it to try and create something along the same vein. So I started brainstorming.  In the book, the hero had to find three keys, copper, jade and crystal, each of which opened a gate. A challenge awaiting the ones who opened the gate. So I decided the game would have three parts, each of which would be further divided into two, a key and a gate. The key level would helping to solve the gate level.

Before I'd even gotten as far as designing the levels, I got another friend, B, to photoshop some awesome looking gates for the game. Something that I never used in the end. Then again they were made by modifying the gate images Earnie Cline had commissioned of the easter egg hunt he'd made, so meh.

I had a few ideas floating around in my head on how to design the levels, initially I wanted the first level to be a sort of find the object game, where a picture of a room would be presented and user could click any objects on the image and if they were interactible, it would be picked up. But I quickly gave up on it due to lack of technical skills needed to implement it. I also wanted to add an almanac, a sort of guide, here originally functioning as the rule list, and eventually gaining more and more importance.

Fast forward a couple months later I had a semi coherent game fully envisioned in my mind but noone to play it. I thought I'd give it for the college festival as a challenge and front a ton of money to the winner. But I chickened out from that plan. Not having any other incentive to get this game from my mind into code, it stayed in a lull for more than a year.

I randomly ran across the r/readyplayerone subreddit at this point, Since I knew I'd get some players here, I created [a post](https://www.reddit.com/r/readyplayerone/comments/4xpqsg/thank_you/) saying that I was making the game based on the book.

Lacking the technical skills, the levels had to be designed to take input as text without fanciful ui. But I still wanted it to feel like a game with nonetheless.

when the game was completed, I [put it up on reddit](https://www.reddit.com/r/readyplayerone/comments/4zu9hv/easter_egg_hunt_game_based_on_ready_player_one/). The reception was pretty good. But me being impatient ended up giving a lot of clues and hastening the end of the game, instead of letting it run for a longer duration.

The game came around with a second lease on its life when the college fest was fast approaching, and a typical treasure hunt was still not available. So I figured I'd dust off this project and use it a second time. The treasure hunts typically last for two three weeks. Again, due to my impatience, I ended up giving a ton of clues and someone cleared the final level in three days. This was unacceptable to the big wigs, So I ended up writing some extra uninspired levels, which was a bunch of text, which when solved would give a text to input. Since this was easy to implement, I could crank out new levels without having to update the code.

But this felt extremely uninspiring to me, and I couldn't let this stand. So to break it up, while the game was active, and the top player was four or so levels from the new final level, I conceived of a better ending to the game. A text adventure (the improved version of which can be [seen here](https://moonblade.github.io/textAdventure)). In this a player would experience his surrounding as a text description. Could move around by typing commands like 'go north', 'go east' etc. The game created with mostly spaggetti code featured dungeon exploring, monster killing, puzzle solving and item crafting. Cramming all of that into a short game within a couple days took some doing. But I got it up just in time.

This iteration of the game received a lot of praise since the players were expecting a typical treasure hunt type game, getting something different was refreshing.

---

*SPOILER ALERT*: If you plan to play the game, reading further will spoil elements from the game.

---

## The levels

### Level 0

The players are greeted with a simple question. To prove their worth. This level was added at the end of the process so that the no of people in the scoreboard would be thinned out from the outset.

![Level 0](https://i.ibb.co/XypkqbF/image.png)

In the book, the hero finds the first clue by noticing that in the thick almanac volume, a few letters had notches cut out of them, almost unnoticable, he initially dismisses it as a printer issue, before finally understanding that it was indeed a clue.

![Sample notched letter in almanac](https://i.ibb.co/hVQRFQP/image.png)

The [almanac](https://github.com/moonblade/gunt/blob/master/public/Almanac.pdf) provides has a bunch of such letters, which together spelt the word `ignition` which is the answer to the level.

![Completed level 0](https://i.ibb.co/RyP4dJg/image.png)

### Level 1 - The Copper Key

![Copper key](https://i.postimg.cc/h4pq5cBQ/image.png)

In the book, preceding the first key, the hero had to sovle a rhyme to get the location of the first key. I liked this idea and kept playing with it. Tweaking the initial rhyme a lot, finally hitting upon the final version.

`Beneath these words the copper key awaits`

Taking the words literally, an observant player might notice that there is a little bit more space between the first and second lines than the second and third. But its easily missed. On selecting the text however, Its much clearer.

![image.png](https://i.postimg.cc/cH18d05t/image.png)

Another line hidden in tiny white letters. Pasting this into a notepad gives the following.

```
Beneath these words the copper key awaits
22 00 61 48 01 12 40 62
An invincible foe beyond the gates
A Roman general known for his might
An eight bit word to help win the fight
```

`An eight bit word to help win the fight`

So `22 00 61 48 01 12 40 62` would be the key, once decoded, and would possibly be an eight letter word. So how does one go about decoding it? This doesn't seem to be letters, since there are numbers above 26 here.

`A roman general known for his might`

Julius Caeser, arguably the most famous roman general, has a couple of encryption techniques associated with him. The caeser shift cipher and the caeser box cipher.

In the box cipher, the letters are written in a square box left to and then read top to bottom. The key in a box would become

```
2200
6148
0112
4062
```

And when read top down `26 04 21 10 04 16 08 22`, These are definitely letters, namely `ZDUJDPHV`. Okay that doesn't seem to make much sense. But wait, caeser had one more cipher attributed to him. The shift cipher, in which the each letter was shifted by some amount to get a new letter.

Shifting the letters thrice to the left gives the copper key.

`WARGAMES`

A 1983 Sci-Fi movie that was referenced in the book. Entering this, solves the level.

But what about `An invincible foe beyond the gates`?

### Level 2 - The Copper Gate

A terminal window is shown where a game of tic tac toe has been started.

![image.png](https://i.postimg.cc/028x4yj7/image.png)

I didn't want the gate levels to be boring text entry, so coming up with this level was fun. A playable version of tic tac toe, where the user inputs the numbers 1-9 to pick a cell, and the computer picks a different one. The objective is to win the game. Any input other than f, r or 0-9 gives an invalid input message and the game continues.

Remember the warning from the copper key, `An invincible foe beyond the gates`. The game has a perfect AI, ie the game is unwinnable, you can draw or you can lose. There is no way to win against this. The player is stuck.

![image.png](https://i.postimg.cc/JzvfRrr6/image.png)

The key is supposed to help with the gates, not hinder it. In the climax of the movie WarGames, an AI is set to destroy the world by starting a nuclear attack. The protagonist averts this fate, by making the computer play tic tac toe against itself, by setting the number of players to 0. The computer eventually realizes the concept of futility and no win scenarios, and says "The only winning move is not to play".

In this particular instance, the number of players is set at 1, and cannout be changed. But if the player enters `theonlywinningmoveisnottoplay` the game is won and the gate is cleared.

![image.png](https://i.postimg.cc/T2jQwR97/image.png)

An easter egg here, the original computer used by the protagonist in the movie, is an IMSAI 8080 machine, which appears as the device name in this terminal. The username MB stands for moonblade.

### Level 3 - The Jade Key

![image.png](https://i.postimg.cc/RFShLQkn/image.png)

Looking back, I feel this was the weakest link in the game. I couldn't find anything to put as the jade key, that satisfied the constraints of the answer starting with a particular letter and it being helpful for the jade gate. So this is what I ended up with.

Its a straight up treasure hunt style google answer hunting from the text provided.

In the Lord of the Rings series, there is a creature known as the "watcher in the water". The heros encounter this monster when they are making their way to Moria. The west gate of Moria also known as the "Doors of Durin" stand in the way of the heros while they are attacked by the creature from behind. The door has inscription in elven that says "Speak friend and enter", but not giving a clue on what to speak. Realizing it literally meant to speak the word "friend" in elven, They speak "mellon" granting them entry and saving them from the monster.

In the lore of the Lord of the Rings, The Doors of Durin were created by a dwarf named `Narvi`. The watcher in the water could see from its position that the door was closed.

Entering `Narvi` unlocked the level.

### Level 4 - The Jade Gate

![image.png](https://i.postimg.cc/C564gKGm/image.png)

The doors of during stand in your way, and mellon isn't the answer.

Googling for a reference image to the doors of durin, the bottom inscription is noticeably different.

![image.png](https://i.postimg.cc/9XSTCs38/image.png)

In the elven script of "Tengwar", The inscription says 8121. Tengwar is written left to right, but Tengwar numbers, curiously, are written right to left. So the numbers actually say 1218.

Googling for 1218 and the doors of durin leads you to an [xkcd comic](https://m.xkcd.com/1218/).

![doors of durin](https://imgs.xkcd.com/comics/doors_of_durin.png)

The solution to the level was `Mellogoth`

Ever since I read the comic, I knew that this would definitely be a level in the game I was making. But I had no clue how to get people there. Learning about the tengwar script, and some noob level photoshopping later, I had an image that I was proud of that isn't immediately noticeable to have been photoshopped.

### Level 5 - The Crystal Key

![image.png](https://i.postimg.cc/hGgZMfpd/image.png)

![zoomed view](https://i.postimg.cc/VNpRpvFg/image.png)

In the book, when the characters reach the crystal gate, a simple keyhole appears to them, but they are unable to use their keys to open it. Following an earlier clue to its conclusion, they recite, "Three is a magic number" and the keyhole splits into three. Requiring three keys instead of one to open the gate. I was really interested in doing something similar. 

Being uninspired to create another puzzle that gave the answer three, I blatantly stole from Dan Brown, the code he uses in Digital Fortress. The letters that go around the screen from top left in a clock wise manner spell out.

`PFEE SESN RETM MFHA IRWE OOIG MEEN NRMA ENET SHAS DCNS IIAA IEER BRNK FBLE LODI`

The code on running through a ceaser box cipher returns

`PRIME DIFFERENCE BETWEEN ELEMENTS RESPONSIBLE FOR HIROSHIMA AND NAGASAKI`

The answer to which is `three`.

Entering three as the key, wait for it....., the keyhole splits into three parts.

![three keyholes](https://i.postimg.cc/J0mbCkHN/image.png)

This rhyme is one I'm particularly proud of, being able to cram three different answers in four lines to someone who pretty much sucks at coming up with rhymes was a huge deal. Combining it with the textbox splitting into three to emulate the book, couldn't be happier. This definitely deservs to be the last key.

`Game, book and movie blends`

The first line gives a clue for each for each of the keys, the first related to a game, the second to a book and the third to a movie.

`A glitchy egg for our plumber twins`

Mario and luigi, are in fact twins. Googling plumber brothers immediately gives you Mario, but plumber twins, its not as obvious. 

Super Mario Bros was one of my favourite games on the NES when I was a kid. Recently realising there was a glitch level in it, I played through it and eventually reached it. The level is called `minusworld` which was the first key.

At this point, I realised that finding out three keys without knowing whether any of them were correct would be a nightmare for the player, so I needed to implement something that would make playing a bit more fun so that if they had part of the answer, they would still know about it.

What I ended up going with was a tick mark next to whichever key was correct. I wasn't too subtle a UI designer at this point in time.

![partly correct answer](https://i.postimg.cc/gkbYdKJF/image.png)

`The twist by richard ends`

This was straight out of left field. With no connection to any of the other levels, keys or the premise. 

A play on words, if the player realizes that richard the name can be substituted by its shorter form, dick. the line reads `The twist by dick ends`. Dick ends, Dickens. The second key being `Oliver Twist` the novel by Charles Dickens.

`The tribute to where it all begins`

Since the game was inspired by the book Ready Player One, I wanted that as at least one of the answers. Since, a movie based on the book was coming out as well. So It seemed like the perfect answer. `Ready player One` was the third key.

### Level 6 - The Crystal Gate

![Crystal gate](https://i.postimg.cc/Gt25Gtb1/image.png)

In the final book of the Harry Potter series, Harry receives a golden snitch from the will of Albus Dumbledore, and on it was written "I open at the close". The password is `snitch`. Seems a bit underwhelming doesn't it.

Typing snitch into the text field does nothing though.

In an unrelated internet browsing session on steganography, I came across two interesting pieces of information. A pdf file has a end marker to tell the pdf software where the file ends. Whereas a zip file has a start marker to tell where the zip file starts. Hmmm, So what would happen if you appended a zip file at the end of a pdf file, would it work as both a pdf and zip? I tried it out and was overjoyed when the command `unzip sample.pdf` spat out the content of the zip file. I figured I'd put the answer to the final level in the almanac and on unzipping they'd get the answer.

Adventure, The Atari 2600 game, is regarded as the first video game to have an easter egg in it. In difficulty levels 2 and 3, the player could find a miniscule grey dot, that would allow him to pass through a barrier in the game to see the easter egg room, with the creators name in it.

![atari easter egg](https://i.postimg.cc/xCHK7Sgb/image.png)

In the climax of the book, the hero has to find the easter egg in the game to finish the last hurdle. I had played Adventure before but had found it too hard to crack and had left it. Coming back to it after reading the book though, I eventually got good enough to get to the easter egg room every time. 

Some time later I came across the [assembly code for adventure game](https://github.com/johnidm/asm-atari-2600/blob/master/adventure.asm). Okay, this got me excited, I built the game, and started playing. I wanted to mess around with the code of it and see if I could get it to do something different. I managed to create test version of the game where the player could walk through the barrier without needing to beat the game. With some trial and error, I setup a small python script to edit the code in the easter egg room to whatever picture I painted. Thus editing the easter egg room to say something different. At this point I was beyond ecstatic. Removing the test version and replacing the original, and adding the new easter egg room and building it, I zipped up the binary and put the password `snitch` on the zip file. This zip file was appended at the end of the almanac.

To beat the final level, the player would need to download the almanac, unzip the pdf, put in the password `snitch`. Get an atari 8600 emulator. Play Atari adventure in difficulty level 2 or 3, and reach the easter egg room. If they did all that successfully, They'd be greeted with the following screen.

![my easter egg room](https://i.postimg.cc/sDkd5Yqf/image.png)

Entering `Gregarious Games`, which was the company that made the game in the book, would solve the level.

### Level 7 - Credits, Bonus key

![Credits](https://i.postimg.cc/q7MT7kW2/image.png) 

On clearing the Crystal Gate, the credits screen is shown. Ostensibly the end of the game.

In hindsight, the actual credits should've been kept outside of the game, since few would have actually reached this stage.

Couldn't help but add another level as an easter egg. So on clicking the second o of moonblade would lead to

![credits level](https://i.postimg.cc/wB3GP3S4/image.png)

![bonus key](https://i.postimg.cc/6ppj2y56/image.png)

The keys collected (ignoring the gate levels) till now where

```
Ignition
WarGames
Narvi
Three
Minusworld
Oliver Twist
Ready Player One
```

`Cutting off the heads claimed`

Taking the first letter of the keys, you'd get the string `IWNTMOR`.
Taking a few liberties and expanding it as `I want more`. Gives the answer.

![I want more](https://i.postimg.cc/Kz04Yq98/image.png)

Originally the game ended here, but on its second run, since the game completed too quickly, I had to add a few more levels. So I hid a disgruntled message in the game assuming none of the higher ups are ever going to see this message.

### Uninspired levels 8-14

I had to add more levels to the game on short notice, while the game was online, so like every other treasure hunt game, I added levels that can be controlled without editing the code. Adding a new level could be done just from backend. So that new levels could be added easily.

Since the game had started, I didn't have the luxury of time to create carefully crafted new levels. So I had to make do with this instead. In the interest of completion, I'm adding it here.

<details>

<summary>
    Click here to see these levels
</summary>

#### Level 8

![8](https://i.postimg.cc/BvMJ582h/image.png)

Removing the symbols which were a red herring gives you `3127A1B73` which on converting to binary gives `001100010010011110100001101101110011`. Which is the paradox correcting time code from the series futurama. It is a level 87 code.

The answer being `Eighty Seven`.

#### Level 9

![9](https://i.postimg.cc/tRr209NL/image.png)

On decrypting the bottom part with a playfair cipher with the key "DEATH". 

![answer 9](https://i.postimg.cc/GhVK2zNK/image.png)

You get `Visor and glove control`. In the book, the game console where the book takes place has visor and glove controls and is called the `Oasis` which is the answer.

#### Level 10

![10](https://i.postimg.cc/NFWXgCMr/image.png)

Taking the first letters of the words, you get `sn foil 1 corn`. With some imaginative extrapolation, it can be made `tin foil unicorn`. Which is a series from the movie blade runner. The tin foil unicorn was part of the jade key in the book.

The answer was `Oscar Pistorius`, A double amputee sprinter, who was also known as blade runner, due to his prosthetic limbs.

#### Level 11

![11](https://i.postimg.cc/SQ8Cdqt6/image.png)

An error message pops up saying that there was an issue and to contact tech support.

At this point I'm reusing ideas. Some fancy googling of tech support and the numbers gives links to my favourite xkcd comic. [#806](https://xkcd.com/806/).

![xdcd 806](https://imgs.xkcd.com/comics/tech_support.png)

The answer of course was `Shibboleet`. The fictional code word to get better tech support.

Status 418, is an april fools joke from 1994, under the hypertext coffee pot control protocol, which returns the error code "I'm a teapot".

#### Level 12

![12](https://i.postimg.cc/c4gjXKGD/image.png)

Feeling that the original level provided here was so bad, on some recent update, instead of making a good riddle, I just plagiarized again from Dan Brown, from his book Da Vici Code, The answer to it is `apple` available on a simple googling.

#### Level 13

![13](https://i.postimg.cc/5yNmTRr5/image.png)

The third _stone_ from the sun, is an instrumental composition from Jimi Hendrix, If the song is played at more than double the original speed, an easter egg is revelaed as a conversation between two aliens who talk about Earth.

During the course of the conversation, they conclude that chickens are the smartest creatures on earth. The answer to the level is `Chicken`

#### Level 14

![14](https://i.postimg.cc/pTVc8CHS/image.png)

Harmless earth, is a reference to Hitchhikers guide to the galaxy, In which earth is referred to as mostly harmless. A character in the Hitchhiker's guide to the galaxy, is repeatedly killed by the main character, Arthur Dent, on every reincarnations and is hell bent on revenge, but fails every time. The character is named `Agrajag`.

</details>

### Level 15 - The final level

![15](https://i.postimg.cc/V6jMfQpQ/image.png)

At this point, I didn't like how the game was turning out, So while it was active, I wanted the end to be a good one. So I put up some levels to give me some time, and started work on this. I ended up completing the thing in two days and putting it up as the final level.


I was interested in creating a text adventure, one where the player would interact with the world through text commands and the descriptions of where he was and what transpired would be provided via text as well.

![text adventure](https://i.postimg.cc/zGTVRZ8x/image.png)


I started by drawing a simple map of the dungeon I would build, complicating it further and further, till it resembled a long enough game. I ended up with 10 rooms, in two levels. A grid of 9 rooms, and the final boss room as the cellar underneath the bottom right room. Then the game mechanics, which involved finding keys, opening doors and chests, crafting items and killing enemies. If you didn't have the right weapon to kill the enemy with, they would attack and kill you. In hindsight, there's way too many keys and chests, which is not really condusive to an enjoyable game. 

What I ended up creating was a game engine, that took the world I created in json structures and built the world around the player with that. The interactions would also follow whatever was present in the json structure of the world. But since I was pressed for time, every time I needed to create a special condition, say, making an item required the player to be in a specific room, it was hardcoded in in the logic. So eventually the code became an even mix of hardcoded spagetti and game engine logic. On killing the final boss, a vampire with items crafted during the game and retriveing the trophy and putting it in its correct place. The game was won and the final level was passed. 

The game provided enough difficulty for the player to keep occupied for a while, and frustrating dead ends that needs the game to be restarted for a lot of hair pulling.

<details>
<summary>
Full walkthrough for the final level
</summary>

- In west room, you have platinum key, take the key. 
- Move east to the center roomm and take the copper key lying there.
- Move east again to arrive in east room. Open the copper chest to get the silver key. Ignore the scorpion trying to strike you.
- Move west back to central room, move north to the north room, and open the silver chest to get the gold key. The silver key will fall out of the keyhole when the chest is opened. Retrieve it as well. There should be an empty bottle lying around. Pick that up as well.
- Move south and then west to get to west room. Use the bottle to pick up some water in the bottle.
- Go east and then south to get to the south room. Open the gold box to get a wooden key. There should also be an ivory key here, pick that up as well.
- Go north twice to reach the north room, Open the east door with the wooden key, to enter the treasure room.
- Open the platinum door to get the sword. Ignore the decaying wooden box.
- Go west, south and east to arrive back in east room with the scorpion in it. Kill the scorpion with the sword.
- The scorpion on defeat should drop the granite key.
- Go west, then south, to the south room and open the granit door to the west.
- Move west to arrive in the burning room with the big fire in it. Do not put out the fire. Take the wooden club lying there.
- Go east, north twice and east again to the treasure room. Break open the decaying wooden box using the club. It should shatter into decaying wood pieces and give you a stick as well.
- Take the wood pieces, and use the sword to sharpen it and make a wooden stake with it. (make stake).
- There should be more wood pieces lying around. Take another piece.
- Move west, south twice, and west to get back to the burning room. Save a bit of the fire and make a torch by dipping the stick in fire. (take fire). Throw the silver key into the fire, so that it melts into liquid silver. Coat your sword in the liquid silver so that it becomes a silver sword. (Make silver sword).
- Pour the water from your bottle onto the fire. The fire should go out and you should see a red hot glowing box there.
- Go east, north and west to arrive in west room. Get some more water in the bottle.
- Go east, south and west, back to the burning room, and pour water onto the glowing box. It should turn into an ivory box. Open the ivory box to retrieve the stone key.
- Go east, north, east again to east room. Open the south exit covered by the stone door.
- Go south to the cavern. Kill the spider there by setting fire to its hairs. It should drop an iron key.
- Go north, west, north, to north room. Open the west door with the iron key.
- Go west to the cell. Kill the cobra with the sword. The snake should look like it had a recent meal. Open up the snake to reveal the emeral key. Leaving behind its snake skin. Take the snake skin and make rope with it. Pick up the garlic smelling moss in the room as well. Make a ladder with the rope and the wood pieces gathered earlier.
- Go east, south and west to the west room, Take some more water.
- Go east twice to arrive in east room, with its aura of holiness. Imbue the holiness into the water and make holy water.
- Go south to the cavern. Open the trapdoor down with the emerald key. Attach the ladder to a piece of rock so that after beating the boss, you have a way to come back up. (put ladder).
- Go down the the final room. It should be pitch black in here. Put the fire down to get some light. There should be a terrifying vampire there. Throw the holy water in his face. Throw the garlicky moss towards his direction. Stick the silver sword through his abdomen, and finally drive the wooden stake through his heart to kill him. (kill vampire four times). He should drop a trophy.
- Go back up, north, and west to arrive back in center room.
- Place the trophy on the stand in the central room to beat the game.

</details>

## Almanac

In the book, the easter egg hunters are given a sort of manual by the designer of the game called the almanac, and the clue to the first key is hidden inside the Almanac. So to create a similar aesthetic, I added an Almanac for the game as well. 

Ostensibly a rule book, I crammed the almanac chock-full of easter eggs and the answer to the 0<sup>th</sup> level.

### Secrets of the almanac

[Here is a link to the almanac](https://github.com/moonblade/gunt/blob/master/public/Almanac.pdf)

![Almanac image](https://i.postimg.cc/MKggFHgp/image.png)

On first look, it passes as an inoccuous document detailing the rules of the game. 

#### Level 0 answer

In the book, the first key is found by combining the letters with notches in the almanac. To be true to the book, I edited an existing font, cut out notches in the letters, added that as the font for the letters I required. Spelling out the word ignition.

![i](https://i.postimg.cc/rFWLc51r/image.png) ![g](https://i.postimg.cc/NfNRsrQQ/image.png) ![n](https://i.postimg.cc/zfDmnM9C/image.png) ![i](https://i.postimg.cc/G3WZM9Wh/image.png) ![t](https://i.postimg.cc/027hhPvG/image.png) ![i](https://i.postimg.cc/jdRhdbN4/image.png) ![o](https://i.postimg.cc/QtLQLGh5/image.png) ![n](https://i.postimg.cc/PJyY8CZz/image.png)

#### Morse code

After the end of the text, there are tiny white text, visible when selecting the content.

![whitetext](https://i.postimg.cc/ZKqyMKp2/image.png)

On copying it to a notepad, you get 

`.. .-.. --- ...- . -.. .- -. -... .-. --- .-- -. --..-- ... - . .--. .... . -. ..-. .- .-.. -.- . -. --..-- .- -. -.. - --- .-.. -.- .. . -. .-.-.-`

Which on translating from morse gives `I LOVE DAN BROWN, STEPHEN FALKEN,AND TOLKIEN.` Giving clues to the elements used in each of levels of the game. Dan brown for emerald key, stephen falken being a character in war games, and tolkien being the autor of lord of the rings.

#### Secret cheatsheet one

The first letters of all the pointers spell out the word `cheater part one`. Coupling it with point 11 about tinyurl. Players can goto tinyurl.com/cheaterpartone. Which redirects them to an evernote page, giving more clues for the copper key and get.

![copper clues](https://i.postimg.cc/J0Smxqb1/image.png)

If the players went ahead with the logical leap and tried to visit tinyurl.com/cheaterparttwo. They'd be hit with this screen.

![cheaterparttwo](https://i.postimg.cc/7LP6fK9c/image.png)

#### Secret cheatsheet two

If the metadata of the almanac is opened, they are hit with the clue to the second cheatsheet.

![cheatawesome](https://i.postimg.cc/TYGXdpCN/image.png)

Going to tinyurl.com/cheatextends gives them clues for the jade key and get.

![cheatawesome](https://i.postimg.cc/FH8WK6hF/image.png)

#### Secret cheatsheet three

Remember how I said a pdf has an end character and a zip file a start character? So what happens to the space in between. It must be free real estate right?

If player was crazy enough to open the almanac in a text editor, they'd see the third clue.

![third cheatsheet](https://i.postimg.cc/Kc05zWNX/image.png)

On going to tinyurl.com/cheatawesome. The player is given clues for the crystal key and gate.

![third cheat sheet](https://i.postimg.cc/j5pnwzL7/image.png)

#### Crystal Gate

The original final level of the game, an atari adventure game with an altered easter egg room was placed as a zip file appended to the end of the pdf. On unzipping the pdf with the password from that level, you would be able to play atari adventure, The winning of which would give you the final answer. This has to be the proudest I've been of any of the achivements pulled off for this project.


## Conclusion

I'm definitely pleased with this project, and hopefully writing this up inspires current me to create more stuff for future me to be proud of.
