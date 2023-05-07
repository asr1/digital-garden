---
{"dg-publish":true,"permalink":"/projects/custom-singstar/","tags":["projects"],"noteIcon":""}
---

(adapted from the [Twitter Thread](https://twitter.com/AlexRinehart_/status/1500176752445849600) I made at the time)

I wanted to see if I could get a custom SingStar game to run on a PlayStation 2.

The PS2 is the best-selling video game console of all time (even above the Wii)!

SingStar is a series of Karaoke games for the PS2.

There are two challenges here: 1. Can I get my PS2 to run custom software and 2. Can I build a custom SingStar game

### Aside

SingStar games have a really neat feature where, between songs, you can swap discs to another singstar game and it will remember your current score, whose playing, and similar settings. I didn't end up using this, but I want to highlight the innovation!

---

## Unsigned Code

When a proper retail game is made, it's burned onto a disc, and is digitally "signed" by Sony. Any games without this signature won't play on a traditional PlayStation. Naturally a lot of people want to bypass this.

Broadly speaking, there are 3 types of PlayStation 2: the traditional Phat model, the classic Slim, and the modern (2009) slim. I'm using a Slim Classic.

There's (generally) two ways to get a console to run unsigned code: 1. A modchip, usually soldered to the motherboard 2. A softmod, done entirely through software. We're going with #2, and until recently, only the Phat and Classic slim versions could be softmodded.

Typically the way this works is by exploiting insecure code in a game or in the operation system (here in the DVD player). Usually this looks like a buffer overflow, where code says "I want to read 20 characters" and you say "Okay, here's 5,000". Safe code caps it at 20.

If the code is vulnerable, exploiters can dump their own code in here (called a payload) and convince the system to execute THAT code as if it was signed. Once that happens, it's game over. This process is hard and takes years. Once it's out, others can do it in minutes.

The most recent PS2 Hack was discovered just months before I started this project, in 2021 by a modder named CTurt. There's an [incredible writeup](https://cturt.github.io/freedvdboot) of the process online.

Because of that effort, But we'll come back to that. For now, know that it takes about 5 minutes to softmod a PlayStation 2. Really you just need a DVD burner, a blank DVD, and a USB stick. Luckily, I had those sitting around.

So now, in theory, my PS2 can run custom software. But wait! On an Xbox, you could burn a game to a DVD, pop it in, and run it. On the PS2, that didn't use to be the case.

Ignoring DVDs, there two ways to get custom games to work: an easy way, and a hilariously convoluted way. Let's start with the easy way. (I will eventually end up using DVDs, thanks to CTurt).

### The Easy Way
If you take a game that you own, put it in your DVD burner, extract out the files and burn them to an iso, you have a backup. Whoo! Put this iso on a flash drive and stick it in your PS2. In theory, it will play! 

Well, there's two problems. The first is that the PS2 uses USB 1.1. In theory, it can transfer 12 Mbps. That's faster than the DVD read speed of 5.28 Mbps. In theory. In reality, loading a game over USB leads to stuttering if you're viewing cut scenes or movies. I THINK that the PS2 is capped at the low read speed of 1.5 Mbps, not able to tap into the full speed of the spec.

It COULD be that we are getting the full speed, but DVDs are optimized in some way that USBs aren't, but that feels like more of a stretch. Anyway. 

The second problem is one I care more about: The way this softmod works is that it tells the PlayStation "Hey, I PROMISE you that this USB drive is a DVD." It maps the input from one to the other in a big lie. This means you can't ACTUALYL use the USB ports while gaming.

The whole goal of this is singstar. It uses two Karaoke Micropones connected via USB. The PlayStation can't handle this. It interprets it as DVD data. So USB won't work. Dead in the water. What about the second way of loading games?

### Aside: A secret third way
There's a third way that isn't viable here, but it's the best: actually loading the games onto a hard drive. Unfortunately, the slim models don't HAVE a hard drive, so this option is untenable. So we're stuck with the silly second way: the Raspberry Pi.

---

### The Silly Way
All PlayStations have an ethernet port. Ethernet has a top speed of around 100 Mbps. But I can't just take my ISO and put it on an Ethernet cord. But what I CAN do is set up a Raspberry pi to pretend it's a disc drive, serving consecutive segments of an iso over ethernet.

Then you tell the PlayStation hey I PROMISE that this ethernet port is a DVD drive (while trying to keep a straight face—if it detects you're lying to it, it'll shut right down). This removes the stuttering problem and should work!

So could do this, but I gave my last RasPi away the year before. So let's go back to the DVD, thanks to Cturt

## Back to DVD!

Thanks to Cturt, we can read custom DVDs. Great! So what about the SingStar game?

## Problem 2: Singstar

Your first idea might be "hey, can I take my existing singstar game, rip it to my computer, tweak the files, and then burn it back?" Maybe! But probably not. Even if that worked (which assumes there's no data integrity check), the song would be all wrong.

You'd be singing Smash Mouth to the tune of Maroon 5. *(this is, of course, conjecture. I have not, and probably will not try this approach).*

So what CAN we do? Well, if we dig in to a SingStar file, we can find that it contains a few things: first, a song has a cover art. This appears during the menu when you pick your song. So we need a jpg. Next we have a movie that plays behind the lyrics. Then the interesting bit

Each song has a text file that dictates what the lyrics are, as well as what notes correspond to the lyrics. We're going to look at Re: Your Brains by Jonathan Coulton, since the song is licensed by creative commons. As you can see we've got metadata like beats per minute.

![coulton song.png](/img/user/img/coulton%20song.png)

This would be a HUGE pain to make by hand! There are tools like Performous Composer (pictured below) that let you set the notes and durations of various lyrics as you play a song. This is still a painstaking process that requires listening to a song until you hate it.

Also Performous is a PAIN to use. It constantly looses your place, and has a lot of weird gimmicks (like not processing changes until after you commit the next one).

![performous.png](/img/user/img/performous.png)

Surely someone has done this for us? Well obviously in the case of JoCo songs, yes. Otherwise...maybe! UltraStar, which is a Windows clone of SingStar, has a repository of songs... but ONLY the lyrics and notes you see above. You have to provide the music video and art.

Not a big deal, as long as you find the RIGHT music video. Nothing worse than out-of-sync Karaoke. Once you have this, there is a tool called SingStar Creator that converts UltraStar to singstar's format. (the JoCo image above was ultraStar, not SingStar)

One problem: the tool only exists in German. But we live in the future and have translators at our fingertips!

![Translated Singstar Creator.png](/img/user/img/Translated%20Singstar%20Creator.png)

So in theory we have what we need: * A PlayStation that can play unsigned software * A song in the UltraStar format (re: your brains by Jonathan Coulton) * A tool to convert UltraStar to SingStar * The ability to build that to an ISO So let's jump in!

## Testing it Out

The first thing I did was burn a copy of Gran Turismo to DVD and see if it would work. I tried the same over USB.

I actually made a mistake here with my choice. Gran Turismo is too big to fit on a DVD using conventional methods. At the factory it's made using a double-layer disc. I should pick a smaller game.

### Aside on disc burning
I always liked DiscJuggler, which had the nickname "discmangler" because if you didn't know what you were doing, you could easily waste a disc or two. 

I also like Nero, just for the pun (Nero fiddles while ROM burns).

The PS2 community has settled on IMGBurn, an open source disc burner that inexplicably plays a woman's voice going "Ohhhh Noooooo" whenever something goes wrong. I am not a fan.

---

All right! I tried again with a SingStar game and SUCCESS! ....Mostly. Still no DVD boot, but it worked from USB. This means to actually PLAY the game I'll need a Raspberry Pi, but I should be able to verify that whatever I can clobber together will run.

The big question is if I need to build it entirely from scratch, or if I really need to dig into that ISO and do some replacing of files. 

Time to return to that German tool.  It patches custom songs into a (German) version of SingStar pop. So we out our songs in, select some files, and voila! A new iso appears!

(I was also able to get games larger than 4 GB booting off USB, but that's a different story, one which I didn't elaborate on at the time and have no memory of now)

## Results!

So we have our custom iso... Let's take a look! ... Well, it works. But of course it's entirely in German.

![German Singstar Cropped.png](/img/user/German%20Singstar%20Cropped.png)

But this is still going off of USB, which means I can't get my microphones to work at the same time!

A little more fiddling, and I was able to figure out the DVD settings AND find the switch to put it all in English. 

Now I have custom SingStar tracks!

I even experimented with making my own, but Performous isn't an easy tool to use, and the timing quickly got away from me. Perhaps if I had a better sense of Rhythm. 

These burned games aren't perfect (they get about a 60% success rate, and sometimes the notes are wrong), but it sure is neat to experiment with it all and know that it CAN be done!