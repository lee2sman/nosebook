---
layout: post
title:  "Building Gameworlds in Puzzlescript" 
categories: [programming, tools]
---

In the past month I've made over 20 games with the PuzzleScript game engine by Increpare.

[PuzzleScript website](https://puzzlescript.net)

[PuzzleScript editor](https://www.puzzlescript.net/editor.html)

PuzzleScript is a small game engine that runs in a web browser, originally created in 2013, and now up to version 1.7. It was originally designed for sliding block turn-based type puzzle games (aka Sokoban-style games) but can be used for other genres as well, including realtime games. 

PuzzleScript's design is a cohesive, intimate coding environment. It works in almost any graphical web browser. The editor has a drop-down menu with 18 full games that you can load, modify, and run. All games have a player character and out of the box pressing the arrow keys moves the player around on the screen, which can be modified. Games can be shared through the browser, using a free Github gist repository, or games can be exported and self-hosted on a website. 

PuzzleScript's web based editor is a work of genius. If you open the editor, you'll notice distinct sections all on the same screen. At the top is meta information like the creator, game name, color palette. Below that you create your sprites as simple quasi-pixel art. Each object in the game is made of a 5 by 5 grid of color blocks. You specify an object name, colors, and then use numbers to represent the color of each pixel. The number comes from the order of colors specified in the line after the object's name. These become the sprites you use in creating your game.

Here's an example player sprite:

```puzzlescript
Player
Black Orange White Blue
.000.
.111.
22222
.333.
.3.3.
```

The hair at the top (000) is black (and will appear that way in the PuzzleScript editor). The face below (111) is orange. The shirt below that (22222) is white. The pants are the 3s, blue. The periods represent background (empty space). Looking at this inside puzzlescript those numbers are automatically colored with their represented pixel color, and then you can add the object to the game with the level editor (top right).

![screenshot of puzzlescript with code editor, level editor, console]({{'/images/puzzlescript.jpg' | absolute_url}})

Next to a game object's name in the OBJECT section or inside your LEGENDS section you specify a character to represent each of your sprites. For example I'll specify that the @ symbol will represent the player:

```puzzlescript
@ = player
```

Other sections in a game file include the Rules section, Win Conditions, Sounds, Collision Layers. 

In the top right box of the editor is the play section for testing out your game when you click RUN. There is a visual level designer here as well if you click level editor button, that lets you draw your level sprites to the screen and then save as an ascii file to paste into your levels section of your game file. In the bottom right quadrant is the console. which prints out error messages or other compilation messages. Between the game play/level editor and console is a tiny strip, the sound creation toolbar. Clicking on one of the sound category buttons generates an 8bit sound sample randomly within some category of soundwave, and prints its numeric code in the console. If you like a sound you can copy its number and paste it into the sounds section of your game file and assign it a rule.

The most complex section of a gameplay file in PuzzleScript is the rules section. In this section is the meat that defines how our game mechanics functions. This mini domain-specific programming language is based on a simple idea: The game engine will look for any specified match on the left side of any game rules. Then it will transform that match into what's found on the right side.

An example will serve to illustrate what that means.

Let's look at the following basic rule:

```puzzlescript
[ player bomb ] -> [ bomb ]
```

On the left side of the arrow (->) is a player and a bomb in the same space. If the game engine finds this condition anywhere on a running game at any time, it will transform that space containing both a player and bomb into just a bomb, which is what we see on the right side of the arrow. In other words, the bomb destroyed the player and only the bomb is left.

Let's modify this a bit.


```puzzlescript
late [ player bomb ] -> [ deadplayer ] sfx0
```

In this version, when a player and bomb are on the same space, the bomb disappears (we can imagine it exploded) and the player has been transformed to a deadplayer, presumably with altered pixel graphics from the regular player sprite. And we also play the sound effect zero (sfx0), which we've selected from the sound generating section and placed into our SOUNDS section.

So our SOUNDS section may look something like this now:

```puzzlescript
=======
SOUNDS
=======

sfx0 85319102
```

The word late added before a rule means that the rule is run after a regular move has occurred. So that way, this rule will run immediately after a player has moved into a space with a bomb and not on the following move. 
In the following rule code, on the left side is a player moving away from something (that's what the < indicates). The rule looks for a moving player away from a crate. We know it's 'next to' because the rule specifies the player and crate are separated with the | pipe character. So this rule looks for a moving player, moving away from a crate square and the result of this is a moving player next to a moving crate with both moving in the same direction. In other words, if a player away from a crate, the player moves and the crate it moves along the same direction, getting pulled one space.

```puzzlescript
[ <  Player | Crate ] -> [  <  Player | < Crate  ]
```

This rule doesn't specify the direction, so if a player moves up away from a crate, it will drag the crate up behind it. If the player moves down away, it will drag the crate down, etc.

These are the basics, and there are many more rules to be learned in the well-written PuzzleScript documentation.

[PuzzleScript Documentation](https://www.puzzlescript.net/Documentation/documentation.html)

In addition to the game rules, there is a section called Win Conditions. A typical Win Condition might look like:

```puzzlescript
Some player on target
No demons
```

To win each level a player must kill all the demons and get to the target.

The last section of a puzzlescript file is the levels section. A creator builds out the levels in ascii using a single letter to represent each of the objects (sprites) from the objects section. 

Between levels it's common to have full screen text messages, such as instructions or a storyline.

```puzzlescript
message congrats: level 3!

......#######...
.....##P.#####..
....###....####.
..#####O...#B..#
..#####.#.##BB.#
##EBB..O.O.....#
..#####.#.#....#
..######..#G.###
....####..#.OOx.
.....###.GG.#x..
......#######...
```

## My puzzlescript process

I usually start informally with a loose concept for story or game mechanic.

Then I do the puzzlescript version of 'grayboxing'. In 3d modeling game design this is the process of building out your 3d world but entirely with gray (or white, etc) boxes, and placing in your first person controller. This lets you immediately have a playable world you can walk in. You can immediately start testing out gameplay dynamics. And you can start placing in 3d models to replace the gray boxes.

My puzzlescript version of this is to start with just a few primitive boxes. For example my OBJECTS section might look like this:

```puzzlescript
========
OBJECTS
========

background .
transparent

player p
blue

wall #
orange

book b
blue
```

This sets up 4 kinds of blocks, gives their ascii code that I can use them to draw out a level and assigns a single color to represent them as a block.

```puzzlescript
=================
COLLISION LAYERS
=================

background
wall, player, book
```

This sets up a dynamic that the player, wall or book can't be in the same space. So a player could bump into a book, but can't stand on it, for example.

And then I may draw a level like this:

```puzzlescript
=======
LEVELS
=======

########
#......#
#....b.#
#.p....#
#......#
########
```

I'll start without any rules or win conditions. So out of the box I hit run and can use the arrow keys to move the player.

This is a tiny little room. Let's add some rules.

```puzzlescript
======
RULES
======

[ > player | book ] -> [ player | book ] message You pick up the book. It's Labyrinth, by Jorge Luis Borges
```

On the left side of the text arrow -> is the condition. On the right side is what that condition causes.

The left side says "any player moving into a book" and the right side says "results in the player still standing next to the book" and then prints the message there to the screen.

This is not yet even remotely a fun game yet, but there are many possibilities for development now going forward.

## My love for PuzzleScript

I love any game-making or coding environment with good presets and delightful constraints. It's a perfect 'rapid prototyping tool.' Like fantasy consoles such as Pico-8, PuzzleScript's constraints help shape the outcome, encouraging small ideas that can be iteratively tested and modified and played again. In fact, PuzzleScript feels like a 'smaller' tool even than Pico-8. Having the drop-down menu with premade modifiable games, a built-in player controller using arrow keys, and the one-click sound effects creator all help with the quick release cycle. Working in a web browser means the tool can be used without having to set up a coding environment or installing anything. And the one click export and share features make it easy to share one's game, complete with a 'hack' option that lets players open up and remix your own game file.

The presets on PuzzleScript are smart. Each game has a title, author and optional link to a website. The only way to have text in a game is using the message command, which allows one to tell a story or give simple instructions. The only 'action' button possible beside the movement directions is the X or Spacebar action key, and the ability to undo or reset is built-in automatically, or can be turned off. 

The integrated development environment and quickstart options makes the tool strong. Increpare has done the hard work of debugging and making it all work well together. Since he's created it as open source, a number of forks have been created with added features, and tutorials are available around the web. A great community of game-makers have grown around it, and games can be found on itch.io, Increpare's own PuzzleScript games, a PuzzleScript email list and elsewhere. Give it a try.

[Awesome PuzzleScript](https://github.com/lee2sman/awesome-puzzlescript) - this is a list of Puzzlescript links and resources I compiled a few years ago. *Pull requests* or suggestions are welcome.

