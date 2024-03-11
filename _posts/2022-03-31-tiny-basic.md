---
layout: post
title: Explorations in Tiny BASIC
categories: programming retrocomputing
---

![MS BASIC]({{"/images/basic-drawing.jpg" | absolute_url}})  

*2022-04-01 update: I've added a link to my full code for a player + computer opponent version of the PIG dice game to the end.*

*2022-04-06: added a link to a repo with code for my Tiny BASIC games. I have a better opponent AI now, though still quite primitive.*

Lately I've been getting into BASIC. I was a kid in the 80s and 90s and I remember those computers that would boot into a BASIC interpreter. I didn't have one of those but came in contact with one every year or two and played a handful of text games on them. I was aware of some of the commands and syntax, GOTO and the like, and I have looked through the classic BASIC Video Games book a number of times. The ecosystem of BASIC interested me but I hadn't delved too deeply. Recently I read about Tiny BASIC:

> Tiny BASIC is a family of dialects of the BASIC programming language that can fit into 4 or fewer KBs of memory. Tiny BASIC was designed in response to the open letter published by Bill Gates complaining about users pirating Altair BASIC, which sold for $150. Tiny BASIC was intended to be a completely free version of BASIC that would run on the same early microcomputers. --Wikipedia [1]

![BASIC on vinyl]({{"/images/basic-vinyl.jpg" | absolute_url}})  

So originally, Tiny BASIC was a specification, not an implementation. The People's Computer Company published a newsletter, almost like a photocopied zine to my eyes, with articles, tutorials, comix, all aimed at the nascent hobbyist computer community. They invited Dennis Allison from Stanford University's Computer Science faculty to write the spec.

> The magic of a good language is the ease with which a particular idea may be expressed. The assembly language of most microcomputers is very complex, very powerful, and very hard to learn. The Tiny BASIC project at PCC represents our attempt to give the hobbyist a more human-oriented language or notation with which to encode his programs. [2]

The newsletter goes on to describe the motivation for the project, a free implementation of the BASIC language, and the community working on it currently. It specifies what the language could entail, how to solve various problems, a discussion on creating a compiler versus an interpreter, what it will take to build one's own Tiny BASIC, and a request for feedback and ideas. It also contained some simple BASIC games.


![Copyleft All Rights Wronged]({{"/images/basic-wrongs.jpg" | absolute_url}})  

### All Rights Wronged

One of the earlier implementations was Dr. Li-Chen Wang's Palo Alto Tiny BASIC, where he may have devised the term copyleft to describe this process of source code being openly shared and modified and re-published. He affixed the notice "COPYLEFT ALL RIGHTS WRONGED" when he published it in 1976. 

BASIC flourished as a language throughout the 80s and into the 90s. Many versions of BASIC proliferated, and many versions of Tiny BASIC as well, including some that grew into more extended versions, sometimes including the ability to create graphics or sound, rather than just ASCII text. 

In fact, the inital Tiny BASIC implementations allowed printing text output but couldn't receive text string inputs. These were very simple implementations of BASIC as it had to work with low memory usage. They allowed for (integer) variables, subroutines via gosub/return, if-statements (though not if-then or if-then-else), numerical though not char/string input, and not much else!

The allowed statements were:

```
IF - THEN statement
GOTO #
INPUT var 
LET var=expression
GOSUB #
RETURN
CLEAR
LIST
RUN
END
```

Strings weren't defined in the notes, nor were "remarks" aka comments. Missing also were for-loops, random number generation, arrays, though some of the Tiny BASIC dialects did add these. 

I decided to try my hand at making a simple dice gambling game. Where I grew up Threelo was a popular dice game, and my friends had our own house rules. But to warm up, I first implemented Pig, a good first game to program due to its minimal actions and easiness of programming. Essentially, each turn you roll a die and add the total to your points. You can stop at any time and keep that total, or keep rolling. If you ever roll a 1 you lose all the points you accrued. That's it! Pretty ....(wait for it).... basic.

I downloaded Damian Gareth Walker's Tiny BASIC Interpreter and Compiler project written in C. [3] 

It packages a man page and some example games (Hunt the Wumpus, Tic Tac Toe, and some others).

Without a built-in random number generator, how was I going to create a random die roll? 

Luckily, Gareth published some instructions to construct a minimal not-very-sophisticated random number generator. [4] We don't have the privilege of referencing the clock of the computer for example, so we follow early BASIC tradition and ask the user for a seed number, then perform a simple calculation. Some other implementations of Tiny BASIC came with a random number generator. Gareth's doesn't by default but does add in the ability to use REM (remark) for commenting. 

![Tiny BASIC in Cool Retro Term]({{"/images/lemonade.jpg" | absolute_url}})  
*lemonade.bas running on Tiny BASIC in CoolRetroTerm*  

### PIG 

So here's my small and not terribly fun or sophisticated game of Pig. No doubt many improvements can be made. 

```
    REM --- PIG Dice game test
    REM --- Created: 2022-03-30
    REM --- Created for cyningstan's Tiny BASIC 
    REM --- No one will want to use this code, but consider it public domain CC0.

    REM --- Variable List
    REM
    REM R - A random number returned by the Random Number Generator
    REM D - Current die roll
    REM T - TOTAL SAVED
    LET T=0

    REM --- Initialise the random number seed
10  PRINT "Enter a number:"
    INPUT R
   
    REM --- MAIN GAME LOOP
20  PRINT "YOUR CURRENT TOTAL IS ",T
    PRINT "Would you like to roll? (0 no, 1 yes)"
    INPUT Q

30  IF Q=0 THEN GOTO 300
   
    REM --- CHECK IF BUSTED
    GOSUB 200 
    LET D=1+R-R/6*6
    PRINT "YOU ROLLED ",D
    IF D=1 THEN GOTO 50
    LET T=T+D
    GOTO 20

    REM --- BUSTED!
50  PRINT "BUSTED!"
    LET T=0
    GOTO 20

200 LET R=5*R+35
    LET R=R-R/6547*6547
    RETURN

300 PRINT "YOUR SCORE IS ",T
    PRINT "GOODBYE"
```

UPDATE: I've added a link to a 2 player version (player + computer opponent) I made of Pig dice to the links at the end. Source code license: COPYLEFT ALL RIGHTS WRONGED, natch. There are likely errors as this is the first time I'm programming in any BASIC, and I made this in less than an hour, and sure enough, I was making spaghetti GOTO code! But you are welcome to improve or build upon this in any way you like.

From here, it would be relatively easy to create some version of Blackjack with a little bit more effort. Of course, it would also be fun to make text adventures, pizza-ordering calculators, the classic text game Lemonade Stand, or a version of my favorite BASIC game TI-83 calculator version of Drug Wars/Dope Wars (that's a story for a different time). To play the game you'll need to download Tiny BASIC. Save the program with a .bas extension. The computer opponent sorely needs better AI than what I've implemented.

There's a procedurally-generated maze / dungeon adventure game, like a simplified text RPG, called Kingdom of the Lyre that was made for and entered into PROCJAM in 2019. [5] I played it. It's challenging and I thought it was fun. I'd love to have a Tiny BASIC game jam one day.

To wrap up, I'll leave you with this WANTED ad from Volume 1, Number 1 of Dr. Dobb's in the section on My, How Tiny BASIC Growed, 

> WANTED: Entirely new, never before seen, Tiny Languages, imported from another planet or invented here on Earth. Especially languages for kids using home computers that talk to tvs or play music or run model trains or...

## Links

[Wikipedia article on TinyBASIC](https://en.wikipedia.org/wiki/Tiny_BASIC)  
Dr. Dobb's Journal of Computer Calisthenics and Orthodontia, January, 1976 - [PDF](http://cini.classiccmp.org/pdf/DrDobbs/DrDobbs-1976-01-v1n1.pdf)  
[Tiny BASIC Interpreter and Compiler Portal](http://tinybasic.cyningstan.org.uk/)  
[Minimal random number generator for Tiny BASIC](http://tinybasic.cyningstan.org.uk/download/10/random-number-generator)  
[Kingdom of the Lyre game](http://tinybasic.cyningstan.org.uk/download/44/kingdom-of-the-lyre)  
[Tom Pittman's Tiny BASIC User Manual](http://www.ittybittycomputers.com/IttyBitty/TinyBasic/TBuserMan.htm)  
my [Tiny BASIC games repo](https://tildegit.org/exquisitecorp/tinybasic-programs) with a better computer opponent for PIG dice game  

