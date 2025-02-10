---
layout: post
title: Porting 47 year old BASIC code from The Oregon Trail 🥾🖳
categories: [open source, creative code, programming, permacomputing]
---

Today I am working with the original code from one of the original sources for The Oregon Trail when it started as a text-based game in BASIC, known as Oregon. [The Oregon Trail](https://github.com/clintmoyer/oregon-trail/blob/master/oregon.bas) game source code I'm working with is from 1978. I'm porting it to a modern BASIC variant [Yabasic](http://2484.de/yabasic/), which is over 25 years old itself, a free open source program, and works on a number of new and old Windows and Unix-based computers and Playstation 2. 

This work I'm doing is part of a project I've been engaged in recently and will be presenting at the Low Tech Electronics Faire at The Digital Scholars Studio at the Charles Library at Temple University next month. I am in the process of porting a number of these early kinds of economic simulation text-based strategy games like Hamurabi, Lemonade Stand and Drug Wars. My goal is to mine these sources as an example of still deeply-engaging play experiences, and to track their history, how source code was shared within a community of players and programmers, and how these games later came to influence games like M.U.L.E., Reigns, Democratic Socialism Simulator, and even parts of Final Fantasy, Sim City and Grand Theft Auto, among others. I have been deeply interested in the nascent concept and growing community of practice around [permacomputing](https://permacomputing.net/), reducing consumption, and looking at ways to minimize the impacts of computing on the environment. What greater way to resist the need for constant upgrades, powerful GPUs and junking "old" machines than to create, play and adapt command line text games in BASIC?

In recent years I participated in online conversations in [Critical Code Studies](https://criticalcodestudies.com/) as well. Playing with the code, reading the 47-year old comments, and trying to figure out the original program's functions and how to adapt them have been both play and a hands-on research and a thrilling but reasonable challenge. 

It's interesting to "read" the code (versus reading the text strategy game), and consider what they included in creating these economic simulations.

"Shooting" is an interesting case in point. What does shooting (or hunting) mean in the context of a command line game simulating the experience or story of The Oregon Trail? On the original trail of westward expansion, hunting was for food, survival. Reducing that experience to a simple typing of a challenge word within a set time clearly collapses that experience. But I can't think of an alternative currently, and as part of this research practice, I *go* with these choices made in 1978. Come to think of it, it's not too different than rolling the dice in a D&D game or the war simulations that earlier influenced those.

Back to The Oregon Trail. I began my porting work with some simple *translations*. First, I convert all semicolons, used in the original to separate text from variables in concatenated printed out code, to commas. Next I replace all *rnd()* instances with Yabasic's *ran()*. I considered creating a rnd() subroutine that simply calls ran() but went with the replacement instead. Finally, of all the hundreds of oneliner IF conditionals that jump to another line of code, I needed to explicitly call GOTO and end the line with ENDIF, which must not have been required in the 1978 MS BASIC.

With this, I try to run my port so far and the program runs. I walk through the intro, purchase my oxen and supplies, and I'm soon shuffling down the dusty trail. But I notice that strangers on the trail never seem to do me harm, and when I try to hunt, a crash.

In the shooting sub-routine there's a *CLK(0)* command that I couldn't find in the reference manuals that I read online. Either it's undocumented (unlikely), or the version of BASIC must not have been the standard MS BASIC I thought. CLK() I figure stands for clock time. I read the well-documented comments from 1978 from the programmer Bill Heinemann. It's incredible to read code comments written before I was born and then use those comments to help me fix the code to work today, 47 years later. 

Here's the first comments I reviewed:

```BASIC
6130 REM ***SHOOTING SUB-ROUTINE***
6131 REM THE METHOD OF TIMING THE SHOOTING (LINES 6210-6240)
6132 REM WILL VARY FROM SYSTEM TO SYSTEM.  FOR EXAMPLE, H-P
6133 REM USERS WILL PROBABLY PREFER TO USE THE 'ENTER' STATEMENT.
6134 REM IF TIMING ON THE USER'S SYSTEM IS HIGHLY SUSCEPTIBLE
6135 REM TO SYSTEM RMESPONSE TIME, THE FORMULA IN LINE 6240 CAN
6136 REM BE TAILORED TO ACCOMODATE THIS BY EITHER INCREASING
6137 REM OR DECREASING THE 'SHOOTING' TIME RECORDED BY THE SYSTEM
```

That's pretty helpful info. I then guessed before looking deeply that the program was looking for the user to press enter twice in a row and then checking how long that took and seeing if it was less than a certain amount of time. If so, successful shoot. Otherwise, a miss. But I looked again at the *DIM* array of words ("BANG","BLAM","POW","WHAM") and realized, NO, the user is being prompted to type in one of these randomly, and THEN the time is checked.

I looked back to the beginning of the program. Here's the original source code from 1978.

```BASIC
 710 PRINT "HOW GOOD A SHOT ARE YOU WITH YOUR RIFLE?"
 720 PRINT "  (1) ACE MARKSMAN,  (2) GOOD SHOT,  (3) FAIR TO MIDDLIN'"
 730 PRINT "         (4) NEED MORE PRACTICE,  (5) SHAKY KNEES"
 740 PRINT "ENTER ONE OF THE ABOVE -- THE BETTER YOU CLAIM YOU ARE, THE"
 750 PRINT "FASTER YOU'LL HAVE TO BE WITH YOUR GUN TO BE SUCCESSFUL."
 760 INPUT D9
 770 IF D9>5 THEN GOTO 790 ENDIF
 780 GOTO 810
 790 D9=0
```

So I take this to mean you can assign yourself 1 (best) to 5 (worse) or if you're a smart-aleck and type a number higher than 5 it seems they assign you the value 0 in line 790, which should be harder than ACE MARKSMAN, right? 

I want to use this self-assigned markmanship. Next I see:

```BASIC
6240 B1=((B1-B3)*3600)-(D9-1)
```

So I need to make my own version of this line. I don't see that in the original they actually check to make sure you're typing the correct word, so I added that in too. I also check that a player types the word within time, which I defined as 550 milliseconds times the self-selected shoot skill from the beginning (1 to 5, or 0 for smart-alecks, who will always fail). The 550 is a bit of a *magic number* (just as 3600 above is?) that came about from my own repeated practice to hit upon the right rate.

In the end, my *hunt* section takes more lines of code than the original, speaking to the brevity and a certain kind of elegance in the original. This parallels the experience of translating the famous BASIC 1-liner known as [10 Print](https://10print.org/), where porting  the original maze code takes many more lines when converting to Processing for example. In an attempt at making the game even more engaging, I add in a random timer to the beginning to add some difficulty, in the interests of gameplay, in addition to the aforementioned check for correct spelling. All porting, like all translation, isn't neutral, but still I consider how this deviates from the original programmer's work. I consider it to be inline with what may have been intended.

Here's the *basic* idea, with my own comments:

```BASIC
amt=round(ran(3))+1
REM wait some amount of time
sleep amt
start = peek("millisrunning")
6200 PRINT "TYPE ", S$(S6) REM Randomly selected word
input challenge$
print "POW!! "
REM Grab time at end
stop = peek("millisrunning")
REM if time is less than a second, success
if challenge$==S$(S6) THEN
  REM Word typed correctly
  REM It took stop-start millis
  REM To succeed, a player must do it in 550*D9 millis
    if start+(550*D9)>stop then
      print "A hit!"
    else
      print "A miss!"
    endif
  else
    Print "Misfire!" REM Typed incorrectly
endif
```

The ability to run *peek* to get *millisrunning* for total elapsed time in milliseconds was only added to Yabasic in Version 2.79.0, April 21, 2018. How does this impact my desire for creating a version of the program to work on computers both new and old? Will these more recent versions of Yabasic that take advantage of millisrunning work on older computers, say from 20 years ago for example? If not, do I create a simpler version of this program that only makes use of the more limited *time$* variable, and how will that impact the gameplay? I have to make some decision, so decide to use millisrunning and document it here at the least.

I'm still not 100% finished porting Oregon, but this section just on porting Hunt I think exemplifies my working process and thoughts. I'll be publishing my code and more documentation of this research and games projects as I progress further.
