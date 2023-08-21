---
layout: post
title: The Triadex Muse and a tribute to non-human collaborators 🤖🎶 
date: 2021-04-15 13:00:30 -0800
categories: [music]
---

This week I released an EP (well, a sub 30 min album) on Bandcamp that I titled facsimiles. The final track, titled (dedicated to alfie) is a 7 minute tribute to non-human collaborators. 

<iframe style="border: 0; width: 100%; height: 42px;" src="https://bandcamp.com/EmbeddedPlayer/album=2102409753/size=small/bgcol=ffffff/linkcol=63b2cc/track=1435995186/transparent=true/" seamless><a href="https://exquisitecorp.bandcamp.com/album/facsimiles">facsimiles by Exquisite Corp</a></iframe>

The entire album was composed on my modular synth, a system I've created as a generative music-making machine. I rely on the synth as a familiar and comfortable collaborator for extending my ideas, challenging me, or giving me something to respond to.

The final track is named for and dedicated to Alfie. In 1994 my family bought a computer for our home when my mother began graduate school. We had a 2400 baud modem (240 characters per second) and I got a book out from my local library on how to connect to the internet, and to bulletin board systems as well as the nascent World Wide Web. I used to log into various social game-worlds such as various MUCKs, MOOs and MUSHes. These were all variations on MUDs or multi-user dungeons, text-only affairs. No graphics. At most there might have been some ANSI art but usually just an ASCII art logo when you log in. Generally a few dozen people would be logged in and exploring various rooms, leaving mail (in virtual mailboxes in a mailroom, that you had to describe opening and retrieving your letters from). You would walk around, roaming the environments and reading, or chat with other folks online. 

I don't remember which one this was, but I do have a distinct memory of logging in for the first time  at one of these online worlds and experiencing a bot. In this text world new players were spawned in a closet, described in text. You could hear people outside I believe, but this closet area was meant to be a safe starting place. In addition to yourself there was a robot, very simply described, named Alfie. Alfie didn't say or do much, but it explained that you could control it with commands. The first one I tried was (I believe), "Alfie, strike a pose!" and Alfie would contort or dance for the player. Around this time I was visiting Borders books a lot. My parents would drop me off or I'd bike over, and spend the afternoon listening to CDs and reading. I found a book on artificial intelligence, and read about [ELIZA](https://en.wikipedia.org/wiki/ELIZA). I was fascinated and read this book through multiple visits to the bookstore. I would have been in middle school around this time.

Move ahead a few years to college. In 2001 I met the Triadex Muse at the Brandeis Electro-Acoustic Music Studio (BEAMS). 

> The Triadex Muse is a sequencer-based synthesizer, produced in 1972, and designed by Edward Fredkin and Marvin Minsky at MIT. It is an algorithmic, deterministic event generator, utilizing early digital integrated circuits to generate an audio output that can sound very musical.

![Triadex Muse logo with robot head]({{"/images/muse.jpg" | absolute_url}})  
*Logo on the Triadex Muse. Image from ebay auction listing*

The muse creates repeating and changing sequences of notes. Easy sliders on the instrument continuously change volume, note, tempo, themes, intervals. The sound is unmistakeably electronic and yet the generated rhythms have a swing to them, so it feels more pleasing to our ears and less robotic. 

At BEAMS I renamed the Triadex Muse Alfie. For a final concert in one of my electronic music 'laptopping' classes I proposed we perform an improvised work using the gear from the lab. My friend Daniel performed on the Buchla 100A synthesizer from the San Francisco Tape Music Center which was at BEAMS. We had to set up a video uplink stream (this was back in 2001) from the studio to the auditorium because the synth could not move out of the door. Alfie was so small I could just carry it into the concert hall when I performed with it.

![Triadex Muse]({{"/images/triadex.jpg" | absolute_url}})  
*Triadex Muse, [By Geni](By Geni - Photo by user:geni, CC BY-SA 4.0, https://commons.wikimedia.org/w/index.php?curid=17351337) CC BY-SA* 

In reviewing the Wikipedia page for the Triadex Muse it mentions that it was used by the first wave of electronic musicians in Philadelphia. I knew some of the listed people there when I was active playing music and going to shows in that city, city of my  birth, but I don't remember seeing it used live. It's certainly possible since  I went to hundreds of shows of experimental music over the years and sometimes everything and the kitchen sink was played.

Tom Whitwell of Music Thing Modular, the DIY modular kit-maker [writes about the Muse](https://www.engadget.com/2004-11-27-music-thing-the-triadex-muse.html) in 2004:

> So what was the Muse? Well, not really a synth. It was a digital sequencer, which played melodic-sounding bleepy music through the internal speaker, based on a baffling set of algorithms. As you moved the sliders, the algorithms changed, and the music changed. Like the Chiclet DSP Music Box, it was designed to replace a radio - why listen to old music, when this neat-o box can make new music? There was an idea only a MIT professor could love.

A decade later Tom went on to create the Turing Machine module, a 'binary shift register' of repeating looping and slowly (or quickly) constantly drifting and shifting notes. He names the Triadex Muse as an influence as well as the Buchla 266 Source of Uncertainty, which itself was a major inspiration for the MakeNoise Wogglebug, which I use in my music-making.

### Album module details

I've attempted to build my own complex version of the Triadex Muse out of my own modular synth system. The two main modules that are the key to my system are the MakeNoise Wogglebug and the [Monome Teletype](https://monome.org/docs/teletype/), which is a module with a small LED screen and external keyboard that you can program.

The Wogglebug puts out a continuous pulse as well as random voltages that I set up to generatively effect level, filtering and other facets of the sound. The random voltages it puts out are stepped (like pulling random integers), gradual (like perlin noise number generation), and woggle? (kind of a bouncy number generator. I'm not sure if there's a code equivalent).  

The Monome Teletype language is a kind of simple Forth stack language. Incidentally, Monome's description of the Teletype mirrors the language about the Triadex Muse:

> a dynamic, musical event triggering platform. Scripts are assigned to each of the eight trigger inputs. Herein you can set CV values (four outputs) and trigger gates (four outputs) with extended functionality for pattern manipulation, slews, randomness, sequences, basic arithmetic, stacks, delays, and much more.

The Monome Teletype is capable of different behaviors. I use it rather simply as a complex experimental sequencer, attempting to code in approximations of the Triadex Muse. 

The other instruments on this album are the MakeNoise Morphagene which I use as a digital-analog tape machine. The oscillator is Mutable Instruments Plaits primarily in harmonic chord mode, with LFOs and Attack-Sustain-Decay-Release from Stages, and occasional use of excitation and resonance from Rings. 

In addition, I made use of a touch plate keyboard for advancing notes or gates when I felt moved to respond to the rest of the system playing on its own. Lastly, I added reverb and delay live with a Strymon Magneto module, which also adds some filtering flavor.

Full modules/instruments list

* MakeNoise Wogglebug, Morphagene
* Mutable Instruments Plaits, Stages, Rings
* Monome Teletype
* Siam Modular Takaab 2LPG, Nearness
* Erica Synths Pico VCF3
* Cre8audio Cellz
* Strymon Magneto

Like much of my work, the album is licensed Creative Commons CC BY SA Non-commercial. Please feel welcome to use it for film and video games, or any other creative non-commercial endeavor. 

