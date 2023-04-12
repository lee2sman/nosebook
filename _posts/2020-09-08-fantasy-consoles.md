---
layout: post
title:  "Some brainstorming about Fantasy Consoles 🎮🕹️"
categories: programming art games tools
---

The term fantasy console was originally developed by Joseph White aka *zep*, a New Zealander who lives and works in Japan and is responsible for Lexaloffle games. Joseph has been a developer for almost 20 years. Originally a flash game developer, Joseph found himself rebuilding his own custom game development environments when he switched to new systems or languages. What he originally called Lex grew over time to become Pico-8, an integrated 8bit *fantasy console*. 

<div style="width:100%;height:0;padding-bottom:100%;position:relative;"><iframe src="https://giphy.com/embed/26vIfqxOmTzF98nxS" width="100%" height="100%" style="position:absolute" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></div><p><a href="https://giphy.com/gifs/3d-shadow-pico8-26vIfqxOmTzF98nxS">via GIPHY</a></p>

A fantasy console is based around constraints and is considered a cohesive environment to make tiny videogames. No other software is needed. There is a set palette of 16 colors (though this can be *hacked*); a sprite editor to draw characters or other elements to be used in a game; a map editor to draw a world with your sprites; a code editor with tabs and 8bit font; an individual chiptune sound editor, and a sound sequencer known as a tracker for making songs. And that's it. Pico-8 is coded in a subset of the language Lua, a language I've not previously used but found not too bad coming from my background in javascript and the p5.js library. 

The fantasy console specification means that it starts with an imaginary premise that a physical console could indeed be built to these specifications, and in fact you can easily run Pico-8 on underpowered hardware like Raspberry Pi and my handheld PocketChip tiny linux computer that looks like a modern gameboy. 

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/87jfTIWosBw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


What I love about the Pico-8 is its feeling of intention, constraint and holistic completeness. Saved games or programs are called *carts* and can be exported as image files, which actually contains the embedded code for your program inside the png image file! They can also be exported as html/js files, so you can put them up on a website such as itch.io so that anyone can play your game. There is a built-in browser called Splore inside the Pico-8 fantasy console, where you can browse, play and open up the code of any cart that's been uploaded by others. There is a thriving community of folks who create work in Pico-8. The forum for Pico-8, called BBS, is active, and people share games, codes, ideas, and collaborate.

![Pico-8 code editor]({{"/images/fantasy-consoles/pico8.jpg" | absolute_url}})  
Pico-8 code editor  

I tend to use open source software because it fits my ethos and interests, but I do use some closed-source software particularly if it's made by an individual. Pico-8 is closed source and Joseph generally charges $15 though there are sales often and I believe I may have gotten my copy through a Humble Bundle. 

Pico-8 is so popular it has spawned any number of clones, both open and closed-source fantasy consoles, some that also use a subset of Lua but others that use Basic, Javascript, C++, and other languages. These fantasy consoles have their own constraints for color palettes, pixel size, how games can be shared, and their APIs. The most popular open source fantasy console is Tic-80, which looks exciting but I may keep working on Pico-8 since I'm now starting to be comfortable in it.

![Quiltfolk screenshot]({{"/images/fantasy-consoles/quiltfolk_012.png" | absolute_url}})  

For my first Pico-8 project I created a proceduraly-generated tiny village called Quiltfolk. This small vignette (I took the term from Mike Cook of ProcJam who used the term to describe some of his software works) is less a game and more of a small place to explore. You walk around the generated village meeting townsfolk and occasionally visiting various houses where the inhabitants will show you their (generated) quilts, which you then compliment. And that's mostly it for gameplay. At some point I may possibly introduce more roguelike gameplay elements or perhaps fork and make something new in this line. I'll be sure to write up a post if I do so.

What I love about the idea of a fantasy console is its united develpment environment and productive constraints. With some basic coding knowledge and the language's reference one has enough to start making games and software. The same could be said for other software, but I like that it imposes limited choices on you. There are no libraries you can add. You can't interface with the internet. There are limited keys (arrow keys and two other buttons). No externally-produced recordings or image files are permitted. In fact, you must make chiptune-style audio. There's even a limit to file sizes and number of instructions. And with that, you have essentially a small studio environment to work within. 

![Quiltfolk gif]({{"/images/fantasy-consoles/quiltfolk_0.gif" | absolute_url}})  

I have ideas for some other *fantasy consoles* or console-like environments. One idea is to use dialog, the 30-year-old library to create text-based dialogue boxes in the command line. One could combine this library with some constraints of the Bash language in a smaller Domain Specific Language (or not) to produce a way to make dialogue-based games, almost like a command line Twine engine. I've made one demo program, [Secret Sound](https://github.com/lee2sman/sssh) (aka ss.sh) as an example of this. It relies on Bash and a way to play audio (any of four different sound engines can work). It would be nice to wrap this into a fantasy console that includes a sound sampler, text editor, and maybe ASCII art tool, and dialogue flowchart, something to reward creating story-based games in this format. A base code framework to jumpstart a micro-genre.


![Secret Sounds]({{"/images/fantasy-consoles/screenshot.jpg" | absolute_url}})  

This is also making me think of ideas for cohesive game-creation mini engines like Flatpak to make flatgames or my p5.flatgame creator. I'd like to turn this into a constrained beginner-friendly tool.

I noticed when using Pico-8 that I had to go online and search for solutions to problems such as collision detection. I think it would be nice for the engine to be able to do automatic collision detection with a builtin function call, especially since Pico-8 is intended largely for making simple 2d games, but no matter, I implemented my own. But I think for beginners, this info would be harder to find and use, so I'm trying to be mindful of the right cross between beginner-friendly and wide enough to let intermediate and advanced users shape the tool to their needs.

I have been drawing with pen and crayons in a notebook recently. I have made maps, sketches, writing and flowcharts. In a certain light I could consider this my own analog fantasy console. I have the constraints of the page and paper, the limited crayons from a box, and my basic pen. From these constraints I can write, make pictures, stories, take notes...It's a fluid process that's hard to replicate digitally. I've been brainstorming alternative cyberdecks and minimal tablet-computers recently, especially ones combining drawing or cameras with a keyboard and limited software. I may go deeper into exploration mode here and build more tools along these lines.

And that ends this post about fantasy consoles. Go [try one out](https://paladin-t.github.io/fantasy/), or make your own!
