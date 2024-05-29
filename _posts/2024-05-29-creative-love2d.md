---
layout: post
title:  "Creating code-based artworks and projects using Love2d 🖳" 
categories: [programming, art]
---

This week I had an artwork presented in a group exhibition. I built the work as a non-interactive work that continously runs in a generative fashion, in the simplest sense of that term. 

![Pennsyltucky screenshot - artwork with distorted trees, spinning, digital glitch effects]({{"/images/penn.jpg" | absolute_url}})

> Description: A photograph of trees on the edge of a forest running into an urban landscape. This photograph is in the background and is offkilter. Eerie blue gray skies bleed through. Several "glitched" images with a "ranked superpixel" effect that causes their edges to collapse in digital ruptures. It is hard to say what these individual layered glitched images are: perhaps a house or building, a distorted barn, or landscape.

This is a screenshot (and description) of a continuously running infinite length "simulation", so I am just describing one moment. Some of the things I was thinking about: capturing a breakdown of the land, a breakdown of human abuse of land, in-between spaces, Teju Cole's photographs, Steven Shore's snapshots, the novel Graffiti on Low or No Dollars, breathing and staring into the woods where the city runs out.

Many of the visitors today at the opening thought the work was a "video", which I think means they thought I edited video footage in a video editing suite and added animations. I explained it was made in code, and described as plainly as I could what that meant and the general idea of how it worked.

I've previously mostly used Processing and p5.js or html/css/javascript to make my artworks. [Processing](https://processing.org) is a software toolkit, IDE and Java-based library designed for artists, designers as well as beginners to programming to make digital art and simulations. [p5.js](https://p5js.org) is based on Processing, but a port into javascript so that projects work in the web and make use of the advantages of using a browser.

Processing is two decades old, and has inherited a hefty codebase, something like half a gigabyte. p5.js has inherited the logic, flow and functions of Processing. It feels a bit "lighter" to me, but there are also the challenges of working with a web browser, such as the bloat of a browser, the asyncronous system, security challenges and more.

Recently I've been motivated to spend more time using [LÖVE](https://www.love2d.org/) also known as Love2d, the Lua framework for making 2d video games. I'll be teaching a class in it next year so have been spending more time with it. Though I have 8 years of experience or so creating my artworks primarily in p5.js or vanilla javascript I knew in my head it would be possible to build the kinds of works that I make, using many images (photographs) in a collaged manner, and with my sounds (recorded from modular synth), with Love2d. While Love2d was created for building 2d games, it contains most or all of the functions that ship with p5.js for example, and with similar functionality, along with some other functions that I've found useful.

Using Love2d to do "creative code"-based artwork is so far a pleasant experience. I find the language/framework of Lua/Love2d not too different from Processing/p5.js. While I did have to look more things up, the documentation is excellent, and I was quickly up and running, and the default functions seemed to be intuitive. I didn't spend much time in the forum or wiki, but what I saw there was useful and the community seems supportive and friendly.

What I envisioned in my head that I could do in p5.js I was able to do in Love2d, and with similar code. No doubt if I do many more projects in Love2d I'll find some things that Processing or p5.js are better for, and some things that Love2d is better at.

Some quick reflections on that here:

p5.js - excellent beginner-friendly documentation and community. "No code snobs." All are welcome. Great introduction books. Killer video tutorials on YouTube (see: The Coding Train). Online web editor is very beginner-friendly and great for rapid testing. To share work, export and host as a web site.

Processing - The original software toolkit IDE. Useful for making something on a computer that won't be running in a browser, especially if you are learning to code by making artwork or working with hardware. For what it's worth, I tend to teach p5.js first to my new art students. In the past few years I've used Processing to make a video project, which needed speed, and didn't need a browser, so it was better to use than p5.js. To share works made in Processing, export a java-based applet/application. These won't necessarily work on another architecture. Or you can use processing-java from the command line. Exported files tend to be quite large. 

Love2d - If you're making a game, use Love2d! Spritesheets, delta time, ways of working with animation, etc are built in. But even if not making game, I found the advantages for my artwork: speed, and simplicity. Lua is so fast. Even syncronously run programs with huge file imports instantly start up. Tiny and do I mean tiny library. Easy to share for all systems: export a love executable. I also like I can make system calls, access the file system, and do other OS-based work pretty easily.

I considered making some wrapper functions that take love2d functions and make them work more like Processing, essentially trying to build a version of Processing in Lua/Love2d. But I've decided that's more trouble than it's worth, at least for now, so I'm going to keep using the tool on its own terms and seeing how I build out helper functions or change my working method. I will definitely continue to still use p5.js, and I'm teaching a class on p5.js and one with Love2d in the fall.

I'll be continuing to make projects, interactive and otherwise in the months ahead. I may build up a little personal library or template. I'm also excited to work on some games.
