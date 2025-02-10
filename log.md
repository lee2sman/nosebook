---
layout: default
title: Log
permalink: /log/
---

# Log

*This is a page for ongoing tiny updates on my projects and research, including technical notes, code, and screenshots of work in progress.*

## 2025-02-09

I studied the Oregon Trail source code (1978) a bit because I couldn't get the shooting sub-routine section to work correctly. There's a *CLK(0)* command that I couldn't find in the Microsoft Basic reference manuals from 1980 that I read online. I must be running a different BASIC? I figure it stands for clock time. So I read the comments. Thank G-d for comments from 1978 from the programmer! It's incredible to read code comments written before I was born and then use those comments to help me fix the code to work today, 47 years later. I can't recall experiencing anything like that before.

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

Okay, that was helpful info. Next I first thought that the program was looking for the user to press enter twice in a row and then checking how long that took and seeing if it was less than a certain amount of time. If so, successful shoot. Otherwise, a miss. Then I looked again at the DIM array of words ("BANG","BLAM","POW","WHAM") and realized, NO, the user is being prompted to type in one of these randomly, and THEN the time is checked.

THEN, I remembered back to the beginning of the program. Here's the original source code from 1978.

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

So I need to make my own version of this line. Incidentally, I didn't see that they actually check to make sure you're typing the correct word, so I added that in too. In the end, mine takes many more lines of code than the original.

```BASIC
clear screen
amt=round(ran(3))+1
REM wait some amount of time
sleep amt
start = peek("millisrunning")
6200 PRINT "TYPE ", S$(S6)
input challenge$
print "POW!! "
REM Grab time at end
stop = peek("millisrunning")
REM if time is less than a second, success
if challenge$==S$(S6) THEN
  PRINT "Word typed correctly"
  PRINT "It took you ", stop-start, " millis"
  PRINT "To succeed, you must do it in ",550*D9," millis"
    if start+(550*D9)>stop then
      print "A hit!"
    else
      print "A miss!"
    endif
  else
    Print "Misfire! (Typed incorrectly)"
endif```

I ended up writing a number of lines of code, but in the end, my program works pretty well I think. It checks that you type the correct word, and that you did it within time, which I defined as 550 milliseconds times the self-selected shoot skill from the beginning (1 to 5, or 0 for smart-alecks, who will always fail). The 550 is a bit of a *magic number* that came about from my own repeated practice to hit upon the right rate.

## 2025-02-08

I did some work to prepare for my workshop for LOW TECH at Temple University next month. I started by porting the Hamurabi game to Yabasic, which I had saved in a [GitHub repo of BASIC games](https://github.com/lee2sman/BasicGames/) over a decade ago! Porting was straightforward and I wrote some notes on my process. I didn't try to translate GOTOs to subprogram (functions) for example. Mostly I needed to alter conditionals to explicitly have *GOTO* statements and end with *endif*. I also switched out RND() for RAN() and formatted text. It worked! Incredible. I'm still really bad at the game. And studying the code doesn't mean I've learned how to get better. The code is from 1978, and the game is even older, so it's really cool to be working with the same code from almost 50 years ago. I wrote up my process and some links to learn more to include in my workshop materials. Next I came across [The Oregon Trail](https://github.com/clintmoyer/oregon-trail) source code and took a look. It contains both the original code as well as some other refactors. With some of my own refactoring for Yabasic I got the main functionality working except for hunting, and some other things (bandits never seemed to attack). It's been fun working on this so far. I haven't placed any of the code or notes online yet but will do so when I get farther along.

## 2025-02-07

Added the [pages](https://leetusman.com/pages/) page to my website, which links to lots of things that were previously harder to find, such as tutorials, my links page, this log, and my more public software projects and class websites. I also added a direct link in the navbar, but wasn't sure at first what to call it. I ended up going with *+*, implying, click here on the plus sign to see more. Hopefully that works. I did some css cleanup on the jekyll blog and cleaned up the links page a bit, though I hope to grow it further.

## 2025-02-06

I updated my Pomodoro Timer for Pico-8. I tweaked the UI and added the ability to change timer length. For Pico-8 owners you can find it in *splore*, or anyone can run it via the [embedded web player](https://www.lexaloffle.com/bbs/?tid=144025). It should also be easy to get it working on Picotron.

![Short looping animation gif of Pomodoro Timer for Pico-8](https://www.lexaloffle.com/media/51769/5_pomodoro_0.gif)  

I had a proposal accepted to the low-tech electronics faire conference in March. I'm going to teach a workshop in making oldschool video games using BASIC. Specifically, I proposed to teach a video game workshop with [Yabasic](https://2484.de/yabasic/), since it works on both old and new computers, and has some modern programming conveniences (subroutines, graphics commands). Inspired by ideas of permacomputation, minimalism in digital humanities, retro-computing, and *platform studies*, I think BASIC will allow us to explore these concepts in a hands-on, engaging way. I started by looking for the source code for Hamurabi, Star Trader, Drug Wars and Lemonade Stand. There's also my game [Gobi](https://notapipe.itch.io/gobi) (an Oregon Trail-like), not to mention modern economic sims like M.U.L.E., Reigns, Democratic Socialism Simulator, and many others. I want to create some starter code that folks can use in a workshop. To practice with Yabasic I made a simple version of Twenty-one, Pig dice game (I previously coded one in Tiny Basic), a basic Hello World window, and a random dice roller. 

## 2025-02-03

Minor fixes to [Daily quilt poem](https://leetusman.com/everyday/293/), separating out the html, css and lua script to separate files. I also improved the css so it looks better on mobile. One fun note: I am using the *noscript* tag, used to convey a message to a visitor to a site that they are unable to see the full working site without javascript. In what may be a first, I let the reader know the site requires javascript to render the Lua script, or alternately, they can read quilt poems as a book.

![noscript message on Daily quilt poem]({{"/images/log/noscript.png" | absolute_url}})  
*Message to users not running Javascript in their browser. I'm testing this on the [Dillo browser](https://dillo-browser.github.io/25-years/index.html), one of my favorite minimalist browsers, and also no-Javascript.*  

## 2025-02-02

I cleaned up organization and published some of the demo projects to my [everyday](https://leetusman.com/everyday) mini-site, which is really a back-of-house place for me to do experiments, daily coding sketches and the like. I added some projects testing an experimental [pseudo-radio player](https://leetusman.com/everyday/291/) for a residency this summer, a tribute to the earliest incarnation's of Harold Cohen's self-drawing AARON program that I viewed at the exhibit at the Whitney last year, the [LoremSoft](https://leetusman.com/everyday/294/) generative lorem ipsum shareware page. 

I found the remnants of an earlier test I had tried in using [Fengari library](https://github.com/fengari-lua/fengari-web) to run Lua code in a website's frontend code (implemented in Javascript). I was on an Amtrak train back to NYC and started by writing a minimal demo example to interact with the DOM.

```
<!-- minimal example using Lua to control the DOM -->
<body>
<div id="demo">
  Starting text
</div>
<script src="fengari-web.js" type="text/javascript" async></script>
<script type="application/lua" async>

	local js = require "js"
	local window = js.global
	local document = window.document
	demo=document:getElementById("demo")
	demo.innerText="I've changed it!"
</script>
</body>
```

Next step: I wanted to build a quilt-poem-a-day generator as a prototype. I've not exhausted my ideas on the quilt-poems yet evidently! I adapted my code from my previous Lua-based quilt poems generator, and SUCCESS, it worked! I really enjoyed using Lua in the browser. Next steps were to add some minimal CSS, import a wordlist, change to monospace font, keep spaces because javascript will try to strip them out, implement daily seeding. All that I accomplished with another hour of work, so this was a pretty rapid project. I added in a single list of minimal words to start and got a smolweb style theme going with shades of blue. I'm not sure if I'll keep adding to this daily quilt poem project here or leave it as is for now, but I [published](https://leetusman.com/everyday/293/) this version in the browser within my everyday daily code sketches section of my website, so you can return and visit every day if you like.

![Daily Quilt Poem 2025-02-03]({{"/images/log/daily-quilt-poem.png" | absolute_url}})  
*The inaugural [daily quilt poem](https://leetusman.com/everyday/293/).*

## 2025-02-01

Had an idea to make the quilt poems even smaller. I thought it would be complicated but the implementation was trivial. Rather than a single variable to hold the max width of words in a quilt I have a table (array) of 8 values: one for each column. The previous time I cycled through each individual word checking for its width, so now I compare each word's width to the current max width for its column and simply replace it if it's longer. These 8 max column width values are then used to pad out with blank space when writing a quilt poem as output. So this means that each column could be a different width rather than all standardized. Visually, I think it looks better, and it will better fit when I try to do printing for a chapbook.

So next I worked on mocking up a chapbook. I asked for some suggestions on fedi and did some searching of my own. I ended up generating a lot of quilt poems, then selecting favorites and adding them to a document in LibreOffice. I copied my previous NaNoGenMo layout and added in a colophon page, the code and quilt library before the selected poems. I found [Zine Arranger](https://nashhigh.itch.io/zinearranger), a really wonderful web-based layout tool that resizes a source PDF to new dimensions, and used it to create a half fold zine. I also selected a public domain image of an old quilt from the 1800s to be the cover image. I printed off a sample at home and it looks good. Next time will be to print an edition, bind them (I have my long-arm zine stapler), and then distribute. Will try to do it as a riso zine.

Found this online [riso print simulator with ink shift](https://risottostudio.com/pages/print-simulator-ink-shift) tool (reminds me of the [Experimental Archive Space](https://www.experimentalarchive.space/) zine maker that Caleb and I designed - maybe same or similar library under the hood?). Mocked up cover and a sheet.

![Mockup of a riso-printed cover]({{"/images/log/riso-cover-mock.png" | absolute_url}})  

![Mockup of a riso-printed sheet page]({{"/images/log/quiltpoems-riso-mock.png" | absolute_url}})  

## 2025-01-31

Updated the [quiltpoems](https://github.com/lee2sman/generative-quilt-poems) algorithm to make better visual output. The previous algorithm I wrote scans through every *possible* word "patch" selected for a quilt and finds the maximum word length. Now, I've changed it to only scan through the *actual* used words in each quilt. This theoretically means a performance drop (e.g. "more expensive") since I'm checking 64 times for each quilt instead of the previous 8 times (so 8 times slower) but in practical purposes the total rendering out of 700 visual quilt poems was still less than a second, and that's more than fine. The point of this change was so the columns of a quilt would get smaller, particularly for Amish bars-style quilts. I thought about whether I wanted to change column size for any column with only shorter words in it (such as happens in a Cross Bars quilt) but decided to keep columns consistent for now. The change I've made improves the visual quality on screen and should also make it easier to include more quilts at larger text size in a half-fold printed chapbook/zine, which is one of the things I'd like to do next with this project.

Two examples from today:

```
Mess Juice Big Quarters Quilt 

 mess  mess juice juice  mess  mess juice juice 
 mess  mess juice juice  mess  mess juice juice 
juice juice  mess  mess juice juice  mess  mess 
juice juice  mess  mess juice juice  mess  mess 
 mess  mess juice juice  mess  mess juice juice 
 mess  mess juice juice  mess  mess juice juice 
juice juice  mess  mess juice juice  mess  mess 
juice juice  mess  mess juice juice  mess  mess 
```

And another, as a pic:

![Lobby Leery Drunkard's Path Quilt]({{"/images/log/lobby-leery.png" | absolute_url}})  

## 2025-01-24

Updated documentation for [panblog](https://tildegit.org/exquisitecorp/panblog).

[Bookmobile](https://tildegit.org/exquisitecorp/bookmobile) is a command line program for saving articles from the internet, that I originally wrote four years ago, as an alternative to Pocket or Wallabag or *Save as...*. Bookmobile downloads articles, scrape off the ads, sidebars, navigation bars, and any other extraneous junk. Then it saves the article as an epub for ebook readers, or as plain cleaned up html, or a new html file with a CSS theme, or just as plain markdown text. Tonight I worked on the backend of the program, removing the npm/node.js dependency and replacing it with rdrview. While many folks do use node.js/npm, I certainly don't want to require it, and rdrview is a C program with equivalent functionality. I also cleaned up some of the bookmobile code with proper pandoc titling, the filenaming system, and updated the README documentation. 

## 2025-01-21

Procrastinated on some school prep by creating my own [Lorem Ipsum](https://leetusman.com/lorem/) "shareware description" generator. Then procrastinated even further by writing out a [Website Tracery tutorial](https://leetusman.com/nosebook/tracery) since I couldn't find any basic tutorials  on how to integrate Tracery into a website and got stymied until I figured out it required jquery as a dependency! Now I've come full circle, and the tutorial will be useful in my classes! :)

## 2025-01-18

Published initial version of my class website for [Creating User Interfaces](https://leetusman.com/cui_spring2025/), built with my panblog static site builder. I came across the [Reasonable Colors](https://www.reasonable.work/colors/) system for creating accessible color palletes and tried it for the first time to ensure I had met minimum color contrast ratios.

I tried out the latest v1.2 version of [Lichen-Markdown](https://codeberg.org/ukrudt.net/lichen-markdown) by @abekonge, @soapdog, and @notplants, a fork of the original Lichen by @sensorstation. I had previously suggested they build in locally-running php-only support, and tried out this new feature. It's a big improvement since you can then just publish static pages afterwards. I sent some suggestions on additional beginner-friendly improvements: wysywig buttons for adding the main markdown things (headings, links, code, images), and a suggested fix for adding image titles with spaces in the name.

## 2025-01-17

Added a mini fish script to complement adding simple entries directly to [CAROUSEL](https://partytimehexcellent.itch.io/carousel) (by Rachel Simone Weil) notetaking program without having to launch DOSBOX.

```fish
#!/usr/bin/env fish
#place in /usr/local/bin

set filename (date +%Y%m%d).MD
nvim ~/dosprogs/CAROUSEL/ENTRIES/JOURNAL/$filename
```

The site I built for Sara and Michael's exhibit is [online now](https://isthereanaftertasteoflifeinthesegraves.com/). Its full title is *Is there an after-taste of life in these graves? And in the flowers’ mouths do bees find the hint of a word refusing speech? O flowers, prisoners of our instincts toward happiness, do you return to us with our dead in your veins? Flowers, how can you escape our grip? How can you not be our flowers? Does the rose really use all its petals to fly away from us? Does it want to be only a rose, nothing but a rose? No one’s sleep beneath so many eyelids?*


![Screenshot of the Is There an Aftertaste of Life... 24 hour animation website at 14:15:32]({{"/images/log/flower-clock.jpg" | absolute_url}})  

The site works like a 24 hour film. I programmed it to run like an extremely slow flipbook animation. Here's a screenshot of the site at the moment about halfway through the minute at 2:13pm. Due to the fires in LA the exhibit opening was postponed and now is going to open this coming saturday at Timeshare gallery.

## 2025-01-16

Published online the first pages of the Drawing, Moving and Seeing with Code [class site](https://leetusman.com/dmsc_spring2025/), built with my [Panblog](https://tildegit.org/exquisitecorp/panblog) static site generator that I created in December. It's really easy to use, and to publish with GitHub pages from a docs directory is simple. I also programmed a little fun wandering bee for the landing page using the DOM function calls (formerly p5dom) in not many lines of p5.js code, using perlin noise. I tested the site on Firefox, Falkon, Dillo, Netsurf, and w3m. 

![Drawing, Moving and Seeing with Code screenshot WIP]({{"/images/log/dmsc.jpg" | absolute_url}})  
*Screenshot of initial build of Drawing, Moving and Seeing with Code website. This is a still, the bee is animated through p5.js.*

Last month I built a web-based artwork in the form of a 24-hour movie/animation presented on a custom website. This was work-for-hire for artist friends as part of an exhibit of their work opening at a gallery in LA this month. Today it was deployed and I tested on several browsers and phone.

## 2025-01-15

I'm back in NYC. The past few days I did some course prep for my course Drawing, Moving and Seeing with Code. I'm excited for the class. On my laptop I installed [Moby](https://www.moby-thesaurus.org/) open source thesaurus and created a simple command line function alias.

## 2025-01-12

Yesterday Yuehao and I visited MOLAA the Museum of Latin American Art and saw [ARTEÔNICA: Art, Science, and Technology in Latin America Today](https://molaa.org/2024-arteonica), which I had been recommended to see by Katherine Moriwaki and Jonah Brucker-Cohen only last week. I'm so thankful for the recommendation as this was an incredible survey exhibition of work from decades past to today. This is a well-curated exhibition, directed by Gabriala Urtiaga. I loved many of the works and took lots of photos and notes. I'm going to include teaching about these artists in my Drawing, Moving and Seeing with Code course next semester.

I spent time researching a number of the artists from the show. [Francesco Mariotti](https://www.mariotti.ch/en) has a great website documenting his portfolio of works over the years since 1964! I downloaded photos and a PDF from his website on [Chullachaqui](https://www.mariotti.ch/en/bibliography/1984/chullachaqui-5/) Intelligencia Artifical, a series of "AI" projects influenced by Tristan Tzara's dada experiments to modern software arts. He worked with programmers who wrote software in BASIC on the Commodore64 to produce audio and text animals for performances and interactive installations over many years. There was an interview in the PDF and [I used Google Translate to translate to English](https://archive.org/details/inteligencia-artificial-chullachaqui). 

I am still in LA. Two flights on two separate days already cancelled on me! Hoping I can fly home tonight.

## 2025-01-09

Studio visit with Yuehao Jiang and Matt Doyle. We showed each other our recent projects. Yuehao gave some great feedback on my interview art piece currently titled *Hyphenated*. One suggestion was to simplify the background to make the speakers the focus, and to add subtitles. I tried out a 'basic primitives' version and a wilder one in my typical style. Still need to add the subtitles and some other improvements when I'm back in NYC.

![two basic 3d model heads made out of primitive shapes are facing each other. Their skin and feature textures are glitchy drawings and the background is also a big glitch image of many colors]({{"/images/log/heads-wild.jpg" | absolute_url}})

## 2025-01-08

Added a page on Lua to my [Programming Notes](https://leetusman.com/notes/programming/) page. I also started working on building a basic theme template system for the note pages.

I continued work on my Forth-like language.

## 2025-01-05

I'm kicking off this tinylog today. I'm not 100% sure I'll stick with it, but I enjoyed participating in the [December Adventure](https://leetusman.com/december-adventure-2024/) last month and thought I should have a spot to plop down further thoughts as I build projects or do research or what-have-you. I think anything that isn't quite a blog post or a project page could go here.

The past couple days I've been reviewing NTTP's tutorial [More About Tiny Scripting Languages](https://notimetoplay.org/engines/more-scripting.html) and trying to wade into continuing work on my 3th (Forth language). I am having trouble implementing nesting and delimiters.

I went back into the ExquisiteCorp site I prototyped for my music website, but I'm still not sure what domain to register for it and whether the graphics I mocked up really fit with the kind of music I'm making.

![mockup of ExquisiteCorp website? - phone size screenshot of a website with title exquisitecorp followed by a 2column grid of 'fried' images]({{"/images/excorp-mockup.jpg" | absolute_url}})

Hmmm. Not sure that works. In any case, I've been recording music lately and need a place to plop it!

