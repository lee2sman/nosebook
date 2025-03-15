---
layout: post
title: Programming a BASIC Game 🎰🎲
categories: [open source, creative code, programming, tutorial]
---

![Cyberhoss AI]({{"/images/log/cyberhoss-ai.png" | absolute_url}})  

For the past couple months I've been exploring BASIC through the implementation Yabasic, a modern procedural-based implementation of BASIC.

Today I presented the workshop Programming a BASIC Game at the [Electronic Faire 2025](https://sites.temple.edu/efaire/) at Temple University's Charles Library.

I started by presenting an early history of Basic at Dartmouth, both its creation and the technical and community aspects relating to its founding. Then I went on to describe a history of timesharing and later the rise of microcomputers. I showed games created in Basic, with a focus on type-in games, particularly those that were part of the People's Computer Company magazines and books as well as David Ahl's Basic Computer Games.

Finally, I presented a brief introduction to programming in Basic in the implementation Yabasic.

Since we were at the Charles Library, an incredible university institution, we checked out copies of [The Best of Creative Computing](https://archive.org/details/Best_of_Creative_Computing_Vol_1_1978_Creative_Computing_Press), edited by David Ahl, and some other BASIC books from the 1970s.

[My Yabasic Games repository on GitHub](https://github.com/lee2sman/yabasic-games)

[Slides](https://github.com/lee2sman/yabasic-games/blob/main/slides.pdf) (PDF)

[Slides](https://docs.google.com/presentation/d/1zZ4FVsBcjpZPdGgco8aE0CsfcyuVwuOoBaO6PkX0xXU/edit?usp=sharing) (GDrive)

## Yabasic Resources

[Download Yabasic](https://2484.de/yabasic/). This is pretty straightforward currently on Linux and Windows. See Mac install instructions below. 

**[Yabasic Reference Manual](https://2484.de/yabasic/yabasic.htm)**

[TutorialsPoint Online Ya Basic Compiler](https://www.tutorialspoint.com/execute_basic_online.php) if you don't want to install on your own computer. It requires no login. Beware this is unsecure. You can drop into a bash shell and read other users' files on the system.

## MacOS

Written March 2025. Thanks Paloma and Richard for discovering/testing this.

Using the Yabasic Unix binary works on MacOS, but is a bit tricky to get working.

1. Download the yabasic tar-file from [2484.de](https://2484.de/yabasic/download.html)
  Search for "Compile the sources for Unix"
1. Uncompress the tar file (see instructions above). You should end up with a folder like yabasic-2.91.1/
1. Install homebrew from [https://brew.sh/](https://brew.sh/)
1. Install libffi using homebrew: `brew install libffi`
1. Install xquartz using homebrew: `brew install --cask xquartz`
1. Go to your yabasic-2.91.1/ folder. Run `./runme`. This installs a `yabasic` executable.
1. Type `./yabasic` to open the `yabasic` interpreter
1. Alternatively, if you have `.yab` file, run `./yabasic yourfile.yab`

## The Games

Note: The game code here is intended for those new to programming: heavy commenting, global variables, magic numbers, and verbose programming *style* abound. 

Also note that these are demo games and may contain bugs and lots of opportunities for improvement!

### Catanite

[Code](https://github.com/lee2sman/yabasic-games/blob/main/catanite.yab)

This is a simple economic simulation game inspired by Star Trader and Dope Wars/Drug Wars.

### Cyberhoss

[Code](https://github.com/lee2sman/yabasic-games/blob/main/cyberhoss.yab)

This is a cybernetic *hoss*-racing gambling game inspired by [Quibble Race](https://ufo50.miraheze.org/wiki/Quibble_Race) in the games collection UFO 50.

### Gobi

[Code](https://github.com/lee2sman/yabasic-games/blob/main/gobi.yab)

This is a desert travel survival adventure game, and the second time I've programmed this game. It is in the style of the game Oregon Trail. I programmed the first version of Gobi as a web-based game and now ported it to Basic. It was originally inspired by an unknown Shareware game that I had on a CD-Rom of hundreds of Mac games in the mid-90s, now lost to time and memory.

### Hamurabi

[Code](https://github.com/lee2sman/yabasic-games/blob/main/hamurabi.yab)

This is a light port of the original 1973 version of Hamurabi published in Basic Computer Games. Detailed notes at the end of this document. The source code for the original was published by David Ahl.

## Not Games

### Hunt

[Code](https://github.com/lee2sman/yabasic-games/blob/main/hunt.yab)

This is not a game but a lifting of the source code comments/remarks from Oregon Trail and then an attempt to write a modern version of the hunting simulation algorithm in Yabasic.

### Pig

[Code](https://github.com/lee2sman/yabasic-games/blob/main/pig.yab)

Not much of a game. This is an extremely simple simulation of the dice game Pig, for one player! The goal was to teach how to set up a recurring game loop.

### Pirate Name

[Code](https://github.com/lee2sman/yabasic-games/blob/main/piratename.yab)

Not a game! Pretty much a "Hello World" program to introduce Yabasic to an audience.

### Randos

[Code](https://github.com/lee2sman/yabasic-games/blob/main/randos.yab)

Also not a game. This demonstrates random number generation.

## References

* [Basic Computer Games](http://vintage-basic.net/games.html) by David Ahl
* [McCracken, Harry. “Fifty Years of BASIC, the Programming Language That Made Computers Personal.” TIME, 29 Apr. 2014, https://time.com/69316/basic/.](https://time.com/69316/basic/)
* [Birth of Basic. Directed by Mike Murray and Dan Rockmore, Dartmouth](https://www.youtube.com/watch?v=WYPNjSoDrqw)
* [People’s Computer Company. What to Do After You Hit Return (1975). 1975. Internet Archive, http://archive.org/details/Whattodoafteryouhitreturn.](https://archive.org/details/Whattodoafteryouhitreturn/mode/2up)
* [“Star Trader.” Wikipedia, 16 Feb. 2025. Wikipedia, https://en.wikipedia.org/w/index.php?title=Star_Trader&oldid=1275966462.](https://en.wikipedia.org/wiki/Star_Trader)
* [Porting 47 Year Old Basic code from The Oregon Trail](https://leetusman.com/nosebook/oregon-comments)
* [Explorations in TinyBasic](https://leetusman.com/nosebook/tiny-basic)

## Notes on Hamurabi in 2025: 57 years and growing

King of Sumeria or The Sumer Game was originally written by Doug Dyment in the Focal language for DEC computers in 1968. 

> The game consists of ten rounds wherein the player, as the ancient Babylonian king Hammurabi, manages how much of their grain to spend on crops for the next round, feeding their people, and purchasing additional land, while dealing with random variations in crop yields and plagues. The Sumer Game was inspired by The Sumerian Game, a much more in-depth text-based economic simulation intended for children, developed from 1964 to 1966 by designer and elementary school teacher Mabel Addis and IBM programmer William McKay. 

Around 1971 David Ahl ported the game to DEC BASIC, and then published it in his classic type-in program book 101 BASIC COMPUTER GAMES in 1973 and in expanded form in Microsoft BASIC in 1978 for BASIC Computer Games.

## Translating Hamurabi between BASIC implementations

I was able to translate Hamurabi from its original code in BASIC Computer Games to Yabasic with only minor changes needed. 

These were:

* I added more spacing for better formatting in the print around variables in PRINT lines with concatenation, and changed all semicolon separators to commas.
* Any line with a conditional and implied goto jump needed an explicit `GOTO` and `ENDIF` functions added. For example: `if L<7 THEN 565' needed to be changed to `IF L<7 THEN GOTO 565 ENDIF` in Yabasic.
* `RND(1)` is translated to `ran()` in Yabasic.
* After some tests with various BASIC emulators I believe `PRINT CHR$(7)` produces a bell sound, so I translated line 990 to `bell` in Yabasic, however I couldn't get this to produce sound on my computer.

