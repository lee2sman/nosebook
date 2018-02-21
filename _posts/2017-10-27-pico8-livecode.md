---
layout: post
title:  "Pico8 and Processing for Livecoding?"
date:   2017-11-21 18:40:05 -0800
categories: programming
---

# Livecoding
![](https://www.lexaloffle.com/gfx/p8_tracker.gif)

For the past year I have been doing [livecoding](https://en.wikipedia.org/wiki/Live_coding), on-the-flow improvisational electronic music that is created with code live in front of audiences. There are many approaches to making music and performing this way. My own method has evolved and will probably continue to change. Currently, I use a combination of Bash scripts and aliases in the Terminal. I play samples in the Terminal and affect their volume, speed and other effects using the program *Sox*. I also use the software [Sonic Pi](http://http://sonic-pi.net/), the beginner-friendly livecoding software, though I run it in the Terminal with Neovim using a [plugin](http://widdersh.in/controlling-sonic-pi-from-vim-or-anywhere-else/).

![Livecoding]({{"/images/livecoding.png" | absolute_url}})

# Pico8

On the wishlist: I'm a big fan of the [Pico8](https://www.lexaloffle.com/pico-8.php) *fantasy console.* It's intended for learning coding and especially to make and share games. You code with a simplified subset of the Lua programming language. It also features sound-creation and music tracker software. It would be great if there was a way to livecode audio using the Pico8 system. I'm not sure if it's possible, but I'm bookmarking the idea here.

![Livecoding visuals]({{"/images/livecodeviz.png" | absolute_url}})

Lots of great resources for learning Pico8 [here](https://blog.nextthing.co/resources-to-help-you-learn-pico-8-game-development/). In particular, the Pico8 [zines](https://sectordub.itch.io/pico-8-fanzine-1) (there are 4 total) are helpful and fun to read. 

# Processing-like languages for Livecoding

I spend a lot of time coding art and teaching Javascript and P5JS. Pico8 appears to be influenced by Processing and P5. There is a Clojure library [Quil](http://quil.info/) for livecoding art with Processing syntax. I don't know the language Clojure but this could be a great way to learn a Lisp-like language in a framework I'm familiar with. No idea yet on whether it allows working with live-reloading sound. I've also tried out [LiveCodeLab](http://livecodelab.net/) a web-based framework for livecoding a limited amount of 3D elements and sound. It works well but mostly using predefined shapes. It would be nice to develop something like this further that can create more general 3d elements, especially from photogrammetry. I believe I've seen livecoding with Unity, so maybe I'll have to go that route.

