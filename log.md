---
title: Log
permalink: /log/
date: 2025-08-13  # Update this when you modify
layout: default
feed: true 
---

# Log

*This is a page for ongoing tiny updates on my projects and research, including technical notes, code, and screenshots of work in progress. You can [subscribe to the RSS feed](https://leetusman.com/nosebook/feed.xml).*

<a id="december-adventure-2025"></a>

## 2025-12-07

I replaced the battery on my dad's 10-year-old Macbook laptop, thanks to ifixit for their instructions. I also tried to work on some tutorials but got bogged down and didn't complete them, but I did get some good writing down for some articles. Lastly, after installing L5 on my dad's old Mac, I decided to test some of the example code from the website. The horror: I found an annoying tiny bug that won't be commonly experienced by many people, and yet, bothers me since I am trying to get cross-platform equivalency of L5. The bug is this: when switching to fullscreen on the old Mac, the setup's background color didn't persist when switching to fullscreen if no further color was added in draw. On Linux, I can't reproduce the bug. I don't have a Windows machine around now to test on that. I spent almost two hours trying to solve this bug, with all sorts of solutions, but the only solutions that worked caused other problems in their stead. In the end, I gave up and will have to document and hopefully learn some more and try again another day. Frankly, it's easy to fix if a programmer just adds a background color to their draw, or adds a background color in the windowResized function. Hmmm, that gives me an idea on another way to try to fix it internally in the library....

## 2025-12-06

I created a new [tutorials](https://l5lua.org/tutorials/) and [examples](https://l5lua.org/examples/) sections to the L5 website and began porting some from the p5.js and Processing sites, which are licensed CC BY-NC-SA. I updated video playback and added functions: loop(), noLoop(), time(), volume(), and native methods play(), pause(), seek(), isPlaying(), getWidth(), getHeight(). I updated image() to handle videos as well as images for restoring/drawing tints, and fixed CHORD in arc().

## 2025-12-05

Was out most of the day and visited Joe's opening for 'First Friday' at GrizzlyGrizzly in evening. I saw some old friends. I really enjoyed the exhibit.

In the evening I did some work on L5 and the website. I had a bug so fixed arc drawing for chord() mode. After I tried starting to build out an *examples* section to the website and porting over some examples from p5.js but didn't complete it.

## 2025-12-04

I finished the first alpha release of [L5](https://l5lua.org)! I'm typing it here first, then will post online and notify friends. I've easily put hundreds of hours into getting to this moment. I feel like I should rest, but the next steps are to try to spread the word to friends and get some initial use and feedback. Then based on that start building out further and getting some contributions. I'd like to add lots more tutorials, build out the error system, and refactor and expand the API with any functions I've missed or are incomplete.

In the afternoon I met with Kit to work on our academic paper. Most of the rest of the day beyond cooking has been making sure [L5's code repo](https://github.com/L5lua/L5/) and [documentation site](https://l5lua.org) were complete. I finished the reference pages (197 of them) that I wanted to get done, tagged L5 with a 0.1.0 release, added download links.

My friend Janek liked the little L5 studies project Painterer I made two days ago and asked if it could live on the web. Well, yes, it could in p5.js! So I made a quick [port of Painterer to p5.js](https://editor.p5js.org/2sman/full/gynGKq8by). So far I've ported hundreds of p5.js example sketches to L5 so it was funny for the first time to go in the reverse direction. Now it is possible some L5 sketches could be made to run with love.js for web but I don't know if I want to pursue that for now but maybe a script that's a p5.js-to-L5 bash script could be next, lol!

## 2025-12-03

I updated the [p5.js to L5 converter bash script](https://gist.github.com/lee2sman/f84e03ef5e5209a9466d2c0795c2d50a), which is basically a collection of regex expressions with sed. I did have help but it still could use some improvement. This is what I use as my starter each time I create a new reference page since I'm starting with p5.js's reference and converting what I can.

Then I put it to work again and started grinding through editing/building more reference pages and bug-fixing L5 as issues came up. I updated hex() to pad to 8 digits by default, for feature parity with Processing-p5. I made sure all conversion functions have table support so they can accept an array and return an array with all members converted. I did some tests with push() and pop() and realized L5 does not have parity with Processing-p5.js in terms of containing style changes. It only contains transformations. I thought about implementing style on top but decided against it for now as I don't want to introduce too much more heavy internals so I just documented this on the [push()](https://l5lua.org/reference/push/) and [pop()](https://l5lua.org/reference/pop/) reference pages. Anyway, I'm moving right along on the reference and hope to finish the reference maybe tomorrow.

## 2025-12-02

Today was spent working on reference pages and debugging the [L5](https://l5lua.org) language library, getting ready for the pre-alpha release. What I worked on today: save() can take an optional filename. I added an alternate data structure for single element tables to saveTable. I updated text() to deal with non-strings. Lots of fixes to events: key detection majorly improved, fixing delete and function keys, etc reporting. Surgical fix so that keyTyped() reports true at the correct spot. Cleaned up mouseWheel() (no need to report x-value since wheel only scrolls vertically). The biggest update/fix was debugging and correcting the order of mouse handling events. mousePressed() runs as soon as the user clicks the mouse. mouseReleased() runs as soon as the user releases the mouse click. mouseClicked() runs immediately after mouseReleased(). Phew. Worked through a ton of reference pages and it looks like I have a bit under 30 left to do now. At the rate of 10 a day I seem to be on now maybe there are 2 - 3 days left.

Before bed when I should have gone to sleep I decided to work on some *L5 Studies*, where I code sketch and try out building different projects in L5, usually improvising as I go. I ended up making a procedural painting generator inspired by [No Paint](https://nopaint.art/) app.

![a procedurally generated digital painting - lots of squiggles and bright colors and lines]({{"/images/log/L5-painterer.webp" | absolute_url}} "a procedurally-generated digital painting")  
*a procedurally-generated digital painting with lots of squiggles and bright colors and lines*

## 2025-12-01

This is the start of [December Adventure 2025](https://eli.li/december-adventure), an unofficial monthlong activity started in 2023 by online friend Eli where all who choose to participate work at their own pace on code and other creative projects, and keep a log about their work throughout the month. In fact this very log you are reading right now grew out of my past positive experiences participating, so I'll continue things from here. 

Here's some projects I'll work on this month:
* I'll finish up the initial round of documentation pages for the [L5](https://l5lua.org) creative coding library in Lua.
* I'll also deal with bug fixes as they come up
* I'll come up with a good system for contribution (git, issues, what else?)
* I'll work on some emulator projects
* maybe a BASIC interpreter in Lua
* I want to get up all my concert recordings from this summer/fall, and perhaps rebuild the faircamp website
* Move Dig Archive to a custom domain.
* I'm not sure what else

Little things come up periodically. Today I started and finished NaNoGenMo 2025 with a [small project](https://github.com/NaNoGenMo/2025/issues/24), based on Ulysses. I used a bash script to shuffle lines of the experimental novel. I started with something else, but bash won out in the end.

## 2025-11-30

It's been a whirlwind few weeks as I completed my residency at ZK/U. On the 20th we had our Openhaus open studios. I presented new works, including *Altar*, built at ZK/U. I also performed a live concert with Zelin and Siiri. I traveled back to the US for Thanksgiving and a reunion. 

![Stepan looks on at installation with 3 monitors showing black and white images, graffiti, plants, old laptop, mug, skateboard, speakers]({{"/images/log/altar.webp" | absolute_url}} "Stepan looks at Altar installation with monitors, plants, custom software, sound, graffiti, skateboard")  
*Stepan with Altar, 2025* 

After Openhaus and continuing to today I worked on bug fixes and L5 reference documentation. Here's some of the more notable fixes from the git log: 

* added helper references to loadTable
* max and min functions can accept tables
* added exp()
* fixed resizeWindow()
* fixed deltaTime output from seconds to milliseconds for alignment with Processing and p5.js
* add resetMatrix(), fix applyMatrix()
* fixed a backBuffer canvas tint issue
* fixed fullscreen() to correctly send to external displays on Windows
* update defaults to filters. fix inconsistent pixel loading.  
* fix tinting to apply to image objects not all drawables
* add in error checking to imageMode() rectMode() ellipseMode() angleMode() loadImage() loadVideo()
* fix textAligning and wrapping
* wrote, edited documentation and produced screenshots or gifs for 150+ reference pages
* updated some colors, fonts and added a copy button for all of the codeblocks on the L5 website

## 2025-11-19

In the afternoon I worked on a few more reference pages. Then band practice improv sesh with Siira prepping for our concert. Afterwards I began working to set up for tomorrow's Openhaus open studio at ZK/U. In the process, for the first time I tested whether the fullscreen function accurately could send to external monitors as one of my installations uses multiple screens. I found it didn't work correctly on the 12 year old Windows machine I've been testing L5 with, but with some fixing it works well and with parity on Linux and Windows, and now it's easy to send a sketch to play fullscreen on an external display. I set up a pretty large multi-monitor installation, running a generative L5 program on each of 3 monitors. Afterwards studio visits with Zelin and Stepan, and feedback from Nina remotely from Greece. 

## 2025-11-18

In past 5 days I've put in dozens of hours of fixes to L5 and work on the reference pages, of which there are now just under 200 pages! In contrast, p5.js has just under 400 pages, but it has a LOT of browser-specific functions that don't make sense for L5, so while L5 is expected to grow a little bit more, I can't imagine more than 20 to 50 more functions to be added? Some of the functionality I've improved in the past couple days are textAlign(), textWrap(), text() (BASELINE positioning), imageMode(), rectMode(), ellipseMode(), set(), filter(), tint(), loadImage(), loadVideo(), bezier(), the pixels array, loadPixels(), updatePixels(), 

Tested the website on non-JavaScript browsers in links (command line), w3 (command line, with an image extension to show images), and Dillo (an oldschool, tiny, non-JS web browser). I also removed the web loaded font to slim down the page load, with the goal that the website (like the L5 library itself) be fast to load even on older equipment or on lower bandwidth devices.

I sent out my monthly email newsletter. Our ZK/U Openhaus is this Thursday. More music practice with ZZZ and Siiri for our concert.

## 2025-11-16

Last night I went to a performance with Z at Volksbuhne of performance art scores/music by Nam June Paik. It was a bit zany post-fluxus performance art. Afterwards was a big fundraiser event at ZK/U.

I spent much of the weekend plugged into my laptop trying to grind through the reference pages and fixing bugs in L5. I fixed some of the color modes like HSB and HSL which I think should be working much better now. 

So now you should be able to work with colors in all of the following ways:

* fill(grayscale)
* fill(grayscale, alpha)
* fill(R, G, B)
* fill(R, G, B, alpha)
* fill(HSB)
* fill(HSL)
* fill('HTML color name') or
* fill('#3-digit hex code') or
* fill('#6-digit hex code') or
* fill(color-object-table) 

Wow, that's a lot! I hadn't thought about it until now. And that's why debugging took me so much time. I had to build in some sanity checks and make sure things worked correctly for: color(), fill(), background() - which also takes an image file input, and fixed lerp(), lerpColor(), brightness(), lightness(), hue(), alpha(), red(), green(), blue().

In addition, I had to fix all of the documentation pages for each of these, plus many others, test all of the code and produce screenshots to add to the documentation pages. There are about 200 pages right now! It's a lot. Still a good bit to go but I'm on a roll and the end is (soon) in sight. Will keep grinding through it this week. 

## 2025-11-14

I've put a good deal of work into L5 this week, both expanding the library to add many more functions, as well as improve the documentation website to get it ready for a soft launch.

I added boolean(), byte(), char(), float(), hex(), str(), unchar(), unhex(), fract(), log(), norm(), pow(), sq(), sqrt(), asin(), acos(), atan(), atan2(), randomGaussian(), randomSeed(). These were mostly trivial to implement in Lua/love. I experimented with building a noWindow() mode to run headless, but I don't yet know if it's possible to render graphics to a file this way (I think not), so am holding off on adding this to the library. I spent a lot of time on the website, writing some introductions, tutorials, and the like, and cleaning up all of the reference pages. There are 186 reference pages. I also included a few notes where some of the functionality was still missing but intended to be added later. 

Today I had *band practice* with Zelin and Siiri. We'll be performing together next Thursday for the Openhaus at ZK/U, which is also when I'll put out the pre-alpha of L5 to friends for testing.

## 2025-11-09

In L5 Studies tonight I implemented a first version of a webcam library!

I'm not targetting finishing this by the time I release a pre-alpha of L5 but it is important to me that there is a useful audio library and a camera library that can be used with L5. I have already set up a test of an audio library a month ago and it went ok. Tonight I tried to take on accessing the webcam, which wasn't obvious what to do at first. I implemented a little webcam library using libjpeg-turbo in C wrapped in a little webcam.lua library that can be used with L5.

![L5 code and window showing screenshot from live camera footage, thresholded into black and white]({{"/images/log/L5-webcam.webp" | absolute_url}} "L5 code editing with running program showing a window with live footage of my camera showing me, thresholded into black and white")  
*Screenshot showing code and a threshold filter running on top of the live camera footage*

## 2025-11-08

I'm in Leipzig for the weekend and visited GfZK museum, 47m Contemporary, a beautiful university library, and a GDR history museum. I met Chaline for lunch. It was really nice to reconnect after their great talk at Offline a couple months ago.

Before bed I put in a couple hours on L5 and lo and behold solved the "double setup" bug so that setup is only called once and properly draws graphics to the screen. The bug had been a result of incorrectly modifying the underlying framework which only allows drawing in draw by default, but I wanted it to work like Processing/p5 and allow drawing graphics anywhere. I also corrected the fullscreen() function to support monitor selection, and simplified the call to parallel Processing rather than the more obtuse p5.js version. The next step is to finish the reference this week so I can create a pre-alpha release and start getting testing from people beyond just me.

## 2025-11-06

I added [FLOSS + Art](https://leetusman.com/archive/floss-art/) to the ➘Dig Archive.

## 2025-11-05

Studio visit with Compost collaborator [Arne](https://arnes.space/) today. Arne is currently building a processing-like web-based IDE for coding visuals on E-ink screens and displays, implemented in Lua! We exchanged ideas on IDE design and I tried out writing code in the inkblot language. I also showed L5 and we played with PureData/PlugData and I spent time making music with Arne's PureData patches for midi hardware. Really fun. We'll try to get together again before I leave the residency program.

In the late evening I had an idea to implement a writing program in L5 that emulated creating Captcha-style text. First I looked for Captcha fonts but didn't find anything to my liking. Then I spent a surprisingly long time to attempt writing the software, and ended up adding applyMatrix() function to L5. Each key or mousepress re-mixes the text display.

Here's one of many iterations:

![L5 code and Captcha program running, with the text Hello L5]({{"/images/log/L5-captcha.webp" | absolute_url}} "L5 code editing with running Captcha program, displaying Hello L5 in captcha-style text")  

## 2025-11-04

![Speaking at UDK Generative Kunst]({{"/images/lee-at-udk.webp" | absolute_url}} "Giving a talk to the Generative Kunst class at UdK")  
*Giving a talk in the course Generative Kunst at UdK Berlin, photo by Bruno Gola*  

I was invited by computational artist, sound artist and live coder [Bruno Gola](https://bgo.la/) to give an artist talk to the Generative Kunst class at UdK University of the Arts Berlin this afternoon, for a course with Prof. Alberto de Campo. I spoke about my background, showed my artwork, my recent research on encoding quilting, and my work in artist-run community. I also introduced [permacomputing](https://leetusman.com/nosebook/permacomputing-links) and intersections with our work as computational and new media artists. Afterwards we had a lively discussion and the students had interesting ideas to discuss around preservation, speculative design, permacomputing and community infrastructures.

In the evening I added [A Traveling Network of Feminist Servers](https://leetusman.com/archive/feminist-servers) to the [➘Dig Archive](https://leetusman.com/archive/). I met with Caleb to show each other what we're working on. He gave a suggestion to add in some curatorial/best-of section to the Dig Archive like UbuWeb does with their TopTen, or some other sites do with suggested syllabi. I tested the site size and it's less than a 1MB on load so maybe I should submit it to [1MB club](https://1mb.club/). Maybe I could get it down further?

## 2025-10-30

Made a little rainfall screensaver in L5 studies to start the day.

![rainfall and wind coded in  L5]({{"/images/log/L5-rain.webp" | absolute_url}} "rainfall and wind simulator, coded in L5")  

## 2025-10-28

I coded a few projects in L5 for my *L5 Studies* series this past couple of days. I made a daily *ritual* program that provides a prompt for a little daily ritual to perform (a meditation, art-making instructions, etc). It changes only when the day changes. 

![A daily rituals program in L5]({{"/images/log/L5-rituals.webp" | absolute_url}} "A daily rituals program in L5")  

This weekend was also the streaming Roguelike Celebration conference, for game designers, academics, programmers, etc who work in procedural generation broadly and in *roguelike* games specifically. I found myself tinkering on such a game myself while tuning in. It is not at all a complete game, but it's on its way.

![A little roguelike in L5]({{"/images/log/L5-roguelike.webp" | absolute_url}} "A little roguelike in L5")  

Finally, while listening to a Brian Eno interview today in the times I decided to do some free-coding and I ended up making a pretty nice acquarium simulator that I think is fun to leave on in the background.

![A blurry acquarium in L5]({{"/images/log/L5-acquarium.webp" | absolute_url}} "A blurry little acquarium simulator, coded in L5")  

In the afternoon Anna gave us an intro to some knitting. In the evening we had our group dinner and artist presentation at ZK/U, and then we played poker and then did more knitting.

## 2025-10-26

In the past few days I've been planning work on a book outline and some brainstorming. The goal is to turn the podcast into a printed form. I also did some L5 work, and mocked up a simple roguelike system in about 160 lines of code while watching the streaming Roguelike Celebration conference. Lastly, did some music with Zelin again on no-input mixing board but hurt my ears! Ugh. I saw some great shows prior to that: Suzanne Ciani, DJ Haram, and some others.

## 2025-10-22

### Work on L5 today

* added loadVideo() function
* Added a Video page with example code, intro to working with video playback, and adapted notes from Godot documentation on working with Ogg Theora files. Since it has the same issues as L5 built on the Love2d framework, I adapted the notes for L5, thanks to the Creative Commons licensing of its documentation.
* Added the ability to set a background image by specifying an image variable to background()
* Added copy() and blend() pixel functions. The copy function works fine but the blends could use more work likely implementing them in shaders.
* Added ability to set custom cursor images via filepath

## 2025-10-21

In the evening I visited panke.gallery for a reading/discussion group on Hito Steyerl's new book. I met some interesting artists and scholars, and we discussed Machine Learning and exploitation, and military origins and ongoing connection to computing.

Today I added the loadVideo function to L5, which turned out to be trivial after some testing, and added documentation pages to the in-progress documentation site for the language. The mechanisms for loading and playing video differ between L5, Processing and p5.js. L5 is the simplest in terms of loading and playing, but unfortunately, the underlying library Love2d only allows Ogg Theora video files currently (ogv), so video files have to be converted from other codecs first (mp4, mkv, mov, etc). In comparison, Processing has a separate Video library, and its API differs a bit from vanilla Processing, which is not very learner-friendly in my opinion, but it allows more codec options. Likewise p5.js allows more codecs but one must use the createVideo function which adds a separate video element to the browser's DOM, which must unfortunately be manually hidden, and while the video is loaded asyncronously one must check first that it is loaded before drawing video frames to canvas. I considered whether I should ship a tool to convert videos to ogv but instead I've currently just linked to Handbrake video converter and mentioned ffmpeg command line tool.

## 2025-10-20

I made a compelling abstract artwork using L5 today and my photographs of graffiti in Berlin. Randomly layered additive thresholded and tinted images build up, creating a heavily textured shifitng composition.

![layered textures of black and white graff in L5]({{"/images/log/L5-graff.webp" | absolute_url}} "Layered textures of black and white graff in L5")  

## 2025-10-19

Two hour jam today with Siiri. Ella joined us for some time as well. Our instruments were clarinet, microphones, and no input mixing board. We recorded the full set and will hopefully put some online.

### L5 work today: 

* Fixed looping ( see: loop(), noLoop() and isLooping() )
* Added default width and height to offscreen graphics canvas in createGraphics()
* Added ability to draw textures to (custom) shapes with newly implemented functions texture(), textureMode() and textureWrap()
* Added a bunch of reference pages with example code and screenshots

## 2025-10-18

I joined the Creative Code Jam organized by Creative Code Berlin today, to work on L5. I cleaned up my comments in the library, then implemented custom shapes. I spoke with Stef who works on the Processing infrastructure, did some tests in p5 and based on that implemented a p5-like version of these functions using Love2d's polygon function and passing in an array of vertices.  

![beginShape function in L5, with code editing on left and rendered custom shape on right]({{"/images/log/L5-beginShape.webp" | absolute_url}} "An example of creating a custom shape with the new beginShape(), vertex() and endShape() functions.")  

And in L5 studies tonight I decided to use the new functions and draw a grid of random blobby polygons and colors.

![code and grid of blobby polygons in L5]({{"/images/log/L5-blobbies.webp" | absolute_url}} "Code and grid of blobby polygons in L5")  

## 2025-10-15

Monday I led an introduction to making visual art with code, with p5.js, at ZK/U. After I gave an artist talk on my practice and current work in the residency.

![Leading a workshop at ZK/U]({{"/images/log/zku-workshop.webp" | absolute_url}} "Workshop at ZK/U")  

Tuesday I met with Kit to brainstorm for a research paper we're co-writing. In the evening I saw Tuvan ensemble [Huun-Huur-Tu](https://huunhuurtu.wordpress.com/) perform. I saw them play one other time, while living abroad in Prague 22 years ago!

## 2025-10-12

Added [Practical Retrofitting](https://leetusman.com/archive/practical-retrofitting/) for Obsolete Devices to the ➘Dig Archive. I think it's an interesting topic that would be valuable to share with others in another format, particularly as a zine. But unfortunately its creative commons licensed with No Derivatives, meaning that you cannot remix or alter the format or contents.


## 2025-10-11

I polished up the Toothbrush Timer app a bit, adding in positioning that indicated what quadrant of the mouth your brush should be in, and where to change every 30 seconds til done. I also added a nice ending slide when you're finished. I've also now used the program while brushing my teeth :)

## 2025-10-10

Tonight in L5 studies I coded a simple toothbrush timer. It shows a moon or sun smiling depending on time of day, and a rotating toothbrush. Every 30 seconds the toothbrush moves to a different position to remind you to move to a different quadrant of your teeth. When you're done, it just says "Donezo" but maybe it should stick out its tongue? Well, it's a minimal version of the program and I need to stop now but will hopefully come back and finish it off in the days ahead. 

![Toothbrush timer app with code on left and a smiling moon with toothbrush on the right]({{"/images/log/L5-toothbrush.webp" | absolute_url}} "Toothbrush timer app with code on left in L5 and a smiling moon on right with toothbrush")  

This was a good task because it reminded me I should add hour() minute() and second() functions, thankfully trivially easy in Lua.

Also, earlier in the night I went out with Fletcher and Grayson, who both wanted to know why they or other folks that already use Processing or p5 would want to use L5, or even vs TouchDesigner, OpenFrameworks, etc for that matter. Good question! I gave some answers and a more full answer will be presented later, but here's quick thoughts:

* works on old/ancient computers (need to define this. So far I've tested on 12 year old Windows, old iPad, new Mac, 5 year old Linux...)
* stable, very fast, consistent
* cross-platform
* desktop-oriented though same code can (likely) be packaged for browsers through love.js (via Emscripten)
* consistent, cohesive syntax
* long term reliability of Lua and Love2d
* small (size) - only 4.5MB and doesn't require a browser or internet.
* can package up sketches into application
* a compiled languages, scripting language, dynamic typing
* more TBA

## 2025-10-09


![Zelin's hand on our No Input Mixing Board]({{"/images/log/no-input-zelin.webp" | absolute_url}} "Zelin with our no input mixing board")  

I did a recording session using the No Input Mixing Board as our instrument, with Zelin at ZK/U. See [No Input Mixer Workshop from The Noise Upstairs](https://leetusman.com/archive/no-input/) in my Dig Archive for more on this technique. We played for an hour and a half or so, having a great time with feedback and two microphones added in. Later we listened back and took notes. We created a mix, a little studio work moving or removing some sections. It's currently 36 minutes, and I'm enjoying listening to it. Since we're both also doing field recordings in our practices, we talked about integrating these recordings to get a more dense and changing textures into our sound. 

I've also been listening to other No Input Mixing Board recordings, to identify what I like or don't like in the style. Far from being just a wall of erratic noise I'm enjoying the subtleties and textures possible. Toshimaru Nakamura, considered father figure of the technique, has dozens of albums available on Bandcamp. I picked up [Stationary](https://awavepress.bandcamp.com/album/stationary) by Nakamura working with US composer Mark Trayle on laptop. I like the variety of textures, the use of space, the overlapping of sounds. I also picked up [UK ツアー 2019](https://scatterarchive.bandcamp.com/album/uk-2019) with Sam Andreae on alto saxophone and DIY electronics, David Birchall on electric guitar, Toshimaru Nakamura on the no-input mixing board and Otto Willberg double bass. This one I really love, for marrying the free improv post-jazz scene and sound with Nakamaru's reworking of industrial noise into sensitive soundscapes, tones and texture scrapes. It's been nice playing the mixing board as something that opens up new sound possibilities and still feels intuitive as an instrument with just enough unpredictability to make it interesting, in some ways a more constrained and less precious alternative to my modular synth.

## 2025-10-07

I added set() and get() and a number of reference pages and examples for L5 today.

## 2025-10-06

I updated the json data of [rappers from XXL's Annual Freshman cover](https://github.com/dariusk/corpora/blob/master/data/music/xxl_freshman.json) and it was merged to Darius Kazemi's Corpora, which I occasionally have contributed to. The Corpora project is a collection of word data for creating bots, computational poetry and rapid prototyping of other art and code projects. I use it in my teaching as well.

I started working on adding the ability to address the pixels array in L5. Tonight I implemented pixel-drawing functionality: global RGBA pixel array, loadPixels(), updatePixels(), pixelDensity() and ported example reference code from the Processing and p5.js references.

I also made a variation on my long-running note-taking tool *today* that lets me save info to previous days (*yesterday*).

For example, to write an entry for today:

```fish
# today
set filename (date +%Y%m%d).MD
nvim ~/DOS/CAROUSEL/ENTRIES/JOURNAL/$filename
```

If I wanted to update yesterday's entry:

```fish
# yesterday
set filename (date -d "yesterday" +%Y%m%d).MD
nvim ~/DOS/CAROUSEL/ENTRIES/JOURNAL/$filename
```

These fish scripts are each saved in /usr/local/bin. The CAROUSEL from the path name is a reference to typewriter program [CAROUSEL](https://partytimehexcellent.itch.io/carousel) by Rachel Simone Weil.

## 2025-10-05

I was away on a trip and away from my computer for about a week. I'm back. I made a small little L5 Studies sketch tonight before bed when I wasn't feeling like diving into something that deep. On my trip I had my iPad and took some notes on things to fix in the L5 library this week. I also did some testing with the main maintainer of [pyradio](https://github.com/coderholic/pyradio) to figure out some UI improvements I suggested.

![L5 'nothing' bright lines sketch]({{"/images/log/L5-nothing.webp" | absolute_url}} "Openhaus at ZK/U")  

## 2025-09-30

I worked on L5, fixing the blur filter, changing from Gaussian to Exponential based on info from Processing and p5 folks Kit and Raph. I also tried to fix my setup code issue where I am calling setup twice, once to set screen size and global vars relating to that, and a second time to draw any graphics there. I'm causing some minor bugs in my current system where I modified Love2d's default run and load functions. I didn't solve it yet but have some ideas to try. I also started compiling tables of what I'm currently calling Processing Family Langs, based on the [Uzulangs site](https://uzu.lurk.org/). I think seeing all of the Processing-related languages in one place would be a helpful starting point for some kinds of research and development, not to mention history.

In the evening I presented [Dig Archive](https://leetusman.com/archive) and a short live performance with Modular Play on my Playdate for the Show Us Your Screens event at Offline place. I met some artists and really enjoyed the work presented. I took lots of notes of projects to check out.

## 2025-09-26

I monkeyed around with the build script for Dig Archive, and now there is a [RSS feed](https://leetusman.com/archive/feed.xml). Chouette! While I was at it I also added a [404 page](https://leetusman.com/archive/404.html). 

For my L5 Studies tonight I took on a bit of a challenge to make a collection of microgames in the style of beloved [Warioware D.I.Y.](https://en.wikipedia.org/wiki/WarioWare_D.I.Y.) I was looking earlier today to see if such a thing existed for the Playdate handheld console. It seems like it should exist, no?! There was evidently a microgames jam with that idea in mind.

In any case, for my L5 programming tonight I ended up making some confused hacker mini game system with 3 different games. It's 'complete' in the sense that you can play it. It took me a couple hours and is a couple hundred lines of sloppy improvised coding. I've been using my own reference pages from the as-yet-unpublished L5 reference docs website (they still need work, more pages and polishing before going live), which has been helpful.

Anyway, here's a screenshot of gameplay of my silly microgames.

![Hacker minigames]({{"/images/log/L5-minigames.webp" | absolute_url}} "Code and gameplay from my Hacker-ish minigames")  

## 2025-09-25

![Openhaus at ZK/U]({{"/images/log/zku-openhaus.webp" | absolute_url}} "Openhaus at ZK/U")  

Openhaus at ZK/U went really well. We had 100 or so visitors and I showed *Dig Archive* and the generative digital quilt patterns work, using Jayrope's 12 year old PC. I showed the *Hyphenated* project, created in p5.js, on a giant flatscreen monitor. Lastly, I projected *Comfortably* on the wall, a work currently exhibited via NY's [New Media Art Space](https://newmediartspace.info/current.php), BUT...I didn't want to pull up a browser, then run fullscreen, then reload to get the right dimensions, and worry about a browser having memory issues. So instead, I ran the L5 port of the project I made last month and ran that instead. And lo and behold, it worked really well. It ran continously from 4pm until midnight, never once crashing or needing a restart. I'm really happy with it, and this is the first time a L5 program has been *exhibited.* I performed a good and noisy music set tonight too. I wish I had recorded it.

While doing L5 Studies tonight before bed I wanted to draw to an offscreen buffer. The reason for this is because I wanted to draw freehand but have the underlying background color change randomly only once each time the mouse is pressed. To do this requires allowing continuous drawing on an offscreen buffer that then gets applied on top of the background. This meant it was time to implement offscreen buffers in the L5 library, so I created the createGraphics() function (that's what it's called in Processing API). 

In this example I created a drawing program that lets me draw with photographs. The background only changes when the mouse is pressed down, but the drawn photos are persistent due to...the new createGraphics() function.

![An L5 program that makes use of drawing to an offscreen buffer, then applying that on top of a changing background]({{"/images/log/L5-offscreen.webp" | absolute_url}} "An L5 program that makes use of drawing to an offscreen buffer, then applies that on top of a changing background")  

I also added my [Quilt Poems](https://leetusman.com/archive/quilt-poems/) chapbook to the Dig Archive as I'm almost out of print copies and some folks asked me for them. I will probably try to print another edition though.

## 2025-09-24

I began setting up for the Openhaus at ZK/U. In the evening I added [Decolonising the Digital: Technology as Cultural Practice](https://leetusman.com/archive/decolonising-digital/) to the Dig Archive. I also enjoyed listening to podcast episodes [The World on a Wire Show 1: Beautiful numbers, magic numbers, & illegal numbers](https://archive.org/details/ep01_20190910) and [Solarpunk Presents: Low Carbon Methods for Doing and Communicating Research With Dr Anne Pasek](https://www.solarpunkpresents.com/season-five/low-carbon-methods-for-doing-and-communicating-research-with-dr-anne-pasek).

I worked on L5 studies to make a simple poster generator and realized I hadn't implemented int() so I went back to L5 and took some time to try to correctly add it. Since Love2d uses Lua prior to 5.4 I didn't have the math.tointeger function to rely on. Once that was finished I threw a bunch of screenshots in my posterer directory and used them as sources to generate some simple poster page layouts, then called it a night.

![An L5 program and very simple layout page of a the Three Lores zine by Mark Price from Dice Crew with one of my generated Pico-8 quilts overlaid]({{"/images/log/l5-posterer.webp" | absolute_url}} "A screen of L5 code and the generated posterer output showing hollowed out dice and dollars overlaid with a 8bit digital quilt")  
*An L5 program and very simple layout page of a the Three Lores zine by Mark Price from Dice Crew with one of my generated Pico-8 quilts overlaid*


## 2025-09-23

Prep has begun for the Openhaus happening at ZK/U this Thursday. I'll be screening a work I created at Signal Culture a few years ago, as well as new work I made in p5 for an online exhibit. I'll be performing modular synth too. 

In the evening tonight I jumped back into L5 working within my *L5 studies*, an approach to mastering a tool or technique by starting from zero and iteratively building small projects and experiments with that tool. I learned this while following the [Teletype Studies](https://monome.org/docs/teletype/studies-1/) several years ago, and a couple years ago I did [Puzzlescript Studies](https://leetusman.com/projects/puzzlescript-studies/) for about a month. 

The L5 studies is a way for me to use my language when I'm not feeling like developing it, but it's also a way to debug, test and find its affordances and limitations. Since the Processing / p5 API is second nature to me after using it for a decade, it's quite easy for me to try things out.

Tonight I implemented a LOGO-like turtle graphics mini language, fairly rapidly in a couple dozen lines of code, then tested it out.

![A random turtle walk implemented in a LOGO-like language created in L5]({{"/images/log/l5-turtle.webp" | absolute_url}} "A screen of L5 code and the turtle graphics library running in a screen on the right")  
*A random turtle walk implemented in a LOGO-like language created in L5*

I also added [The Scores Project: Essays on Experimental Notation in Music, Art, Poetry, and Dance, 1950 - 1975](https://leetusman.com/archive/scores-project/) to the Dig Archive. Later I added Anne Pasek's [Getting Into Fights With Data Centers zine](https://leetusman.com/archive/fight-data/). Thanks to the authors/editors of both for Creative Commons licensing their work.

## 2025-09-15

I'm back from the UK. I arrived in Sheffield Thursday evening for the [Algorithmic Pattern Salon 2025 conference](https://2025.algorithmicpattern.org/). Friday I attended talks, met folks I had previously only seen online, like the [Pastagang](https://www.pastagang.cc/) live coders. That evening was a performance night. The next day were more talks, including my own on Encoding and Experimenting with Vernacular Quilt Patterns. I think it went well, there were some good questions from the audience, and I spoke with a number of people afterwards. That evening was a festival of live coding performances at two venues that went late. The next day was the last. After a morning workshop I attended on a japanese weaving technique I traveled with Bérénice and Hannes on the train from Sheffield to the Manchester airport. I'm back now in Berlin and feeling motivated on my projects.

## 2025-09-10

Great opening of Everest's exhibit at panke.gallery tonight. I feel so self-conscious about irl presentations of my artwork, made on a computer, with an audience i usually consider online-first. So this reassured me about my old Babycastles days and my own approach: set up some screens, make it a varied and interesting use of the space, and trust your audience will be able to view the screen as 'primary', with screens as surfaces. While it was a 'minimal treatment' it was still compelling. Everest set up old broken internet pieces starting from the right of the gallery entrance and then more recent and working pieces as you moved around the space, and used a variety of types of screens (CRT, flatscreen, large monitors, old, etc) and some wall-mounted printouts of bots, printed books and interactive games/engines. 

In the evening I added an [interview with Danielle Brathwaite-Shirley](https://leetusman.com/archive/danielle-interview/) to the Dig Archive. 

## 2025-09-09

Added [PocketC.H.I.P. original documentation](https://leetusman.com/archive/pocketCHIP/) and my collaborative [Radical DIY Computing zine](https://leetusman.com/archive/radical-diy-computing/), from a workshop taught using the PocketC.H.I.P., with Echo Theohar, to the Dig Archive.

Saw DJ Marcelle at Hamburger Banhof tonight. Great set.

## 2025-09-05

Big success getting a working version of the 3d quilt pattern generator going in Picotron. I'm pretty happy with this, with maybe some work to be done to see if I can shift the color pallet any further.

This is a little animation of what the program looks like. A new *quilt* is generated from the quilts.lua pattern data every couple seconds.:

![Animation of a rotating Little Coins quilt and 2 more, in Picotron]({{"/images/log/quilt_2.gif" | absolute_url}} "Animation of a rotating Little Coins quilt where there is a dominant white color with little bits of colors throughout the digital 'quilt', in Picotron")  
*Animation showing the current state of the program. It generates a Little Coins quilt pattern, Diamond in a Square variation quilt, and God's Eye pattern - all 8x8 resolution.*  

The 3d effect is an optical illusion caused by the "balls" shifting in scale in relation to each other. I tried some variations with squares but it just didn't look very good. The balls were able to maintain the illusion better.

Here's my favorite *housetop* pattern, generated.

![A housetop pattern 'quilt', in Picotron]({{"/images/log/quilt_5.png" | absolute_url}} "housetop patterned quilt, in Picotron")    

I also modified the program to accept any resolution input grid so that it would scale up and down depending on the size. These tests above are all 8x8. But I performed tests with larger sizes as well.

![A test of a larger grid size, in Picotron]({{"/images/log/quilt_4.png" | absolute_url}} "Test of a larger quilt grid size, in Picotron")    

## 2025-09-04

I saw it was on sale so I purchased [Picotron](https://www.lexaloffle.com/picotron.php) the *Fantasy Workstation* by Lexaloffle (maker of Pico-8, that I use and teach with). I have too many projects right now and thought I would be too busy to get into it (an OS coded in Lua) until finishing some projects here but I put about an hour into it tonight, modifying the 3d carpet program from Zep. I added file input and fed in a 64x64 gridded quilt pattern and then modified it to allow any size input grid. It works! 

![Checkerboard pattern "quilt" grid in 3d, in Picotron]({{"/images/log/quilt-3d.png" | absolute_url}} "heckerboard pattern grid in 3d space made up of small colored balls, low resolution, in Picotron")    

## 2025-08-31

Saw lots of performances over the past week, especially some great music performances at Atonal festival and at a noise show at Aktionhaus. Started German class A1.2. Did some "L5 Studies" tonight as a way to get back into semi-daily L5 work. Fixed a bug where width, height weren't set when running without size (for example, default or in fullscreen mode). Rapidly implemented a 10print maze in L5.

![A 10print style maze in L5]({{"/images/log/10print.webp" | absolute_url}} "A 10print maze with code on left and maze on the right")    

## 2025-08-28

Last day of intro German class today. In evening I went to Collective Capernauts at Cittipunkt. There were performances, poetry readings, performative talks (?). I really enjoyed Nina's invented opening ceremony (can't describe it here). 

In the evening I added some more items to the Dig Archive: 

* [Permacomputing](https://leetusman.com/archive/permacomputing/) interview with Marloes de Valk and Ville-Matias Heikkilä in Counter-N
* [Librarian Is My Occupation](https://leetusman.com/archive/librarian/): A History of The People's Library of Occupy Wall Street
* [Occupy at One](https://leetusman.com/archive/occupy-one/) in BOOG CITY
* An issue of [Computer Graphics and Art](https://leetusman.com/archive/computer-graphics/) from 1977
* The exhibition catalog from the [SEQUENCEBREAK](https://leetusman.com/archive/sequencebreak/) experimental arcade exhibition
* [Curatorial Archives in Curatorial Practices](https://leetusman.com/archive/curatorial-archives/)

## 2025-08-27

I made some minor updates, added some new items, and edited the item page builder to include my editor's notes. And with that I made [➘Dig Archive](https://leetusman.com/archive/) public today.

## 2025-08-26

I spent a bunch of hours on the archive site tonight trying to get it close to a *ready to publish* state. I'm feeling pretty good about it. I just need some feedback from friends and to possibly make some adjustments to color contrast based on accessibility testing.

![New Dig Archive screenshot, in-progress page showing a 2 column centered digital archive gallery page]({{"/images/log/dig-archive2.webp" | absolute_url}} "A blue and light blue 2 color Dig Archive website shot showing a 2 column view of archived works in a centered 2 column grid")    

## 2025-08-25

I added the [CrankBoy](https://github.com/CrankBoyHQ/crankboy-app) emulator to my Playdate and added some roms, such as ones I already owned like Super Mario Land, Paperboy and the like. I also chipped away a little bit at the reference pages for L5 again. I grow weary of this slow process. I think I want to work on other areas, then come back later to fix the reference pages and take screenshots for example.

Next I jumped over to working on my archive page. I changed the CSS, which looks better now, but I still think I may want something to make it feel a bit more *modern* in some way. I added some javascript to change order randomly, by editor's choice, alphabetically, and to open a random page. I also changed the name, to *Dig Archive*, which I also think sounds more current and compelling. But I'll sit on it for a few days and see if it sticks!

![New Dig Archive screenshot, in-progress page showing a 2 column centered digital archive gallery page]({{"/images/log/dig-archive.webp" | absolute_url}} "A blue and light blue 2 color Dig Archive website shot showing a 2 column view of archived works in a centered 2 column grid")    

## 2025-08-24

Mostly took off from coding this weekend. Today I updated my paper for the Algorithmic Pattern Salon, then worked on L5 a bit. I updated the [p5 to L5 conversion script](https://gist.github.com/lee2sman/f84e03ef5e5209a9466d2c0795c2d50a) and then manually went through and started cleaning up the generated reference pages and taking screenshots. I think this may take too long, so I may skip performing screenshots for all the pages and work on some other tasks first so I can get the pre-alpha out the door to those who are interested in testing L5 at this point. I also parked the l5lua.org page. I'll change it when I'm ready to push the web pages live.

## 2025-08-21

I moved the ported reference pages for L5 to the documentation site and manually added them in. It was something like 130 automated pages, compared to my own hand typed 15 pages I did previously in many more hours. This was only the first pass and I still have to edit these pages, add any pages that are missing, fix code examples if anything is broken or not L5-idiomatic (!), and set up automation to do screenshotting of each of the example code programs.

## 2025-08-18

Some scripting implemented to convert all the p5 pages to L5 pages. Initial run seems like it worked, and so did the p5.js to L5 converter. Next step will be to add these to the L5 documentation site, removing anything unused (WEBGL code examples, function calls not present in L5). Then afterwards I'll try to implement an automated screenshotting system to use the Example code blocks and save to an assets directory.

## 2025-08-16

On Friday I met Raphael and Steffe at Praxis to interview them about their work on Processing over the past year+. This was my first live in-person interview in a while for the pod. They are really kind and after our interview we actually spent time looking at the modes of Processing (so that I can later hopefully integrate L5) and we looked at some workflows for forking and converting the p5js reference pages in a more automated way.

That evening I hosted a BBQ and dinner concert at ZK/U with Flux friend and collaborator Patrick, visiting from Vienna, myself on mod synth, and pal SarahGHP doing live coding visuals in her La Habra. Wesley was helpful and generous with food he brought. We pulled out a construction fence to project onto, and many ZK/U folks helped with setup, grilling. 

![Performance at ZKU]({{"/images/log/pat-lee-zku.webp" | absolute_url}} "Performance on the patio, with a construction fence and screen with live coded visuals, a musician in the background, and a crowd watching")    
*Patrick Topitschnig performing music and SarahGHP live coding visuals in front of a crowd at ZK/U in Berlin*

After Patrick and I played we had a performance by Lor on vocals/looper pedals and then enjoyed DJing by Blackmoonchild to close out. The afterparty went late and we had a really nice audience maybe 30ish folks joining us, including some people from my language classes.

## 2025-08-13

Lots of ups and downs with compost.party. First I had issues when I woke up late one day, replugged the server on the roof and it didn't accrue enough power to run through the following night. It came up the next day but then died the following night out of the blue after a full charge. I was trying all sorts of hacker-y things on a flickering broken screen, ssh'ing in and such, communicating with Arnold who was on a bikepacking trip and debugging with me! Finally after hours and days he suggested he needed to pay the cell phone bill, and that there was finally a static IP issue on the raspberry pi at his house while he is away. And so that's where it's at currently, with Compost presently down. I also started some additional logs on there, so have been busy getting that going though can't be seen til the site comes back up and I should be doing L5 and some other work.

Started German classes this week. Es geht's gut. Zuper.

I got some utility scripting done this week.

Rather than remember all the different SSG build/serve command incantations I made a fish function command [blog-serve](https://gist.github.com/lee2sman/3afa82cb75b962877de2f7c7aa96efe4) that will run the correct command to build a site and serve it via Panblog, Jekyll (with custom url), mkdocs or Eleventy.

And my [p5.js to L5 converter](https://gist.github.com/lee2sman/f84e03ef5e5209a9466d2c0795c2d50a) brute forces converting hundreds of p5.js reference programs to L5.

Finally, I made some site builders for compost.party that automatically build custom static site generators. That one will remain private for now until I make a more general iteration useful for others.

## 2025-08-08

Yesterday we installed the [compost.party](https://compost.party) server on the roof here at ZK/U, where I'll be caretaking it for the next several weeks while its regular hosts are away. It's a postmarketOS (Alpine-derivation) setup on an older Xiaomi Poco F1. I'm now set up with XMPP, a new git instance, and server access myself. Helping to host this means having to do daily physical activity to unplug and re-plug-in the solar panel to the phone each day. This is a cool project and I'm happy to be part of it.

![On the roof at ZKU]({{"/images/log/zku-roof-dithered.png" | absolute_url}} "On the roof at ZK_U, dithered")    
*On the roof at ZK/U*

## 2025-08-06

I played at OHM tonight for Zoll 19 Stammtisch. I think there were 10 or 12 of us playing together. It was pretty epic. I wonder if there's anything like this in NYC when I get back. 

![Synths and players lined up at OHM]({{"/images/log/ohm.webp" | absolute_url}} "Synths and musicians lined up at OHM")  
*My view of synths and players lined up at OHM*  

I got home pretty late but tested my port of All the Greens (originally HTML, CSS, JS) to L5. It looks 99% the same. Actually, it looks very slightly nicer. 

## 2025-08-05

I played a show at Pedalmarkt for Zhzhzhzh aka [3333]. The headliners were [Silver Galaxy](https://silvergalaxy-official.bandcamp.com/), consisting of Anna-Maria Van Reusel on synth and Dennis Slypen on guitar and pedals. They were absolutely incredible. One of the best performances I've heard in years. Both are virtuosic musicians. They played in perfect synchrony and harmony. Just gorgeous music. OMG, I played after them. Thank goodness there was a break first. I played a short set, which received a good response, and afterwards I enjoyed talking with folks about the music. Thanks to Pedalmarkt for putting together such a cool event and to Anna-Maria and Dennis for giving me a ride home with my synth.

In the late evening I worked just a bit on the L5 library. Today's goal was to alter the filter shader code to also work on Mac. Success! I sent the updated code to my iPad mini through [LocalSend](https://localsend.org/), an open source alternative to Airdrop that works on Linux too. I then saved to local files into the Love2d-studio files folder. All I have to do is hit play to test, and it compiles. Great! I test some programs. L5 is now (I think) cross-platform. I'm making it a priority to get the reference documentation done over the next week, then to soft launch the site and get some testing from friends before announcing more widely and getting a million bug reports (and eyes on my kludgy code!).

## 2025-08-04

Tested L5 on a 12-year old Windows PC today: It worked fine out of the box, including the filters (shader code).

## 2025-08-03

![All the Greens, a screenshot]({{"/images/green4.webp" | absolute_url}} "All The Greens screenshot of green pixelated chunky blocky artwork with lots of meandering digital doodahs")  
*All the Greens, screenshot, HTML, CSS, JS, Digital Drawings*  

I participated in HTML Day yesterday and made [All the Greens](https://leetusman.com/everyday/298/green/) in a field and in Offline, literally without internet. The piece is generative in that each time you click you get a new variation. Full [writeup](https://leetusman.com/nosebook/html-day-2025) blog post.

## 2025-08-01

In the evening was the Creative Code Berlin meetup. Before heading out I sent the latest L5 to Dan to check on his Mac - which was the first time anyone other than me was checking out the library, and the first test on a Mac. The horror, error! It didn't compile and the error message confused me.

At the Creative Code Stammtisch it was a packed place, maybe 50ish people. I showed my work on L5 and other projects, and mentioned I need to test on Mac/PC hoping someone would say, here's my old Mac for testing purposes! The presentation was fun and I had some good audience questions, including about later adding a 3d library. Maybe! Later I decided to see if I could figure out the Mac compilation problem from earlier and learned in some research that between Lua 5.1 and 5.2 they switched from unpack to table.unpack, however, Love uses LuaJit, which should be 5.1 but they modified this in Love, and it might be the Mac one compiles a different version of Lua. I didn't have ready acces to a Mac for testing but I did have an iPad mini, and I downloaded Love2d Studio app. I converted all table.unpack() to unpack() globally, and had no more errors about that. Now I had a shader error, which seems to be a result of needing to write these differently for different architecture. I turned off the shader code and now my example programs ran on the iPad. My next step will be to look into the shader code and see if I have some alternative options, which could mean rewriting them, changing out for non-shader options, or having to ship alternate versions of L5. Maybe the most logical would be to separate things out into more files and pull the needed module depending on architecture.

## 2025-07-31

I'm really cooking. Lots more bug fixing and I've been building out a website for L5. I came up with a logo, theme site design, and all that. I've completed the intro pages, figured out the license, and started converting the reference pages from p5.js. Screenshotting the sketches takes a while, so I'm not sure if i can figure out a way to automate that, but maybe I'll try that next.

[The script to convert p5.js programs to L5](https://gist.github.com/lee2sman/f84e03ef5e5209a9466d2c0795c2d50a) worked pretty well on the half dozen scripts I tested tonight.

Here's a screenshot of what the website currently looks like. I need to add more art made in L5 so the site looks less framework-y.

![first version of the L5 documentation website with logo and yellow background and intro text]({{"/images/log/L5-website1.webp" | absolute_url}} "First version of the L5 documentation website with logo and yellow background and intro text")  
*Prototype pre-v1 version of the L5 documentation site*

In the process of getting this up I figured out some new problems but mostly have been fixing old bugs that cropped up, like arc, rect and ellipse modes, and much more. But as I cross things off the TODO checklist, new ones seem to get added!

## 2025-07-29

In the past few days I worked on L5 as well as an artwork for the exhibit LOVE.exe at New Media Artspace. In L5 I knocked out some bugs from my TODO list: fullscreen now works correctly; the transform works correctly; I fixed the ellipses and circle drawing modes and the rectangle modes. I also created some test sketches like a basic chessboard:

![L5 code with an overlaid chess board]({{"/images/log/chess.webp" | absolute_url}} "L5 code with an overlaid chess board. Pieces in starting positions.")  
*L5 code with an overlaid chess board*

The artwork I created for LOVE.exe I wrote initially in p5.js but then tried to port it over to L5. At this point, the port is only semi-successful. I hadn't implemented filter() in L5 yet, and I think it will take me some more effort as it will require a shader. Instead I tried to use tinting but that's not really the same thing. Another minor issue was the speed of the background gradient effect was somewhat different. I'm not 100% sure why. And I haven't implemented basic sound like p5.sound yet.

Here's a screenshot from the work, just a moment in time. The piece is of infinite duration, a generative piece called *I Act Comfortably With Others*. 

![grayscale glitched downsampled faces merging together with overlaid text]({{"/images/log/loveexe.webp" | absolute_url}} "grayscale glitched downsampled faces merging together with overlaid text")  
*screenshot from I Act Comfortably with Others, in p5.js*

In the evening was *Show Us Your Screens* at Offline. I gave a 10 minute presentation, showing L5, my new piece, and some previous work. Alex McLean gave a talk and demo of new functions added to Strudel and TidalCycles livecoding music languages, and I got to meet Alex for the first time in person and a number of other artists I had known previously only online.

## 2025-07-24

I went to Casey's opening and talk at DAM Projects. It was great to be able to hang out with Casey, Lauren, Raphael and a number of other folks. I talked with them about L5. Casey mentioned there had been a Lua implementation of Processing maybe 18 years ago! Lauren said when she started p5 there was processing.js, which I forgot about, but she persisted and p5 was adopted and expanded its community, so that reassured me I perhaps am not crazy to embark on this project. Funny question: what if this takes off and it turns into a decade-long project with lots of work and community participation? We'll see!

After a nice dinner (25 of us gathered around two round tables at a chinese restaurant) tonight I returned home and kept plugging away at the API. I implemented the remaining mouse functions and some other API features I'd left. I need to add color modes, then debug and refactor code. I added onto the documentation I started and started looking into how to build a documentation site, especially to host tutorials and a reference.

## 2025-07-23

Sunday was a nice hang with lots of folks at Jack's birthday at the park. I got to see his partner's looms and other devices. I'd love to try them out. Tuesday I saw a great performance, my friends Daniel Fishkin and Catalina Alvarez performing music and film with Berlin-based musicians. Today I met up with Mike for a little college reunion. In the evening I completed most of the P5 API. I added onto the random() function so it auto-detects a table input and outputs a random value. I implemented loadStrings(), saveStrings(), loadTable(), and saveTable(). The current data formats are csv, tsv and lua. I considered adding in a loadJSON() function, and still could at some point, but didn't think it made sense to DIY build a basic JSON parser or drop in something now. Could always be added later.

There's a few remaining color modes to add in: HSB, a noise function, some vertex functions, and then lots of debugging and refactoring. Notably, I have not tested on a Mac or Windows machine yet, or any computer other than my own! I also need to review how I'm implementing drawing from setup(). My current method is a bit dumb and draws twice. But ultimately, I'm feeling pretty good about the library so far.


![L5 code with an overlaid window of robots roaming, one has grabbed an orange box]({{"/images/log/L5-robots.webp" | absolute_url}} "L5 code with an overlaid window of robots roaming, one has grabbed an orange box")  
*L5 code with overlaid window of roaming robots, programmed in preliminary L5*  

I've also been making documentation and example programs. Here's the most complex one: a demonstration of OOP with robots that roam around and grab a box.

## 2025-07-21

I'm nearing completion on my initial goals for implementing a Processing API in Lua. I added a lot of functions today: save() (screenshotting the window), smooth(), noSmooth(), strokeCaps, strokeJoins, displayWidth and displayHeight, millis(), mouseWheel() and describe(). Describe() comes from from p5.js and I looked into some options and decided for my initial implementation and testing to render text to the console. I'll need to do more user testing of this of course. I also added in color tables, fixed up some color rendering, screen buffering, and some other details. I still have some typography, I/O file management (like importing and exporting text and data files) to do, as well as debugging my arc() graphics function.

## 2025-07-20

Added mouse events, did more debugging of the L5 library. Started adding documentation. I also did some audio editing of podcast episodes.

## 2025-07-17

It took two days, and I don't know if I solved it completely yet or not, as I'm afraid there may be more corner cases, but at least so far, I believe I have solved the screen flickering problems in the drawing library L5. I added back the ability to draw in any event function call (like keyPressed(), mousePressed(), etc). I also reset the screen transformation each frame. Finally, getting drawing functionality in the setup nearly broke me, but I hacked together a solution that I will definitely need to refactor later. This will all sound like psycho-babble, but I've put in a dozen hours attempting to fix these related bugs over the past 2 days as I re-wired how the underlying framework Love2d works. It's a testament to how well it's built that it is so flexible that I can sculpt it into another *language*. Now I'm back on trying to finish up the rest of the API. Once that's complete I'll make more example files, complete some small programs, then build out documentation. I'm feeling satisfied.

Here's the worst, most basic drawing program I can hack together in 60 seconds:

![L5 code with a drawing program that says It Works]({{"/images/log/L5-works.webp" | absolute_url}} "A hacked-together ugly drawing program that says It Works with the code for the program in the background")  
*L5 code with a drawing program, It Works!*  

Other things I added: the ability to color with html color codes, like "Rebecca Purple", "Dodger Blue", "Lawn Green". I also have a hexcode to RGB color converter. Big thanks to vga256 for pointing out some approaches and functionality, to Alexjgriffith for pointing out I can customize how love2d renders, and to Olivia (and Jack) for co-working with me. It was really fun to work on while having friends simultaneously working on their own programming projects and tools.

## 2025-07-15

I completed more of the Processing API for L5, all keyboard functions and vars. I still have to do the mouse functions/vars, typography, and color modes to feel like I'm finished the main draft of all functions. I built a basic version of pong, with an enemy AI. I hit a bit of a road block after implementing keyPressed(), keyTyped(), etc. Basically, I had modified love.run() so that there is persistence between draw frames, but now there is flickering after these event function calls. Love2d was designed so that the draw calls happen only in draw(). I think I am doubling the draw calls, causing the flickering. I tried multiple approaches to try to solve it but couldn't get a satisfactory solution yet.

## 2025-07-14

I implemented most of the Processing API in my Love2d/Lua hybrid. I corrected some function calls to be standardized with Processing. I fixed the screen reset and transformation between frames. I started to try to build in error handling but that remains to be finished. I added in more trigonometry functions and implemented angle modes. I corrected drawing stroke lines. After doing this I attempted to run a number of the example sketches on the p5.js website and found I have some bugs, such as when drawing an arc, that I'll have to fix. I created a TODO list. But still, I'm pretty happy with the progress so far.


![L5 pre-alpha with code and a rotating square]({{"/images/log/l5-rotating-square.webp" | absolute_url}} "A rotated blue square with red stroke and its code in background")  
*L5 code and rotating square*  

## 2025-07-13

I visited open studios at gr_und today. I liked the group exhibit. Good use of public infrastructure for presenting the work (via a borrowed fence/barrier). In the evening I attended the permacomputing meetup for a talk by [Chaline Bang](https://chalinebang.com/), speaking on her artworks, hosting servers on smartphones, and feminist server communities. She also ran a server on the phone and a borrowed router there and we connected in a shared drawing space on the local network. If you visit Chaline's website it says *"this website is hosted on a upcycled MacBook Air 2010 in my living room in Rotterdam."* I liked the talk a lot; I have some new ideas percolating. It was also great to meet a few folks I had been in touch with online previously, like Brendan and Roman.

In the evening I banged away at the L5 project building an unofficial version of *Processing in Lua*. I implemented constrain(), map(), time and date (millis(), day(), month(), year()), transform (push(), pop(), rotate(), translate(), scale()), max(), min(), dist(), text(), bezier(). 

## 2025-07-12

I did a tape loop workshop with [Sascha Bachmann](https://hand-music.com/)/HAND today at Saftladen. He's a great instructor. He started with a performance, then led us step by step through deconstructing tapes, and cutting together loops. He was very open to our experiments. For example I brought my microcassette recorders and tapes and he offered advice and help, though I found them a bit too small to nimbly work on with my fingers! The third section of the workshop was recording loops, minimizing gaps by blocking out the eraser playhead. I found this useful and am excited to do more studio manipulation of cassette field recordings. 

In the past couple days I saw a number of interesting exhibits, especially Ayoung Kim at Hamburger Banhof. Tonight I saw a sound art installation with Catalina in the Wasserturm water tower in Prenzlauer Berg. There was also the PLASMATRON performance by Felix Kubin. The sounds were crisp, fried, as well as saturated, with surprising twists and growing moving sections. The art projection (and one of the speakers) were on a rolling cart being pushed by a staff member, who pushed around the concentric rings, with the audience following in total darkness except for the black and white projection. Afterwards, I went next door to the other cavern and listened to a 360 sound art installation by Hanna Hartman that was equally strong.

In the late evening I kept working on L5, adding some math functions like different rounding functions, as well as a frame counter. I have a "punch card" of the Processing/p5 API that I'm trying to work through implementing. I'm perhaps more than halfway, but I also have to make some aesthetic and design choices. For example, I'm basically removing the normal update() function native to Love2d and instead having people code inside draw(), but that removes the consistency that update() has with deltatime in favor of being in line with the Processing work flow. I think that's the right approach since the goal is to make a Processing API in Lua, and there's always the regular Love2d for anyone that needs that, but it's something I need to document and note.

## 2025-07-09

I had a podcast interview with Cara today. It was a great interview. I'm excited to get back into podcasting again! I need to hone my editing chops however! In the evening I visited Synthlab at the FabLab Neukölln. I met friends of Jonah and showed off my synth and checked out the modules and other sound projects being built. It's an active group, that meets weekly. At home, I turned back to the L5 (Processing-in-Lua) project. I dumped out a bunch of the Processing and p5 and py.processing reference words into a text file. I had to make some judgement calls, at times throwing out things that I didn't think useful or practical to add. Anything that looked simple to implement in a minute or two I added, so I quickly added lots of things like frameRate(), deltaTime, resizeWindow(), clear(), TAU. I also listed many other things (typography/fonts, image loading/displaying, perlin noise, transforms, input/output, day/time) that I want to add to get to an alpha useful library and then start writing some programs in it.

## 2025-07-08

As is typical when I have other work unfinished, I procrastinated by working on another project: I am implementing a version of the Processing API graphics library with Lua using the Love2d library. I had had this idea years ago but decided it wasn't worth pursuing since Love has similar uses but different enough calls. However, the idea has been growing on me. I had kept it in check for fear it could spiral out into a lot of work, but I couldn't help myself and began to implement it. The library is about 216 lines now and I've implemented: 

```
setup(), draw(), mousePressed(), width, height, PI, HALF_PI, QUARTER_PI, TWO_PI, PIE, OPEN, CHORD, rect(), square(), ellipse(), circle(), quad(), triangle(), arc(), point(), line(), background(), fill(), rectMode(), ellipseMode(), noFill(), strokeWeight(), stroke(), random(). 
```

Here's an excerpt of a test program running:


![L5 pre-alpha with some of the code and a window of colored shapes]({{"/images/log/L5-pre-alpha.webp" | absolute_url}} "A first little test of L5, a processing-like graphics library in Lua showing some code and colored shapes in an inset window")  
*L5 code and colored shapes*  

This is a portion of some test code I wrote and a window showing it running. I tried to get my function calls as close to p5/processing API as I could. I'm currently using the working title L5. I think I will probably continue working on this a bit over the next few days as I'm enjoying it, but I do want to get back to finishing my archive and podcast episodes!

## 2025-07-04

I'm in Berlin now. I spent a few days prepping and arrived this afternoon. In the evening I visited the monthly creative coding meetup, and I met Raphael after following along with his work in Processing for many years. Tonight I also played around with writing a Processing-like API in Love2d. Just some small experiments.

## 2025-07-02

Saturday's performance went really well. We had a large audience and the performance was well-received. I recorded the concert, so I'll likely make an edit, possibly on its own or maybe some combination from the performance and the three recorded rehearsals. There was also photo and video documentation. We'll be looking for more venues to perform this again.

## 2025-06-25

Yesterday we did two rehearsals for Saturday's VENIS performance for the opening of [Shared Grounds](https://www.fluxfactory.org/event/opening-shared-grounds/) at the new Flux IV location of Flux Factory this coming Saturday. Actually, the performance will be held close by, at Hunter's Point South Kayak Ramp at 5pm. Both rehearsals went really well and I recorded them. I'll likely do some light editing and put them online at some point.

We're in a heat wave. Today I met up with artist and writer Robby Herbst and had such a great time connecting in-person together for the first time. Lots of things to talk about in LA and NYC in art and DIY community. 

In the afternoon I added lots of items to the growing archive site I'm working on. I also edited an *editor's note* section to add in my own commentary on items. I'll implement adding that to the page a bit later. 

I added in error checking and output to the build script and updated the README. The script is slightly more *expensive* now as a result, but I think is worth it. For example, this is a run showing one processing error and 41 successful page builds.

```
❯ ./build.sh

❌ Skipped 1 file(s) due to YAML parsing errors:
  - items/klik-n-play.md
    Error:
      YAML parse exception at line 8, column 0,
      while scanning a simple key:
      could not find expected ':'

✅ Successfully processed 41 file(s).
```

It's hard to pick favorites but today I particularly enjoy adding photographs from Kazimir Malevich's suprematist funeral, and a recording of Barry McGee's slideshow at BAMPFA in 2013. 

![Funeral Car for Kazimir Malevich with black square mounted on grill]({{"/images/log/funeral-car.webp" | absolute_url}} "A working draft of Cabinet of Curios mobile responsive view")  

*Funeral Car for Kazimir Malevich with black square mounted on grill, 1935*

> How would you describe what you do to a stranger?
> 
> I think maybe by doing rather than describing. We could start by cutting some holes in fences, throwing paint at billboards, and maybe have a swim in the ocean. *--Barry McGee interview, 2013, in [Acclaim Magazine](https://acclaimmag.com/art/interview-barry-mcgee-appearing-at-carbon-festival-2013/)*

## 2025-06-23

More work on the archive today. Performance rehearsal with Jemila in the afternoon. At one point struggled to handle feedback and distortion and trying to pin down the source in my fairly complex synth with wireless mic system! I was receiving J's mic and putting it out unprocessed, and simultaneously with delay/reverb as well as through the granular delay processing I use that is the heart of my setup. I needed to balance volume levels for these three. I ended up coming up with a different order for chaining modules together that was easier for me to balance the levels and really worked. So for voice it now looks like:

```
mic -> transmitter > input amp (ears)

input amp > delay/reverb (magneto)

input amp > processed vocals (beads) > delay/reverb (magneto)
```

This makes it a bit easier to handle. I can keep her original vocals with a bit of reverb higher and mix in just the right amount of processed vocals underneath it. 

In the evening I met up with friends for a party for Cata's birthday in Chinatown. More work on archive before bed, mostly inputting and processing items.

## 2025-06-22

Lots of progress on the Archive project today, including creating a github [repo](https://github.com/lee2sman/archive) to share the working code.

I wanted to document how pandoc and variables and templates work so I wrote up a [tutorial](https://leetusman.com/nosebook/pandoc-variables) for my nosebook blog. Then I built a template for the generated item pages and then a build script for the whole site. It uses a Lua filter to extract metadata.

![Responsive view - Cabinet of Curios mockup]({{"/images/log/cabinet.webp" | absolute_url}} "A working draft of Cabinet of Curios mobile responsive view")  
*mockup of a new archive page*  

This is a generated page from the static site generator I wrote. This landing page is populated with item pages in markdown with metadata entirely in the front matter.

I have a starting group of 8 pages up. Now I just need to screenshot the remaining 68 items and fill out their item pages with metadata. I also want to work on the design a little bit.

## 2025-06-19

I began working on a database site for an archive of articles, audio, books, pamphlets and other ephemera I've collected and that is stored on the Internet Archive, a collection of (currently) 76 items. These are a collection of out of print items or those that can't be found elsewhere, many open source or freely shared. My goal is to make my own custom and self-hosted collection page, that I can organize as I wish. The underlying items will remain stored on the Internet Archive as well as another collection backup. I am again building a static site, and I used CSS Grid as a base and began building out a template for the landing page and individual item pages. I used my knowledge gleaned and starter code I developed from my panblog project and work I had done during December Adventure 2023. This project grows out of an intention I set when the Internet Archive experienced DDOS attacks as well as my own desire to provide more of a curated space for a collection of texts and other ephemera that relate to my art practice and interests.

![A working draft of Cabinet of Curios]({{"/images/log/curios.webp" | absolute_url}} "A working draft of Cabinet of Curios")  

*A working draft of Cabinet of Curios (working title).*

Colors, final details of items, and even title of the archive collection are all in flux. Currently, hovering over a collection item highlights, changes background color and changes the image back to full color. I am designing with accessibility in mind. This means using color combos with high contrast and clearly labeled screen-readable text with semantic tag markup. The page is designed to be low bandwidth with lazy-loading of images, and a mobile-responsive view, all as a static site with no Javascript.

In the evening I attended WordHack (in its 11th year!) and was one of the presenters during the Open Projector. [I showed Quilt Poems](https://youtu.be/EGQEoXw47hE?si=EbM4UYYjrLoDMxEe&t=3302) and for the first time read some of them out loud! This was an audience of programmers that work with technology and poetry or writing - so an ideal audience for the work. I ended up distributing more copies of the Quilt Poems zine during the night.

## 2025-06-18

I sent off the code poetry piece Directions to Nick at Bad Quarto.

In the afternoon I worked at Flux. The wireless system and microphone had come in, so I set them up and tested them with Jemila. For our performance on June 28 Jemila is speaking vocals (while performing / dance) that I am processing through Mutable Instruments Beads (texture synthesizer). I had researched wireless systems a couple weeks ago and felt reasonably confident it would all work together nicely but there's nothing like realworld testing to confirm. We're using a Shure BLK wireless system. Rehearsal and audio testing went really well today and our system worked flawlessly. Afterwards I spent some time working on multitrack recording with the Zoom and added some [recording notes](https://leetusman.com/notes/music/recording.html) to my wiki. I set it up to record two pairs of stereo tracks, so I can record two voices, one going through the Golden Master, a combo of EQing, compression and mid/side processing with brickwall limiter. 

I worked a bit on scaffolding the site builder for my wiki, starting with a modified form of the [panblog site generator](https://tildegit.org/exquisitecorp/panblog). I had thought about trying to build the wiki with Jekyll but since I'm moving off that tech stack it makes more sense to keep it in house and keep using panblog.

## 2025-06-16

About a third of the Quilt Poems zines I made last week have been distributed, and I anticipate more will go to new homes if I attend WordHack later this week. In the past couple days I submitted some work to a new [Game Poems](https://www.gamepoems.org/) magazine. Today I worked on a small computational text work for Nick Montfort's [Bad Quarto](https://badquar.to/) press for an upcoming zine. As each writer/programmer has only a page I first brainstormed, then prototyped, and then did a bit of *sizecoding* to get the size down a little, but I didn't really do the full minification that would result in hard-to-read code. I was happy with the output, but I'm going to revisit in the next couple days and see if I want to make any changes.

Here's an example snippet of output from my current working version of the code, under the working title *Directions*:

```text
How to go home:
At the turn don't go right
At the turn do go left
At the intersection do go on
Stop when you get to it
```

In the evening there was a monthly Striped Light concert of experimental music. The whole night was great but one highlight was a quartet of synth, woodwinds, percussion kit with bagpipe. This unlikely combination produced unruly, funky but also compelling grooves and squonks. I loved it.

## 2025-06-13

 I finished printing and assembling the first run of the [Quilt Poems](https://leetusman.com/projects/quilt-poems/) chapbook zine in a small edition of 25. I'm looking forward to distributing them.

![assembling the quilt poems chapbook zine]({{"/images/log/quiltpoemschapbook.webp" | absolute_url}} "assembling the quilt poems chapbook zine")  

*zine assembly in action*

## 2025-06-10

Studio visit with Sam Gentle today. We shared our projects and gave each other feedback. This was super helpful. Sam generously shared aesthetic and conceptual critique of my in-progress Hyphenated project as well as spent time looking at code with me. Sam is a champion programmer and helped me figure out an alternate system for panning the background display using uv mapping. We also looked at some of the browser performance issues, and Sam gave excellent feedback on the project overall. I updated some of the modeling on the figures' lips, and tried an alternate texturing. I think I'm feeling close to getting to a final draft version of the piece soon.

## 2025-06-09

Writing up my conference paper took most of the day. I also updated my Pico-8 quilt program, encoding a number of new quilt patterns to the dataset.

<iframe src="https://www.lexaloffle.com/bbs/widget.php?pid=makeaquilt" allowfullscreen width="621" height="513" style="border:none; overflow:hidden"></iframe>

I'm also uploading one of the photo grids generated using my software and quilt pattern data. This piece is currently work in progress. This is a screenshot from a generated animation.

![drunkard's path photo grid screenshot]({{"/images/log/drunkardspath-grid.jpg" | absolute_url}} "a drunkard's path grid arrangement of images in a quilt-like pattern")  

In the evening I updated the Faircamp site I built to host my music and added the Flux 1 track mastered by bad diode. I'm pretty happy with how the music came out. I guess I'm soft launching the site and music now by linking to the site [ExquisiteCorp.institute](https://exquisitecorp.institute).

## 2025-06-08

![Pico-8 quilt]({{"/images/log/pico8quilt.gif" | absolute_url}})  

Today was the parade of the trains on the old BMT (present day Q line) of the subway. I went with Dan, L and their kids to ride subway trains from 1904, 1914 and 1960s. Incredible. In the evening I submitted and had accepted a pull request adding [build instructions](https://codeberg.org/simonrepp/faircamp/src/branch/main/BUILD.md#void-linux) for installing Faircamp on Void Linux. I worked on a new program to generate quilts using my quilt dataset I created previously for the photo grid and quilt poems projects from the past year. The program still has a bug I have to chase down, and the colors are a bit garish due to the constraints of Pico-8. I also added some patterning that vaguely resembles stitching but I may want to try some other variations, and potentially also consider working with the PAL mode of Pico-8 to see if it unlocks any better color options. I started writing up a big overview of the quilts I encoded as data and how I work with them to submit to a conference in England.

## 2025-06-07

I worked on some music, then contacted a Merveilles friend about mastering. Then I set up rust and cargo, downloaded [faircamp](https://simonrepp.com/faircamp/) and built a minimal static site for my music. I attended the NEW INC Demo 2025 and caught up with many friends. A huge group of us went out to dinner for Banh Mi. Wendy thought she had only just met me Wednesday but realized we've met long before. After dinner we went to the Demo party - dark club experience with hanging plants on the 5th floor of a skyscraper. Cyberpunk. Before bed I got back to work on the faircamp site - theming and editing and rebuilding. I also edited photos for potential use on the site.

## 2025-06-05

In the morning I met with Caleb and we chatted about our projects. Caleb is creating a number of personal and artist websites right now and we talked about static site generators, and about updating our Jekyll site for [Artists and Hackers](https://artistsandhackers.org). In one project he's working with someone with limited technical knowledge beyond HTML/CSS so a static site seems beyond their ability and they want to use Neocities. I suggested a Kenneth Goldsmith/UbuWeb-like approach. In [Duchamp Is My Lawyer](https://cup.columbia.edu/book/duchamp-is-my-lawyer/9780231186957/) (highly recommended), he talks about his web dev knowledge despite running [UbuWeb](https://ubuweb.com/) for almost 30 years. He mostly uses html with some minimal CSS and basically any time he needs to make a new page he copies an artwork/film/video/song page and pastes or writes in the new work's title and description and uploads the media and links to it. Caleb seemed convinced that would work for the project! Great.

Afterwards I headed to a performance rehearsal with Jemila at Chez Bushwick. My first time there. A really nice and affordable, large room for dance or performance, in a warehouse in East Williamsburg. Jemila was costumed and we did a run through of the score. Afterwards we spent some time researching wireless mic and transmitter/receiver options since Jemila will be doing vocals during the performance that I'll be live processing through the synth. We settled on a fairly straightforward Shure system with an earset mic. Mic → transmitter pack → receiver → Mutable Instruments Ears. I may need a mic-preamplifier too. In the evening I had a studio visit with Dan L., checking out some of his work, which uses and builds upon his [Community Game Development Toolkit](https://danielp73.github.io/Community-Game-Development-Toolkit/). His current project combines photographs with 2d images, and we talked about billboarding effects, and looked at various other artists that combine *handmade* items from the world in this DIY aesthetic. More than a coincidence that we both work in this way, and both love games but have little patience for many 3d games. Later I spent time editing my audio recordings from synth recorded earlier in the week. Oh, and I purchased [Reaper](https://www.reaper.fm/), as it felt like I've evaluated it, I really like it, and now it's time to buy it.

## 2025-06-03

Today I worked on music at the music studio at Flux Factory. I did some sound tests with Jemila for our upcoming performance at the end of the month. I recorded our rehearsal and afterward I recorded for another thirty minutes. I'm really pleased with my sound lately and want to put more of my music online. I planned to do some studio edits at home on Reaper DAW but needed a bit more knowledge to use all of the features I needed so I watched tutorials on envelope automation in Reaper. I also have been under-using the Endorphines Golden Master on my modular, an end of chain module like a channel strip (EQ, compression, limiter, sidechain). I need to do some more tests but I am thinking I may want to do my end-of-chain mastering 'in the box' there, and just use Reaper for studio edits like moving around sections, fades and the like. I could also add in my microcassette or my 4track into the chain for some extra warmth.

## 2025-06-02

![Riso cover test]({{"/images/log/riso.webp" | absolute_url}})  

I created a short workshop [Intro to Making Games (with Pico-8)](https://leetusman.com/notes/programming/pico8/) that I taught today to a class of rising sophomores at my school. Afterward I worked with the risograph printer in our Media Art Lab, trying to mock up a zine of my generative quilt poems. Although I like the image I wasn't super satisfied with the cover print. The default paper stock didn't seem to help the print to really pop. I also think that rather than overlay text I should create a duotone to get that textured riso print imperfections. I'll have to do more tests. It might be that a different font and size could help resolve it.

## 2025-05-30

I spent the day working with my parents scanning in old family photographs from the early 1900s up to the 1990s. Several online friends recommended the Epson V600, so we purchased a newly refurbished one. It comes with a CDrom of its firmware and scanner software. I see that imagescan v3 for Epson is available in the Void package repos, but my parents have a Mac. I looked on the epson.com site but couldn't find the software for download, but when checking epson.ca (the Canadian site), bingo. I downloaded and updated their firmware and installed Epson Scan 2 on their macbook. The software worked well. It allows you to place up to 5 or 6 photos on the scanner bed and the software individually separates them out to separate image files and allows you to quickly rotate if needed before doing the final scan. I also purchased a lens cleaner, dust blower and microfiber cloth for a couple bucks at the nearby Microcenter and used these periodically to clean the scan bed. We scanned a couple hundred photos and put them in organized directories. We were able to scan almost everything. Next I'll purchase some archival boxes and paper to send to my parents to rewrap their photos and protect them. Some of these images might find their way to art projects but mostly it's just another way to 'preserve' and share these photos to other family members.

## 2025-05-29

I spent part of the day exporting my remaining Glitch.com project pages since they've notified us they're shutting down hosting within the next 6 weeks. A Glitch employee built a python exporting script. I had a few errors and they kindly offered a patch. So I was able to export about 237 of my 251 repos. The exported projects don't rewrite Glitch's image CDN links so I'll need to write a regex to change the CDN path to *glitch-assets/imagename.png* or manually check individual project sites and update.

## 2025-05-28

I exported the [Open Source Tools for Artists](https://leetusman.com/open-source-tools-for-artists/) from Glitch.com (shutting down in a month!) and transferred it to GitHub hosting. This was fairly straightforward as a static site save for Glitch's convoluted image CDN process meant I had to manually export the image files one by one. I also built a [project page](https://leetusman.com/projects/open-source-artists/) for my website portfolio.

## 2025-05-22

I read Mozilla's announcement today they are winding down Pocket, which I've used off and on since 2016 as a read-it-later article service. It was especially convenient on my phone on the subway, or to read on my Kobo e-ink reader since it was integrated. I've already created [Bookmobile](https://tildegit.org/exquisitecorp/bookmobile/) in the past, and today with some help from the internet I added on an additional script that can bulk download articles from one's exported Pocket list of articles. Thanks to Darius for a simple parsing suggestion. RIP Pocket. [Full writeup](https://leetusman.com/nosebook/rip-pocket) on the blog.

## 2025-05-21

![Lil Dungeon]({{"/images/log/lildungeon.webp" | absolute_url}})  

Thanks again to @pancelor for their comment on [lil dungeon](https://itch.io/jam/tweettweetjam-10/rate/3557507) I was able to get the code down to 439 characters, though with the spawning error still present. When a new level is spawned the monsters get to move once before the player, which means a player could die when a new level is spawned. I tried some simple things to debug but struggled a bit with the obfuscated code and GOTOs to get a fully working system in minimal code. Will have to revisit another time. But still, I'm happy with where I've gotten:

```lua
r,x,y,f=rnd,3,3,1::i::e={}a=r(9)\1b=r(8)\1for i=1,5do repeat g=r(8)\1v=r(8)\1until g-x|v-y!=0e[i]={x=g,y=v}end::m::d=16for y=0,114,d do for x=0,114,d do
fillp(r(♥))rectfill(x,y,x+d,y+d,2)end end
?"▒",a*d+4,b*d+5,9
?"🐱",x*d+4,y*d+5
?f,2,2,6
for j in all(e)do 
z=r(4)\1/4j.x+=cos(z)j.y+=sin(z)?"😐",j.x*d+4,j.y*d+5,8
if(j.x==x and j.y==y)stop()
if(x==a and y==b)f+=1goto i
end 
repeat flip()v=btnp()until v>0
x+=v\2%2-v%2y+=v\8%2-v\4%2goto m
```

This reminds me: maybe I should have a type-in games jam in Pico-8 and p5.js?

## 2025-05-20

Since my last log entry I've been somewhat busy. At school I hosted an algorave with my students in Drawing, Moving and Seeing with Code. It went well. I opened the show and made interstitial music between the acts. We finished the semester and I'm now working on the podcast, practicing for a performance on modular synth next month, and prepping for sabbatical. I delved a bit into working in Reaper DAW on audio production for the first time. I like it. I'm just making a rough audio mix from a practice session that will lead up to my performance next month. I want to put more rough mixes, one-offs, performance recordings online. To that end, I purchase a [domain](https://exquisitecorp.institute/) and will start building out site content there.

I participated in [TweetTweetJam 10](https://itch.io/jam/tweettweetjam-10), where the goal is to produce a game in 500 characters or less. I created a dungeon crawler-esque chaser game [Lil Dungeon](https://itch.io/jam/tweettweetjam-10/rate/3557507). I created a first version, then with some online comments that helped me reduce the code, I later reduced the size on further iterations. As of tonight I still feel like there's at least one more version I'll produce to fix the monster spawning code.

In any case, it was fun making this tiny game in Pico-8, and especially gratifying that it's compelling enough not just for me but a raft of people that have contacted me or commented on the game to let me know they are playing it.

## 2025-04-06

Head down on school work the past few weeks, and had a week of illness with fever so little work then. Visited MOMA, Brooklyn Historical Society, and lots of bike riding as the spring weather improves lately.

I worked on a small [Chezz simulator](https://notapipe.itch.io/chezz-simulator) game for the Merveilles [Flickjam](https://itch.io/jam/flickjam-2025/entries) 2025.

![Chezz Simulator screenshot]({{"/images/log/chezz.png" | absolute_url}})  

## 2025-03-22

Despite the annoyance of losing some work (see previous post), it wasn't so bad to recreate what I had lost, and then build some more. I put back in almost everything. At this point, it's been a week since the workshop and I've posted the results, my workshop, games and programs [in a post about BASIC Games](https://leetusman.com/nosebook/basic-games) up on the blog. I just wanted to mention one minor drawback of using Yabasic: I haven't found a working online Yabasic compiler that consistently runs the games correctly (specifically inkey$), so it means the games will have to be run and compiled on the actual computer.

Now I'm prepping for my performance Sunday March 23 at The Living Gallery in Brooklyn.

## 2025-03-13

First the first time in years I lost some work! I accidentally overwrote the Cyberhoss game file and since I hadn't pushed it to GitHub or backed up in a couple days I lost the last few days of changes, including that previously mentioned AI player. Ugh. I'll try to recreate later? In the meantime, I wasn't feeling like going back and trying to redo it. I made a different game, based on Dope Wars/Star Trader/Drug Wars that I called Catanite. It was meant to be a minimal buying/selling market game, where you buy / sell resources from Settlers of Catan but my 'minimal' version took me a couple hours and is 250 lines of code, so not as minimal perhaps as I would have hoped. But I did try to code it with very basic programming skills, for example I didn't use arrays (dim in Yabasic) and only used global vars.

## 2025-03-10

More work on Cyberhoss. I've added in an enemy AI as well as some mechanics to balance the game better. Basically, the top hoss odds are always 1X. Meddling with any hoss affects the probability that it will stumble during a race, in proportion to the strength of meddling. I'm not sure if I should build in a mechanic where meddling could potentially get the player caught. I think I may want to add a leaderboard later as well. But so far the game is now playable and fun. It's in a good state and I'd be happy to present this, which I will do after the upcoming Electronic Faire conference I'm presenting at this coming Friday.

![Cyberhoss AI]({{"/images/log/cyberhoss-ai.webp" | absolute_url}})  

## 2025-03-09

Some more work today on the Cyberhoss game. I have a working demo for one player. I think I want to add in some AI players as well, then run some playtesting with other players.

![Cyberhoss win]({{"/images/log/cyberhoss-win.png" | absolute_url}})  

## 2025-03-08

The [upcoming workshop](https://charlesstudy.temple.edu/event/14200746) I'm teaching at the [Electronics Faire](https://sites.temple.edu/efaire/) at Temple University's Charles Libary is a week away. I began work on another game, a clone or demake of the [Quibble Race](https://ufo50.miraheze.org/wiki/Quibble_Race) game from UFO 50. I think I've made a pretty good working version. Just need some tweaks to wrap up and I think it's already pretty fun. I'm thinking it would be useful to make one more really simple game demo in prep for the workshop, something that absolute beginners can build off of. Once the workshop occurs I'll make my game source code available online.

![Cyberhoss]({{"/images/log/cyberhoss.webp" | absolute_url}})  

## 2025-02-28

For the Hyphenated project I ran a test with the [p5.glitch library](https://github.com/ffd8/p5.glitch), seeing if I could put it to use glitching out the image textures on my character's faces. I made a simple [proof of concept](https://editor.p5js.org/2sman/sketches/73LUdJxaA) 3d ellipsoid blob but it kept crashing for me. I opened an issue to ask about performance savings in webgl and based on the answer there decided to try in Chrome, where it didn't crash for me in laptop but it still crashed on phone. Based on this, I think I'll probably proceed without the library and instead manually switch out glitch textures that I build up as image file textures.

## 2025-02-24

I tried out the [Openshot](https://www.openshot.org/) open source video editor to make an excerpt from one of my fall performances and [uploaded](https://youtu.be/QRva9XkAZN4) it to YouTube.

<iframe width="560" height="315" src="https://www.youtube.com/embed/QRva9XkAZN4?si=sozIDLTA9wsaGI9i" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

This is from a performance at Flux Factory on Governor's Island in September for the Emergent Behavior performance, accompanying the exhibition [Spiritual Machines](https://spiritualmachines.neocities.org/).

## 2025-02-23

Today I finished writing Gobi in Yabasic, to be used in the [upcoming workshop](https://charlesstudy.temple.edu/event/14200746) I'm teaching at the [Electronics Faire](https://sites.temple.edu/efaire/) at Temple University's Charles Libary March 14. It's an Oregon Trail-like adventure game, and I've previously [published a web version](https://notapipe.itch.io/gobi) that I wrote for the web, with photographs for the graphics. It helped to look up my previous algorithms, like how much food is consumed per turn in the desert, how much resting improves the camel health, water and food replenished at an oasis, etc, but I did make some tweaks. I enjoyed the process of writing it in BASIC. 

![Gobi text adventure game]({{"/images/log/gobi.jpg" | absolute_url}})  
*Gobi text adventure game in Yabasic, showing one of many ways to die. This is running in CoolRetroTerm terminal emulator.*

One thing that made this easier than The Oregon Trail that I was working on previously was that I was...using subroutines instead of GOTO statements. This makes it so much easier to get to the right section to fix things. In the updated [Basic Computer Games](https://github.com/coding-horror/basic-computer-games?tab=readme-ov-file#project-goals) repo where participants port the old games to *modern* conventions one of the guidelines is:

> Please DO update for modern coding conventions. Support uppercase and lowercase. Use structured programming. Use subroutines. Try to be an example of good, modern coding practices!

Going back to the original OREGON has been difficult because I have to figure out the control flow. Hamurabi was short enough and I was lucky enough that keeping the GOTO statements in *just worked.* But Oregon's increased complexity means I still have to put more work into it.

## 2025-02-09

Today I worked on the version of the game [The Oregon Trail](https://github.com/clintmoyer/oregon-trail/blob/master/oregon.bas) from 1978. It's a trip to work with code written years before I was born. I made some basic (sorry) changes to get it to run in the modern [Yabasic](http://2484.de/yabasic/), which is a maintained free and open source BASIC interpreter that is at least 25 years old, and runs on Unix-like systems and Windows. First I convert rnd() to ran() (could have just added a subroutine call, but find/replace was just as easy). Then I add in goto and endifs explicitly since that's required in Yabasic. Last I convert semicolons to commas. And with mostly just that, The Oregon Trail runs. 

Then I notice the passing strangers in the game never attack, so there's possibly some work to do there. I also try to "hunt" and the program crashes. I decide to tackle hunting, and through that, I went on a deep dive. The 1978 program calls CLK(0) probably to get the time. I check the original 1980 Microsoft BASIC reference manuals but can't find CLK() listed. This must be a different BASIC? But I thought it was MS BASIC? In any case, there are LOTS of code comments in the original code, and despite the much-maligned GOTOs, the code is not bad to follow. So I isolate out the HUNT code into a separate program to try to debug. First I see that a player self-selects their skill level at hunting. Then I realize there is an array of words ("BLAM","POW", etc) and a prompt that asks the player to type one of these selected randomly, by a certain time. With that, I devise my own hunt program. Two hours later I got a fully functioning hunt program and with an added minor improvement that I check the user typed the word correctly, which was not included in the original as far as I can tell. But at the cost that my version takes many more lines of code. I have much more detailed info on this and source code on my [blog](https://leetusman.com/nosebook/oregon-comments). 

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

![Mockup of a riso-printed cover]({{"/images/log/riso-cover-mock.webp" | absolute_url}})  

![Mockup of a riso-printed sheet page]({{"/images/log/quiltpoems-riso-mock.webp" | absolute_url}})  

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

