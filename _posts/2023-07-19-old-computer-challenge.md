---
layout: post
title: Old Computer Challenge and Permacomputing 🕰️
date: 2023-07-19 13:00:30 -0800
categories: [community, programming]
---


This post is a recap of my week participating in the [Old Computer Challenge 2023](https://dataswamp.org/~solene/2023-06-04-old-computer-challenge-v3.html). The Old Computer Challenge is a week-long event where folks interested in *smol computing* such as [Project Gemini](https://gemini.circumlunar.space/), [permacomputing](https://permacomputing.net/), and reducing tech consumption spend a week using old or ancient computing technology as their main machine, then report back on their experiences at the end.

![Raspberry Pi 1B running Void Linux]({{"/images/pi.jpg" | absolute_url}})
*My decade-old Raspberry Pi 1B*  

I was particularly interested in trying out this challenge because I've gotten more interested in permacomputing and resisting consumption of technology, especially of computing devices. On some of the online new media and technology educators groups I'm a part of I feel outside the norm. Rather than chasing higher resolutions, more 'latest technology', and ever-more-expensive black box tools I like to teach long-running tried-and-true technology and tools, especially how we can customize, own, understand and break them down. This, along with being able to critique and evaluate our own place in technology (and its ties to capitalism and military technologies) feels important to me. 

In the past couple years a disparate group of folks online have been discussing a nascent movement on permacomputing.

> Permacomputing is both a concept and a community of practice oriented around issues of resilience and regenerativity in computer and network technology inspired by permaculture.

> In a time where computing epitomizes industrial waste, permacomputing encourages the maximizing of hardware lifespans, minimizing energy use and focussing on the use of already available computational resources. We do this {because} we want to find out how we can practice good relations with the Earth by learning from ecological systems to leverage and re-center existing technologies and practices. We are also interested in investigating what a permacomputing way of life could be, and what sort of transformative computational culture and aesthetics it could bring forward. *--[permacomputing](https://permacomputing.net/) wiki*.

To participate in the Old Computer Challenge I had to figure out what computer to use, and I didn't want to purchase another used computer just to participate. At my home I have both an old Chip computer and Raspberry Pi computer. I had some issues getting the Chip to run properly, so I found an Old Raspberry Pi 1B in a shoebox, an old computer I had purchased in 2013 as I was first getting deeper into programming and open source software and hardware. 

I've written previously on working to create digital archives of DIY and artist-run communities. One interest of mine is to do create a useable ecosystem of tools intended for longterm preservation of digital assets like texts, images, videos, websites and the like. Being able to create long-running computers, even old computers, is another goal of mine as an attempt at making resilient machines that could continue to work for several decades. One way to do this is to work with long-running command line software. 

The command line has long been supplanted by GUIs by most people, save programmers and techies. Those of us that use the the command line enjoy its speed, consistency, and ability to automate or script repetitive computational tasks. Importantly, while GUI software constantly changes due to the whims of style, audience, and complications of the graphics pipeline, much command line software works the same month after month, year after year, sometimes for many decades. And it works fairly consistently on every machine.

![The Pi running on my desktop]({{"/images/i3.jpg" | absolute_url}})
*A papershoot camera shot of the Raspberry Pi computer display on the side of my desk in front of a wall and bookshelf. The display shows the command line, a photograph of my bookshelf, and the Lagrange Gemini protocol client.*  

I set up Void Linux, an independent distribution of the Linux operating system, and since I run this on my personal laptop and studio machine, I found it fairly straightforward. For a couple days I ran just the command line without installing a graphical system. On the command line I could use text editors to write this blog, play text games, even read the internet, Gemini, or check the weather all using text-based software. 

This all seemed to work fine and not much slower than my much faster and relatively new (from 2019) i7 laptop. Even startup of this old underpowered computer went fast enough, maybe 10 seconds from power to the command line. I thought about basically just continuing the command line for the week. 

I continued to read the news each day, and countless blogs and gemini logs (glogs!). But a day or two later I decided to do the full GUI setup. I wanted to use a full web browser and look at images. I installed a window manager (i3) and the X windows system to see what that's like. It lets me have multiple workspaces and splits my screen to have multiple programs running at once. It shouldn't have been surprising, but I immediately noticed a slower system. And in fact things started to become annoyingly slow. I didn't even bother with installing Chromium (the open source Chrome fork) or Firefox as I knew it would be too painfully slow, so I installed Dillo and Netsurf as they are lightweight GUI web browsers, and Lagrange as my GUI gemini client.

Did I cheat? You bet. Especially at the beginning of the week, I was checking my work email and doing professional work on my regular laptop. Later in the week I experimented with doing some of my research work on the Pi, which went okay, though slowly. But there was an upside to that. I found that due to the time it took to look things up, it was harder to goof off on the Pi, and so I avoided social media except for approximately once-daily check-ins to my Mastodon server community. 

The other elephant in the room: I continued to use my phone this week for communication, maps, instagram. I think it probably would have been better to take a social media  and phone fast for the week, but I was too wedded to communicating quickly with friends and family. I'm also in an exhibit, and I performed a live concert during the week, so I also felt the need to promote these on instagram. Could I have done without the self-promotion? Perhaps I should have.

For entertainment this week I wanted to play some games. In addition to the text-based *dungeon crawler* Rogue that I've been playing for years I downloaded Pico-8, the raspberry pi edition. I'm planning on teaching a class in making games in Lua, probably with Pico-8, next spring, so I thought this could be a fun environment to test. At first I couldn't get it to run but with some search and forum discussion online I found that I could decipher what libraries were missing, and I downloaded and installed those directly via Raspberry Pi's firmware github repo.

I launched Pico-8, smiling at my success. I have made a number of Pico-8 games, and played many, for the past 7 years. On launch, Pico-8 warned me that it would run at less than 30 frames per second but I persisted. I launched splore, the games browser, and instantly had access to thousands and thousands of games made by people around the world. I tried a 3d game, and it was quite slow, but still manageable. I forgot to test [Poom](https://freds72.itch.io/poom), the Pico-8 clone of Doom, but my guess is that it would be too slow to be fun and that I should stick with puzzle games.

I next tried to watch a movie. I used the command line software yt-dlp to download french science fiction movie featurette La Jetee by Chris Marker. Since it's subtitled and told in a series of still images with a soundtrack, I figured that even if the video couldn't play at a reasonable framerate I'd still be able to watch. Alas, it was too slow and I gave up in frustration.

I was able to program on the computer, using my favored command line coding program Vim/Neovim, but I'm fairly certain GUI software like Geany could have worked as well.

I'm still talking about the command line now: I also downloaded bsd-games, a collection of many games like Backgammon, Adventure, Boggle, cribbage, hangman, mille borne, snake, tetris, and a few dozen more games. I didn't try all of them but it's nice to know they're available. When I teach Social Software this coming semester I'll be adding these games to our shared server.

For "consuming" image and video content such as social media, the Raspberry Pi 1B is not a great system. For even my professional work, I'd need to be a bit careful. The system occasionally quit all my programs and dropped me back at the login screen. This happened about once an hour or so, always when I was multitasking with multiple workspaces. I should have resisted multi-tasking to prevent this! Thankfully my text editor has the *swap* backup system that auto-saves everything written, but it was an annoying hiccup when it happened.

In terms of reading, writing, being entertained - this system worked for me with the caveat that I sometimes just needed to be patient when doing anything with graphics. Void Linux is a great Linux distribution, and it's incredible that a volunteer team maintains the operating system and repositories of software that can work for fast new computers and old minimal ARM computers as well. Contrast this with the billion-dollar Apple computer. There's no way they'll individually respond to you on a forum online or in a chat room to help you fix something on a decade-old computer. 

It was also nice to be using these old computers, writing on them and posting to the internet, reading about other folks experiences with their own Old Computer Challenge. It helps to be working in community.

As the week using this computer ended I'm heartened to know that this 10-year-old tiny pocketable computer can still browse websites I've made, is still a useful computer with tools that feel timeless to me.

Going forward one of my next projects is to work on some simple command line and file browser tool for viewing collections of images and text in the [Archiving Artist-Run Spaces](https://leetusman.com/archiving-artist-spaces/) project. I'd love to have a system that can be more resilient, to resist brittleness, by falling back on basic command line programs and the OS's GUI file system defaults to do the lifting, essentially coding via gluing together basic long-running Linux software. I'm looking forward to testing this out in the weeks ahead.

### References

[Old Computer Challenge V1 2021](https://dataswamp.org/~solene/2021-07-07-old-computer-challenge.html)

[Permacomputing Wiki](https://permacomputing.net/)

[Void Linux - Raspberry Pi](https://docs.voidlinux.org/installation/guides/arm-devices/platforms.html)

[Project Gemini FAQ](https://gemini.circumlunar.space/docs/faq.gmi)

[Pico-8](https://www.lexaloffle.com/pico-8.php)

[BSD Games](https://wiki.linuxquestions.org/wiki/BSD_games)

[Archiving Artist-Run Spaces](https://leetusman.com/archiving-artist-spaces/)
