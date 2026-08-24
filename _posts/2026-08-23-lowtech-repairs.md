---
layout: post
title: Some Lowtech Repairs 
categories: [open source, creative code, programming, permacomputing, L5]
---

I've lived in a number of cities (and continents). I grew up in the US and I'm accustomed to American culture. I've always disliked our culture of consumption, as much as I've also benefited from it.

This has only increased during my lifetime, and I regularly find myself as I get older learning to appreciate well-made and home made items, particularly things that wear better with age.

> As interpreted by others, the whole mindset of “beausage” is that things gain beauty when they are used, and used regularly. --*[That Thing Called Beausage](https://accidentalrandonneur.wordpress.com/2017/03/15/that-thing-called-beausage/)*

This also goes for items that can be repaired. In an era of planned obsolescence, much of the technology we use is extremely brittle, with a short intended lifespan.

In contrast, as I've increased my own technological skills I've gained some knowledge and ability to figure out how to repair some items. I've also benefited from knowledge gained online, from tutorials (shout out to the old Instructables and to a million people's blogs!) to in-person workshops, makerspaces, and friends' studios. 

That said, here's a few recent repairs from the past month:

## 'Fixing' the too-long headphone cable on the Sony MDR-7506

I LOVE this headphone. Absolutely love it. In college one of my study tracks was electroacoustic music production, and we had a pair of Grado SR-80 headphones, and I purchased my own that I used for many years, and even had them repaired by the company at their original headquarters in Brooklyn. But these are home studio headphones, not intended for public listening due to their open back design that bleeds audio, so many years ago I tried a friend's Sony MD-7506s, which I loved and then purchased my own.

Every film or theater production tech has used these headphones. If you see people shooting a film, recording a documentary, or working backstage in a theater there's a pretty good chance they'll be wearing these, and for good reason. They're built well, sound quality is good, and they're comfortable.

But the cable is a mile long. Seriously, it almost reaches to my ankles, and I'm tall! I don't want it getting snagged by a passing subway train. I've always thought about cutting off the long coil cable and soldering on a straight cable, but I couldn't be bothered.

Finally I thought about revisiting this option and looked for a little tutorial online or documentation of other people that have tried this. But in my search I stumbled across this incredible [no-soldering solution](https://youtu.be/TtJFX36WOjo?si=aBs_nuLF9TqRtDGq) by Michael Wynne. It's simple to do, takes only a couple minutes, and it has indeed shortened the cable to a more manageable amount.

![Headphone selfie]({{"/images/headphones.jpg" | absolute_url}} "selfie with headphones")  

## Fixing the latch on my eurorack synthesizer case

I've had the Intellijel 7u Eurorack case for about six years now. It does the job, and I appreciate that Intellijel developed the 1u row for utility tool modules. But I've also always found the case a bit overpriced for the value it brings. The black plastic feet are half missing, and the corners never came together well. I've always been worried about bringing my synth out in the rain when I'm on my way to gigs or practice sessions. The thing also weighs a lot. 

I have been looking for a waterproof gig bag forever, and I resent having to pay an additional $125 for a bag on top of the $600 or $700 case (whatever it costs these days, I bought it for much less years ago). And that's when the bag can even be found. It's currently sold out everywhere, including directly from the manufacturer. I've scoured online for other waterproof or water resistant bags of similar dimensions and came across one for a fifth the price that I've been using for the past 6 months as I travel between the US and Europe and across the continent. Well, I made a mistake. Walking through the airport in Vienna not long ago the strap for my generic case snapped and my synth fell to the ground! The horror. The case was damaged, but thankfully my modules all seemed to play okay. But the riveted latches were completely broken off in the process.

I duct taped my case back together and brought it to a gig in Vienna then on the train with me to Berlin. There my music collaborator Janek took a look at it, and we chatted through some solutions to fix it. In the end, he had enough bits and blobs and tools at home that we ended up using tiny modular screws and bits of leftover eurorack rails that we cut with a saw and filed, and while it's not a perfect and seemless fix, I think it will work!


![Janek leaning over my synth]({{"/images/caserepair.jpg" | absolute_url}} "Janek leaning over fixing the eurorack case")  

## Replacing a hard drive on an old desktop

A few years ago I bought a desktop Dell computer (an Alienware Aurora R7) off ebay. It had good specs except for a pretty crappy hard drive. I used it as a studio computer at my old art studio so I wouldn't have to bike back and forth with my laptop each day. Two years ago we gave up the studio we were renting as a group of friends when the landlord raised the rent. Aside from this I do still have a shared music practice space at Flux Factory, but as it is so far from my home my software and 'art studio' practice I do from a studio in my home now. 

![The guts of an Alienware Aurora with drive pulled out]({{"/images/oldharddrive.jpg" | absolute_url}} "Inside the guts of an Alienware Aurora R7")  

As such, I mostly used my laptop and stopped using the *studio computer*. Until recently. I needed to do some work on a different Linux distro, and I just thought it would be nice to set up an exclusively studio computer again. But when trying to flash antiX Linux (and then trying Devuan and Debian), I couldn't get any of them to work. It would fail almost immediately when writing to the drive even though the live USB would always work. From reading online I suspected a drive issue, and I first tried replacing the SATA cable. When that didn't work I decided to take a chance and bought a new but extremely affordable hard drive. It's a *lowly* 120GB but that should be more than enough for a lot of my studio work. Especially in this AI / LLM-pilled time where data centers are snatching up every hard drive and GPU and Pi sold. Incidentally, check out the L5 creative coding library I initiated for more examples of creative computer software designed for modest hardware specs including smaller hard drive storage. 

Opening up the Alienware, I popped out the old cheap drive, popped in the new one, and in less than 5 minutes reflashed the antiX operating system and had a fully working computer. I was so pleased and have been using it every day since.

![The Alienware desktop starts up]({{"/images/alienwarestartup.jpg" | absolute_url}} "The Alienware startup logo on my screen")  

### Outro

Little repairs are satisfying, scratching the puzzle-solving itch, saving money, reducing consumption, and sparking joy. I should give it a shot more than I currently do. These little successes are reminding me I can do this even more. I see some sewing and woodworking projects maybe coming up on the horizon...
