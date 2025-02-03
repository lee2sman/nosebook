---
layout: default
title: Log
permalink: /log/
---

# Log

*This is a page for ongoing tiny updates on my projects and research.*

## 2024-02-02

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

## 2024-02-01

Had an idea to make the quilt poems even smaller. I thought it would be complicated but the implementation was trivial. Rather than a single variable to hold the max width of words in a quilt I have a table (array) of 8 values: one for each column. The previous time I cycled through each individual word checking for its width, so now I compare each word's width to the current max width for its column and simply replace it if it's longer. These 8 max column width values are then used to pad out with blank space when writing a quilt poem as output. So this means that each column could be a different width rather than all standardized. Visually, I think it looks better, and it will better fit when I try to do printing for a chapbook.

So next I worked on mocking up a chapbook. I asked for some suggestions on fedi and did some searching of my own. I ended up generating a lot of quilt poems, then selecting favorites and adding them to a document in LibreOffice. I copied my previous NaNoGenMo layout and added in a colophon page, the code and quilt library before the selected poems. I found [Zine Arranger](https://nashhigh.itch.io/zinearranger), a really wonderful web-based layout tool that resizes a source PDF to new dimensions, and used it to create a half fold zine. I also selected a public domain image of an old quilt from the 1800s to be the cover image. I printed off a sample at home and it looks good. Next time will be to print an edition, bind them (I have my long-arm zine stapler), and then distribute. Will try to do it as a riso zine.

Found this online [riso print simulator with ink shift](https://risottostudio.com/pages/print-simulator-ink-shift) tool (reminds me of the [Experimental Archive Space](https://www.experimentalarchive.space/) zine maker that Caleb and I designed - maybe same or similar library under the hood?). Mocked up cover and a sheet.

![Mockup of a riso-printed cover]({{"/images/log/riso-cover-mock.png" | absolute_url}})  

![Mockup of a riso-printed sheet page]({{"/images/log/quiltpoems-riso-mock.png" | absolute_url}})  

## 2024-01-31

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

## 2024-01-24

Updated documentation for [panblog](https://tildegit.org/exquisitecorp/panblog).

[Bookmobile](https://tildegit.org/exquisitecorp/bookmobile) is a command line program for saving articles from the internet, that I originally wrote four years ago, as an alternative to Pocket or Wallabag or *Save as...*. Bookmobile downloads articles, scrape off the ads, sidebars, navigation bars, and any other extraneous junk. Then it saves the article as an epub for ebook readers, or as plain cleaned up html, or a new html file with a CSS theme, or just as plain markdown text. Tonight I worked on the backend of the program, removing the npm/node.js dependency and replacing it with rdrview. While many folks do use node.js/npm, I certainly don't want to require it, and rdrview is a C program with equivalent functionality. I also cleaned up some of the bookmobile code with proper pandoc titling, the filenaming system, and updated the README documentation. 

## 2024-01-21

Procrastinated on some school prep by creating my own [Lorem Ipsum](https://leetusman.com/lorem/) "shareware description" generator. Then procrastinated even further by writing out a [Website Tracery tutorial](https://leetusman.com/nosebook/tracery) since I couldn't find any basic tutorials  on how to integrate Tracery into a website and got stymied until I figured out it required jquery as a dependency! Now I've come full circle, and the tutorial will be useful in my classes! :)

## 2024-01-18

Published initial version of my class website for [Creating User Interfaces](https://leetusman.com/cui_spring2025/), built with my panblog static site builder. I came across the [Reasonable Colors](https://www.reasonable.work/colors/) system for creating accessible color palletes and tried it for the first time to ensure I had met minimum color contrast ratios.

I tried out the latest v1.2 version of [Lichen-Markdown](https://codeberg.org/ukrudt.net/lichen-markdown) by @abekonge, @soapdog, and @notplants, a fork of the original Lichen by @sensorstation. I had previously suggested they build in locally-running php-only support, and tried out this new feature. It's a big improvement since you can then just publish static pages afterwards. I sent some suggestions on additional beginner-friendly improvements: wysywig buttons for adding the main markdown things (headings, links, code, images), and a suggested fix for adding image titles with spaces in the name.

## 2024-01-17

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

## 2024-01-16

Published online the first pages of the Drawing, Moving and Seeing with Code [class site](https://leetusman.com/dmsc_spring2025/), built with my [Panblog](https://tildegit.org/exquisitecorp/panblog) static site generator that I created in December. It's really easy to use, and to publish with GitHub pages from a docs directory is simple. I also programmed a little fun wandering bee for the landing page using the DOM function calls (formerly p5dom) in not many lines of p5.js code, using perlin noise. I tested the site on Firefox, Falkon, Dillo, Netsurf, and w3m. 

![Drawing, Moving and Seeing with Code screenshot WIP]({{"/images/log/dmsc.jpg" | absolute_url}})  
*Screenshot of initial build of Drawing, Moving and Seeing with Code website. This is a still, the bee is animated through p5.js.*

Last month I built a web-based artwork in the form of a 24-hour movie/animation presented on a custom website. This was work-for-hire for artist friends as part of an exhibit of their work opening at a gallery in LA this month. Today it was deployed and I tested on several browsers and phone.

## 2024-01-15

I'm back in NYC. The past few days I did some course prep for my course Drawing, Moving and Seeing with Code. I'm excited for the class. On my laptop I installed [Moby](https://www.moby-thesaurus.org/) open source thesaurus and created a simple command line function alias.

## 2024-01-12

Yesterday Yuehao and I visited MOLAA the Museum of Latin American Art and saw [ARTEÔNICA: Art, Science, and Technology in Latin America Today](https://molaa.org/2024-arteonica), which I had been recommended to see by Katherine Moriwaki and Jonah Brucker-Cohen only last week. I'm so thankful for the recommendation as this was an incredible survey exhibition of work from decades past to today. This is a well-curated exhibition, directed by Gabriala Urtiaga. I loved many of the works and took lots of photos and notes. I'm going to include teaching about these artists in my Drawing, Moving and Seeing with Code course next semester.

I spent time researching a number of the artists from the show. [Francesco Mariotti](https://www.mariotti.ch/en) has a great website documenting his portfolio of works over the years since 1964! I downloaded photos and a PDF from his website on [Chullachaqui](https://www.mariotti.ch/en/bibliography/1984/chullachaqui-5/) Intelligencia Artifical, a series of "AI" projects influenced by Tristan Tzara's dada experiments to modern software arts. He worked with programmers who wrote software in BASIC on the Commodore64 to produce audio and text animals for performances and interactive installations over many years. There was an interview in the PDF and [I used Google Translate to translate to English](https://archive.org/details/inteligencia-artificial-chullachaqui). 

I am still in LA. Two flights on two separate days already cancelled on me! Hoping I can fly home tonight.

## 2024-01-09

Studio visit with Yuehao Jiang and Matt Doyle. We showed each other our recent projects. Yuehao gave some great feedback on my interview art piece currently titled *Hyphenated*. One suggestion was to simplify the background to make the speakers the focus, and to add subtitles. I tried out a 'basic primitives' version and a wilder one in my typical style. Still need to add the subtitles and some other improvements when I'm back in NYC.

![two basic 3d model heads made out of primitive shapes are facing each other. Their skin and feature textures are glitchy drawings and the background is also a big glitch image of many colors]({{"/images/log/heads-wild.jpg" | absolute_url}})

## 2024-01-08

Added a page on Lua to my [Programming Notes](https://leetusman.com/notes/programming/) page. I also started working on building a basic theme template system for the note pages.

I continued work on my Forth-like language.

## 2024-01-05

I'm kicking off this tinylog today. I'm not 100% sure I'll stick with it, but I enjoyed participating in the [December Adventure](https://leetusman.com/december-adventure-2024/) last month and thought I should have a spot to plop down further thoughts as I build projects or do research or what-have-you. I think anything that isn't quite a blog post or a project page could go here.

The past couple days I've been reviewing NTTP's tutorial [More About Tiny Scripting Languages](https://notimetoplay.org/engines/more-scripting.html) and trying to wade into continuing work on my 3th (Forth language). I am having trouble implementing nesting and delimiters.

I went back into the ExquisiteCorp site I prototyped for my music website, but I'm still not sure what domain to register for it and whether the graphics I mocked up really fit with the kind of music I'm making.

![mockup of ExquisiteCorp website? - phone size screenshot of a website with title exquisitecorp followed by a 2column grid of 'fried' images]({{"/images/excorp-mockup.jpg" | absolute_url}})

Hmmm. Not sure that works. In any case, I've been recording music lately and need a place to plop it!


