---
layout: post
title: "Lessons in overengineering"
date: 2021-09-12 00:00:00 +0530
tags: story
---

> I tried to create a project because I was bored. It ended up ballooning past expectations.

---

Preamble: This is a tale of a persons slow descend into insanity with sunk cost fallacy exploited for trivial gains in return. 

It all started with a simple idea, having to wait till water is completely gone to turn on the motor like cavemen seems stupid. There has to be a better solution. It was also true that at this point was bitten by the rare "I want to do some electronics shit now" bug.

Anyway, so I went ahead and searched online, had previously looked up a nodemcu, a glorified ic chip with inbuilt wifi so making iot shit with it would be a breeze compared to the labour intensive arduino stuff. I thought about using plain wires for sensing the water level with four levels, but that didn't sound sexy enough. So I figured I'd use an ultrasonic sensor on the lid of the water tank and find the distance to the water level and thus find the water level percentage. Which appealed to me. So bought a nodemcu and an ultrasonic sensor from amazon and waited for it to arrive. They arrived a week later, but since the electronics bug is rare enough and the last time I had it was years and years ago, I have literally no electronics stuff to do anything with these components, no soldering iron, no solder, breadboard, dot board, or any of the other minor stuff that you end up needing when you embark on such a project. So I went to the electronics store in town and got the starter kit of shit I'd need. I added a rudimentary code to detect the distance to the water level in cm and upload it to a firebase real time database in the nodemcu. Once done, the actual "electronics" part of the project literally involved soldering 4 wires together. But since I was off the  electronics wagon for a while, it proved challenging enough. With my abysmal soldering done, I needed a way to attach this to the underside of the water tank. Since I had no intention of taking electrical wire into a tank filled with water, I needed to provide power to the nodemcu some other way. So went off and bought some electrical wire, a plug and a phone charger. Added new wiring in the terrace to take power from a fan line, rerouting it to be always powered on, and added a plug at the end of it, dangling down above the water tank. At the end of the plug, connected a phone charger and then connected the end of it, a much safer 5V DC current to the nodemcu, and hung the entire thing in a box under the lid by poking holes in the lid and tying it to the bottom.

![Final product tied to the underside of the lid with the charger cable snaking through the side of the lid](https://user-images.githubusercontent.com/9362269/120058157-968dba80-c066-11eb-8d4d-26f66873411d.png)

Final product tied to the underside of the lid with the charger cable snaking through the side of the lid

---

At this point, what should have cost at max 300 bucks is now just shy of 2K. Now that I had the readings from the tank, I needed some way to show it to the user. And since I had enough electrical shenanigans for a bit, figured I'd create an android app for it. So with the next couple of days, created an app, that takes this distance value from the rtdb and calculates a percentage value from it. Added a clever bit of code in there so that it would automatically change the maximum and minimum values so that I didn't have to find the distances when it was full or empty, it would just find it out and update it automatically. So with the app installed I can now check what the level of water is and whether or not I need to turn on the motor.

---

But this still presented the problem that it only gave the information when the app was opened, the info wasn't there on your face ready to go when you need it. So I tried creating a widget that would show the percentage. But I was new to widget creation and there was a ton of bugs in it and it just WOULD NOT update properly, even if the app had the data, the widget just would not update. It drove me crazy and I just let it go at this point. So now I have an app and a physical device that reads the water level.

![Screenshot of the app](https://user-images.githubusercontent.com/9362269/110064173-9b5a0f80-7d92-11eb-9c23-230dae3abe87.jpg)

Screenshot of the app

---

I went to blore to stay, and since I thought I'd stay there for an extended period of time, I took my electronics kit with me as well. And I figured since there wasn't an in your face display of the water level I should create that as well. So I ordered another nodemcu to blore and bought an 8x8 led matrix as a display unit intending to create an always on display to show the percentage. Once that arrived, I bummed a small breadboard from my roommate. (which is used to prototype electronics stuff without soldering) and created a display unit which would calculate and display the percentage on the led matrix. It had two modes of display with level view and percentage view. Levels view was eventually never used and percentage view was set all the time. So I made a finished product of this by taping the breadboard to the top of a charger (from my speakers) and connecting it to the nodemcu on the breadboard with the display on top. Since this needed a place to plug into, bought a multi plug so that it could be plugged into the kitchen plug. And when I came back (I thought I would be back for only a week, spoilers, I wasn't)This additional feature has cost me another 800 bucks. With the total hovering at 2.5 K.

![Testing the display](https://user-images.githubusercontent.com/9362269/110785068-83055b80-8290-11eb-8b11-7795970e5736.jpg)

Testing the display

![Installed in kitchen](https://user-images.githubusercontent.com/9362269/120057833-f9318700-c063-11eb-82da-114e88e869ca.png)

Installed in kitchen

---

I was trying to get more automation stuff done in my home, and had ordered smart switches and smart controllers for automating my room. Got into a spending spree and ended up buying a raspberry pi as well along with it thinking I'd find some uses for an always on server. The top of the line pi and its accessories cost 13.5 k. Sigh, impulse buying sometimes doesn't work out that much. So I setup the rpi with raspberry os at first but ran into trouble with it, so had to redo everything I did with ubuntu and then later a downgraded version of ubuntu since the other one had issues as well. All told that sucked up a week or more of my time in pointless configurations. Once configured all I had running on it was a pihole and using an 8k machine to run pihole is like using a machine gun as a walking stick. So filled with regret, I looked around for other ways I could use this, trying out google drive alternatives, google assistant clones, torrent seeders and others before thinking that I should also use this to control my motor, so that I didn't need to turn it on and off manually. There were other debugging issues that occured that made me buy an hdmi cable for the pi as well, debugging shit based on guesswork is way harder.

---

The led matrix seemed to have issues at this point, so bought a replacement, but lo and behold the moment the new one arrived, the old one starts working fine. It was afraid it would be replaced. I'm onto you led matrix. I'm onto you.

---

I didn't attempt motor control before this because its not a simple 32 A switch, oh no, its the push on push off switch that people use for outboard motors so that in case current comes on, motor doesn't start automatically. So was terrified of messing with it originally. But eventually overcame it and figured whats the worst that could happen. But now my electronics stuff is in blore and I'm stuck in calicut. So if I decide to do this, the upfront cost would rise again. But I already sunk 8k on a pi, whats another 1k, so said fuck it and went about buying the shit I needed. 

While the stuff was arriving, I wrote the code for the raspberry pi, which would check the water level and every time the level changes, would instruct the motor to turn on or off, and the node mcu code so that motor would turn on or off based on this command.

This time around, I bought a tinier version of the nodemcu called a wemos d1 mini. I can't buy the starting kit from the nearby store because its lockdown now so had to buy everything from amazon at double or triple cost. I wanted to get rid of the charger cable shenanigans, so I bought a miniature ac to dc convertor as well so that my thing would work pretty much directly off of ac now. Then I accidentally bought a 12V 4 channel relay, and returned it and bought a 5v 4 channel relay instead, some connectors to connect it to ac and the starter stuff from last time at higher cost. I had also inquired about printing my own pcb and 3d printing its housing, but it was far too costly (which in retrospect seems laughable) and didn't entertain it. Had ended up building my pcb design in two different software and tried test versions on normal paper as well. Anywho, built the dot board and connected the 4 channel relay with 10 ampere rating, connected up all the circuitry required (unknowingly connecting one wire so that motor could never be turned off, eventually realizing it and correcting) and tested it, and gloriously it worked...

![assembly](https://user-images.githubusercontent.com/9362269/132271024-899ab56e-ccfe-4df7-83b6-5eef81ba003f.png)

assembly

![assembled into an old box I found lying around](https://user-images.githubusercontent.com/9362269/132271150-082d88fd-c467-496e-9a31-b242ba655d22.png)

assembled into an old box I found lying around

![wiring it into the motor switch](https://user-images.githubusercontent.com/9362269/132271170-b57178d9-2abc-46dd-aec0-80a86678559c.png)

wiring it into the motor switch

![finished product](https://user-images.githubusercontent.com/9362269/132271193-f7c9b6ee-e5ed-45c3-b3cf-0c57d9a6828d.png)

finished product

....for one day. The relay rated for 10A, drew 15A of current through it and promptly died. So ended up with a crappy looking paperweight on the motor switch doing nothing.

---

With that not working, decided to concentrate on raspberry code for a while, wrote other code to monitor the water level and show it as a time series graph, all in the efforts of justifying buying the raspberry. Trying to get it on the internet, failing on it due to not getting static ip from the isp. Trying other shit on the rpi like pi tunnel and ngrok and not liking any of those. 

![https://user-images.githubusercontent.com/9362269/132270512-7c44fb35-45ae-483a-b195-0e09f2d6994c.png](https://user-images.githubusercontent.com/9362269/132270512-7c44fb35-45ae-483a-b195-0e09f2d6994c.png)

---

There was something wrong with the display unit, I had went on vacation for a week, and display wasn't moving from 11 percent. Apparently the rpi had restarted but the processes didn't restart. So wrote new code in the display unit such that if the rpi failed, display unit would just start calculating percentages on its own and display that. Why does it ever need rpi you ask? Well rpi does a more elaborate calculation and removes any outlier values. The sensor isn't perfect, sometimes it gives wrong readings where the percentage is much higher than it should be, the rpi fixes all these values with clever coding, by storing the last 10 values and removing any values that are more than 2 standard deviations away from this series. So that most of the scattering gets fixed. But if rpi is down, the display can still show the current data, albeit a bit more flaky data.

---

Eventually figured I needed to do something about the controller, so went ahead and got much higher rated 30A relays, earlier I had used 3 relays from the 4 channel one, somehow I got the notion that I could do the same thing with 2 relays, of course I couldn't. No clue why I thought I would be able to build 2 independant switches from one. I tried and got a motor that never turned off. So passed on it and ordered another relay. Also this time around, I made it smarter so that the motor state was measured externally and not internally so that it would know even if a human turned it on and would be able to turn it off, unlike the previous iteration where it would only turn it off if it was turned on by itself. This required some rejiggering of the rpi code, so did that first, then wrote the code for the new wemos d1 chip which would take this into consideration as well. 

When the third relay arrived, connected everything up.... and it wasn't working. I tried to reflash the chip with new code, but the chip wasn't working now either. Strange. So I bought new cables thinking maybe the cable had some fault? nope, chip still not working. This would normally mean a wiring issue, but I was pretty sure the internal wiring of the board was fine, I retraced it and confirmed that all the internal wirings were correct. Odd. But it seemed to be turning off the motor correctly. The heck. Anyway, since the chip was shot, I ordered a couple of new chips, figuring its good to have a spare.

![new circuit](https://user-images.githubusercontent.com/9362269/132272520-fc4b3dfb-e939-48e7-a574-6e1d59bea94a.png)

new circuit

![finished product in a shinier box](https://user-images.githubusercontent.com/9362269/132272558-3e547a7d-a286-49df-a876-f6f8b5c5a6c2.png)

finished product in a shinier box

---

While I was debugging what could have went wrong with the chip, trying to resuscitate the chip, the water level sensor decided to go for a swim. The thread broke and the whole box took a dip in water. Sigh. Water was also condensing onto it and the swim was just the straw that broke the camels back. It would have failed eventually anyway.

![water damage after 8 months](https://user-images.githubusercontent.com/9362269/132033304-b6c784d4-07c3-428f-9286-d6dd2637c560.png)

water damage after 8 months

Since I couldn't fix motor controller before the sensor was fixed, ordered yet another nodemcu and a waterproof ultrasonic sensor. Also went to the local store and bought the required items for it as well. I tried my hand at hand crafting pcb, but for the life of me could not drill holes in straight lines with the hand drill. So for the second time, let go of the prospect of custom pcbs, and used dot board. The waterproof sensor was a piece of shit, giving invalid readings and readings that were way way off. Thankfully with everything breaking around me, I had thought of this and bought a normal ultrasonic sensor as well. So used that and created a new board. This time around made it so that parts would be swappable. Also added an ac to dc convertor on it, figuring that I'd keep this on top of the lid instead of on the bottom.

![old vs new](https://user-images.githubusercontent.com/9362269/132161640-8e9af23f-c296-4ebe-bd39-4643f38173a5.png)

old vs new

Took off the lid from the tank, and spent some time trying to drill holes in it, realizing that the effort was futile, brought it down and tried making circular holes with safety pin held with pliers over the stove. Got tired of bending over for so long and bought candles so that I could sit and do it in peace. After an hour of work, had a couple of holes through which the detector of the ultrasonic sensor could be pushed through. So now I had the new version of the lid, which just the detector on the underside and everything else on top. hopefully this lasts longer.

![underside of lid](https://user-images.githubusercontent.com/9362269/132161556-d9242ffb-65bf-441a-befc-98c5a41b7320.png)

underside of lid

![topside connected up and insulated for waterproofing](https://user-images.githubusercontent.com/9362269/132161731-35425384-af4b-4f77-8e5a-77ded42fbf48.png)

topside connected up and insulated for waterproofing

Connected up the v2 version of the sensor, the ac current on top of the lid is a bit fear inducing but nowhere near as bad as it could be if it was on bottom. Anyway, this worked perfectly. And the sensor problem was fixed for now.

---

Now for the motor controller. After the new chips arrived, flashed them with new code, and then decided to do another round of testing before inserting it, and found out that the ac to dc convertors were connected up wrong. The internal wiring was right, but the wires connected to the outside terminals were switched. GAH. swapped it around, inserted the new chip and the motor controller started working, when I gave it a command manually, but when the water level went down it didn't turn on automatically. strange. And it was also overflowing, not turning it off when full either. The heck. 

After a day of debugging, realized that I had a setting that turned off automatic control and that setting was enabled. 🤦‍♂️. Anyway, disabled that and it started working correctly. Finally.

---

I had originally attached the raspberry pi behind the television with double sided tape, but the tape wasn't strong enough and the rapsberry pi was now just dangling from its network cable underneath the tv. This was offputting to me, so I poked a couple of holes in its case with a hot iron, drilled a couple of holes behind the tv and then attached the case to the wall with screws so that it would sit tight. And assembled back the raspberry pi. aaaaand it wouldn't boot.

While disassembling, the sd card, which was overheated got struck and got a hairline crack, now the 256 gb storage says it only ever had 32 mb. Tried everything to fix it eventually realizing that its a hardware error that can't be fixed.

![a tiny crack to ruin an sd card](https://i.imgur.com/KfYctj0.png)

a tiny crack to ruin an sd card

Ordered another 64gb drive and waiting for it to arrive. There were a ton of fiddly bits within the rpi that I had setup. Now would need to do ALL of those over again. Sigh.

All told, this project has cost me close to 25k and 8 months, and will cost me more as I add an ssd on the rpi so that this sd card fiasco can't happen again.

I know I should write code in the motor controller to cut out the rpi, in case of failures, I already did it for the indicator, but I'm lazy at this point to do that. Maybe in the future.

---

While I was waiting for the sd card to arrive, I ran the motor controller code on my laptop to auto control the motor, did not like this code running in my lap. I also noticed that the indicator led was not functioning correctly. I took a closer look and realized that the code for it, had some run time issues and was not switching over to direct mode (ie calculate percentage itself so that even if rpi is down it would work). So spent some time fixing it. After that was fixed figured I should probably go ahead and do the same for motor controller as well and did the bloody obvious thing of fixing that up as well. There was no need for the rpi to be involved in this loop whatsoever. Yes it makes it a bit smarter and it makes it easier for me to write code, but its not necessary. Its just overengineering and another point of failure. But now it gets switched over and cut off from the loop if it ever goes down. So theres that.

Haven't tested the newest code. Hopefully it runs well and doesn't cause any major issues. 

---

It just had its first run, and it worked, surprising that something I wrote compiled on the first try and worked as intended. Nice

---

Well, would you look at that, it started misbehaving and turning on the motor at random times and not turning it off. I think the motor controller code is fine, but the water level sensor is broken again. Gah. 

---

The sd card came, I installed ubuntu on it and inserted it in the rpi, aaaaand nothing. It just didn't start. I'll debug it later. For now found something else shiny to work on.

---

The reason I had till now made by iot devices as dumb as possible and then provided smartness externally via rpi or other servers is because it was a hassle to update the nodemcu devices. To update the device I'd need to stop its functioning, plug it into my pc and then manually push an update it. where as I could update the rpi code easily by sshing into it.

This is 2021, There has got to be a better solution than that, and one that would allow me to cut the rpi entirely out of the loop.

So, with the spirit of over engineering in mind, ended up creating a new repo and a new site in firebase, which lets me upload the compiled binaries. I present to you - [IOT Auto Updater](https://water-level-indicator-a555e.web.app/upload), ([repo](https://github.com/moonblade/auto-update-iot-devices#readme)). After a lot of frustrating road blocks and dead ends, eventually got this to work. Now I can compile a binary in my laptop and upload it here and the iot device will automatically check for updates and pull the newest update from firebase if the upload was done. With this I can pretty much go crazy on the logic in the devices since now I have a (ostensibly) foolproof update mechanism in place for when things go pear shaped. Now I JUST need to update all the devices MANUALLY once to be auto update compatible. At least this will be a prevelant feature in any future iot projects I do.

![](https://i.imgur.com/7UoZkA2.png)

---

Now that I have an auto updater setup, updated code for the sensor to get multiple readings, find the mode of those readings approximated to the nearest 5cm and pick that. But sensor is already broken from water damage from the high humidity and just gives random values. So turned off the motor controller, put up a frowny face on the indicator and ordered new sensors, a waterproof one and more standard ones. Will see if I'm able to use the waterproof one since it was broken last time, and doesn't have the range requirements I need.

![](https://i.imgur.com/d1s3v2l.png)

---

I'm way too trigger happy with buying shit, I guess in the grand scheme of things, happiness from the journey matters and if that gives a return on investment in regards to the cost, its fine. With that in mind. LASERS!!!. So I was thinking, for a long term solution, I'd have to downgrade to standard wires to read percentages like cavemen. But no, there is another alternative. lasers. Specifically a laser tof sensor. Something thats small, is already sealed. And can be covered with tape if needed, since light passes through tape, unlike ultrasound.......Huh, I haven't actually tested that last part, I should do that first.

Anyway, I'll probably order a laser tof sensor. And I'll experiment on that to see if thats any good. the options are tof10120 or vl53l0x

![](https://i.imgur.com/7WBvUWv.png)

![](https://i.imgur.com/z2tPa1d.png)

---

20th sep. Got the ultrasonic sensors and the lidar sensor. I'm gonna try and mount the lidar sensor on some sort of mount higher than the hole so that water can't easily get to it, also make some kind of insulating protection on it, Assuming I can put cello tape on it without interfering with its function. Will have to check. The thing is tiny, like "sneeze and its gone" tiny. We're pretty ffing good at making semi conductors small, aren't we.

![here it is at the end of my finger.](https://i.imgur.com/Jj0DmEl.png)

here it is at the end of my finger.

---

25th sep - Made a prototype distance sensor on the breadboard with the lidar sensor. After a couple of wrong turns got the code to work. Went away, came back a couple of hours later and the device no longer functions. No wonder software people hate working on hardware, there is zero repeatability. This project seems custom made to turn me insane. After some intense debugging. Realised that the issue is with the hardware of the chip, It just doesn't work consistently, So assume the thing is broken and order another. Really should have paid attention to the chip on the chip. Ordered a couple of replacement lidars.

---

Since there was work taking place on the water tanks, and the bathrooms, was delayed on the project for a couple of weeks.

---

Before the lidars arrived, I figured I'd give the waterproof sensor another try, and lo and behold this one started working fine (although I figured out an issue with my connections in which software HIGH and LOW wasn't really giving out a potential difference of 5v, and this might have been why the last one wasn't working either), So went ahead, did some reliability testing on it on a breadboard and then replaced the existing module with this one. Aaand it wasn't working. Finding out that with the ingenious replaceable connections I'd made, the dependance on good female to female connectors were present and the ones I had were crap. So ripped it out and soldered on the connections so that this issue wouldn't happen again. 

I'd originally planned to use the overflow pipe for measuring. By inserting the sensor into it, but it turned out to be an echo chamber and always gave the minimum reading. So ended up removing it from there, sticking a new pipe on the tank and putting it inside that instead.

![sensor dropped inside overflow pipe](https://i.imgur.com/jN01Y4P.png)

sensor dropped inside overflow pipe

![Moved it to the new pipe instead](https://i.imgur.com/jaZw063.png)

Moved it to the new pipe instead

---

With this, the measurements were correct, and was kept like this for two three days to see how consistent/error prone the readings were. After a week (where I'd setup the rpi again and dusted off the old grafana dashboard to point to the new values) of monitoring, and realizing that it seems as good as it could be for now, decided to finally open up automatic motor control. Turned it on and it worked like a charm. Will need to continue monitoring for a while, but I'm optimistically calling this project done, finally.

---

Update two years later: Neither the controller, nor the indicator, nor the sensor work now. So ya, that was a complete waste of time. Though I’m using the rpi as an audiobook library, so at least thats fine.

---

Two more years later, the audiobook library has been moved to separate server, so the rpi is also unused now. Sigh.

---

Total bill of materials - Rs 3864

Total R & D cost - Rs 26008

| Component                             | Cost  | Date               | Final Component | Final Cost |
|---------------------------------------|-------|--------------------|-----------------|------------|
| Nodemcu                               | 384   | January 23, 2021  | Yes             | 384        |
| Ultrasonic sensor                     | 169   | January 23, 2021  | No              | 0          |
| Electronics basics kit                | 840   | February 8, 2021  | No              | 0          |
| Electrical wire and plug              | 130   | February 12, 2021 | No              | 0          |
| Charger                               | 250   | February 12, 2021 | No              | 0          |
| Nodemcu                               | 399   | March 6, 2021     | No              | 0          |
| 8x8 LED Matrix Display                | 191   | March 7, 2021     | Yes             | 191        |
| Multi plug                            | 204   | March 12, 2021    | No              | 0          |
| Raspberry Pi                          | 8111  | June 22, 2021     | No              | 0          |
| Raspberry Pi Case                     | 330   | June 22, 2021     | No              | 0          |
| Sandisk 256 GB Card                   | 3792  | June 22, 2021     | No              | 0          |
| SD Card Reader                        | 634   | June 22, 2021     | No              | 0          |
| Raspberry Pi Case Fan                 | 565   | June 29, 2021     | No              | 0          |
| LED Matrix                            | 219   | July 5, 2021      | No              | 0          |
| Raspberry Pi Micro HDMI Cable         | 299   | July 22, 2021     | No              | 0          |
| AC to DC Convertor                    | 375   | July 17, 2021     | Yes             | 375        |
| Wemos D1 Mini                         | 368   | July 17, 2021     | Yes             | 368        |
| Terminal Connectors                   | 198   | July 19, 2021     | Yes             | 198        |
| Single Core Wires                     | 89    | July 19, 2021     | Yes             | 89         |
| Dot Boards                            | 51    | July 19, 2021     | Yes             | 51         |
| Jumper Cables                         | 115   | July 19, 2021     | No              | 0          |
| Breadboard                            | 183   | July 19, 2021     | No              | 0          |
| Soldering Kit                         | 247   | July 19, 2021     | No              | 0          |
| 4 Channel 5V 10A Relay                | 330   | July 19, 2021     | No              | 0          |
| Multimeter                            | 240   | July 19, 2021     | No              | 0          |
| Nodemcu                               | 394   | July 23, 2021     | No              | 0          |
| Micro USB Cable                       | 199   | August 9, 2021    | No              | 0          |
| 5V 30A Relay x 2                      | 686   | August 10, 2021   | Yes             | 686        |
| AC to DC Convertor x 2                | 300   | August 10, 2021   | Yes             | 300        |
| Dot Board, Copper Clad, Sensor, etc.  | 790   | August 10, 2021   | No              | 0          |
| 5V 30A Relay                          | 343   | August 18, 2021   | No              | 0          |
| Wemos D1 Mini x 2                     | 856   | August 27, 2021   | No              | 0          |
| Nodemcu                               | 397   | September 1, 2021 | Yes             | 397        |
| Buzzer                                | 169   | September 1, 2021 | No              | 0          |
| Candles                               | 10    | September 4, 2021 | No              | 0          |
| SD Card 64 GB                         | 633   | September 12, 2021| No              | 0          |
| Waterproof Ultrasonic + 3x Regular    | 825   | September 17, 2021| Yes             | 825        |
| Ultrasonic Sensor x 3                 | 225   | September 17, 2021| No              | 0          |
| VL53L0X                               | 498   | September 17, 2021| No              | 0          |
| VL53L0X x 2                           | 970   | September 26, 2021| No              | 0          |

