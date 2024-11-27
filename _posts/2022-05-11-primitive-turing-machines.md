---
layout: post
title: "Primitive Turing Machines on the Monome Teletype 🎶🎰"
categories: [music, programming]
---

When I was a child and wanted to learn to program I got books from the library on Logo and Forth. I never got to actually program in those languages as a kid because I didn't have access to a computer at that time, and certainly not one with those languages installed. But I remember spending hours reading about these languages and trying to understand programming and how it worked. I got an inkling of the main ideas, but of course, had no ability to actually implement anything. 

LOGO is a children's language, and the illustrations in the books combined with their children-oriented lesson plans meant that I actually understood the ideas and to some degree was able to *program* in my head. So programming was to me like chess, another subject I spent lots of time reading about in library books, where you thought through the moves in your head. Like LOGO, there was an actual language in chess, the algebraic notation and alternative notation systems that I would read in the books and use to move pieces on the chessboard. 

Jumping ahead: I took experimental music production classes in the music department and played the Buchla synthesize in college, though of course I had limited knowledge at that time and was probably afraid of blowing it up. Although I've continued to do experimental music over the past 20 years I only started playing a eurorack synth a bit over a year ago. It's an expensive hobby, with each module costing hundreds of dollars, and you need a small handful to even get started. For a long time I was an artist and worked in arts admin and I didn't have the ability to spend this kind of money, so over the years I've used free software on the computer, my voice, strange cheap pedals and effects, affordable midi controllers, and even a cassette tape 4track given to me by a friend.

My current eurorack setup consists mostly of modules from Mutable Instruments and Make Noise. I've attempted to build something like a Bucha Music Easel, a laptop (as opposed to suitcase-size) synthesizer by Don Buchla, notable for a particular sound and approach that eschewed thick synth notes and filtering as well as traditional piano keyboard input. The sound of the Buchla music easel is a beautiful organic sound and the instrument is an intuitive cohesive system. I borrowed module selection from the easel's parts, and added in a tape machine module as well as the Monome Teletype.

### Monome Teletype

That takes us to my current setup. I have the Monome Teletype, a module that is essentially a primitive computer. You plug a computer keyboard into the front of it. It has an input section and two output sections for plugging in cables. You write short little programs which you can save in memory banks. Plugging in cables and sending a gate input will trigger a program to run. For example, you could a have script 1 that is a coin flip module. When script 1 is triggered with a gate signal running in, script 1 flips a coin (metaphorically) and if a 0 comes up, no output, if a 1 comes up, trigger a gate out running into the trigger of my oscillator. 

Okay, that's just a very simple example. 

The module is programmed in a language similar to Forth, a stack-based, quite old language, developed to be small and efficient and simple and powerful. It is particularly useful on small hardware as the language also functions as an operating system and debugger. 

I built a minimal primitive Modular Turing Machine. What is the Turing Machine? It's not the device described by Alan Turing or the Turing test that's named for him. In Modular Synths, the Turing Machine is a shift register device. It has a number of bits, and essentially plays a pattern of notes. Originally devised by Music Thing Modular, there are a number of manufacturers and implementations. They each work a bit differently. The main idea is that rather than the player creating a small sequence of notes that they repeat, the Turing Machine does it for you. And over time, it begins to drift, as one note at a time slowly shifts to a different note. This makes for a (potentially) calming wave. And since I'm not really a keyboard player, and I love working with generative art and music, I've been really keen to have a Turing machine module. There is one built into the Disting Mk4 a kind of swiss-army module I own, but it is limited, and I didn't love it. I had been thinking for a while about buying one of the turing machine modules on the market, but some are quite large, cost hundreds of dollars, and seemed extraneous since I had this Teletype. Now that I've implemented my own in code, I'm glad I waited. 

### My method:

1. In the init script, loop from 0 to 10 and push a random note number onto the end of the pattern. Also, you could set the tr.time (length of pulse time for a gate output) here.

2. In script 1, when it gets triggered, play the next note from the pattern p.next. This I have triggered by a constant clock cycle.

3. In script 2, pick a random index from the pattern p between 0 and p.l (the length of the pattern) and change that note randomly to a number between 0 and 20. 

That's it! It's really a Turing Machine demake! But I dialed it in using the clock output on my Make Noise Wogglebug and the Burst output. It produced beautiful slowly driving bell sound output that sounded so lovely I ended up letting it play for about an hour, recording the whole thing. Need an album title: Primitive Turing Machine? Why not.

 Going forward, there's lots I can do to extend this. I can use the parameter knob to control the length of the pattern so there are fewer or more notes. Or I can use the parameter knob to increase or decrease the probability that one of the notes in the pattern is changed randomly. I could make a second pattern in init that stores a length of time (maybe 50 to 400?) to pulse each note for each step of the musical sequence. And there's way more options possible. That's only the start.

My code is below:

### Init

This script runs when the *scene*, which is what we call a collection of scripts, is started initially. We loop from 

```forth
L 0 RRAND 4 10: P.PUSH Rand 20	
```

### 1

Now we simply take the next item in the pattern and output that as a note in voltage on CV 1 output. I have this hooked up to v/Oct on Mutable Instruments Plaits. In other words, this script is what changes the pitch of a note. Line two is a trigger output, which I sometimes am using to trigger the trig gate input on Plaits and/or Rings.

```forth
CV 1 N P.NEXT
TR.PULSE A
```

### 2

This script should be triggered less often than script 1. When this runs, it picks a random item from the pattern (between 0 and the p.l aka pattern-length.) and sets it to a random number between 0 and 20. 

```forth
P RAND P.L RAND 20
```

And that's it!

---

Some songs written with this module.

<iframe style="border: 0; width: 100%; height: 120px;" src="https://bandcamp.com/EmbeddedPlayer/album=2202884053/size=large/bgcol=ffffff/linkcol=0687f5/tracklist=false/artwork=small/transparent=true/" seamless><a href="https://exquisitecorp.bandcamp.com/album/its-dangerous-to-go-alone">It&#39;s Dangerous To Go Alone by Exquisite Corp</a></iframe>
