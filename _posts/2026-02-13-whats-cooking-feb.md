---
layout: post
title: "What's cooking with L5? New events, documentation and printToScreen - February 2026"
categories: [open source, creative code, programming, permacomputing, L5]
---

![Computational poetry showing stripes and text responding to ICE raids (compressed gif animation excerpt)]({{"/images/l5-ice.gif" | absolute_url}} "Computational poetry showing stripes and text responding to ICE raids - compressed gif animation excerpt")  
*Computational poetry showing stripes and text responding to ICE raids, code in L5 (animation has been shortened, excerpted, color reduced and compressed)*

I'm not sure if I'll do a post every month on [L5](https://l5lua.org), the creative coding library I initiated summer/fall 2025 and that is now out in an alpha version, but there's enough activity happening that it seems like a good idea to capture work and ideas down somewhere to track progress.

Since I last wrote about the [first L5 contributors meeting](https://leetusman.com/nosebook/L5-meetup) we've now held a second meeting, though this one was rolled into the first [Permacomputing NYC](https://nyc.permacomputing.net) meetup, with one part of it being about L5. We had 20 people show up, discussed permacomputing, which was a spirited conversation, and then had a presentation on [Lichen-Markdown](https://lichen.commoninternet.net/) by Max Fowler, followed by my own presentation on L5. Also I want to note that [L5 now has a page on the Permacomputing Wiki](https://permacomputing.net/L5/). 

Since last month's meetup, L5 now has:

* [Step by step install guides for Mac, Windows and Linux](https://l5lua.org/download/)
* a new [printToScreen()](https://l5lua.org/reference/printToScreen/) function
* updated [Getting Started](https://l5lua.org/getting-started/) instructions for your first steps after installing L5 and Love2d
* new [Contributing to L5](https://l5lua.org/contributing/) guide (thanks to Jessica Garson for contributing this!)
* updated [L5 Starter](https://l5lua.org/download/#l5-starter-project-recommended) project that is more beginner-friendly (thanks to the entire group that contributed ideas to this at the last contributors meetup)
* there were also a few contributed [pull requests to the L5 website](https://github.com/L5lua/L5-website/pulls?q=is%3Apr+is%3Aclosed) that fixed typos, added links, corrected code examples

This is so exciting, that L5 is starting to grow a community around it!

In the coming month or two there are a few events where I'll be presenting L5. There is going to be an L5 workshop at the next [CCFest 2026](https://ccfest.rocks/) on March 21, a talk I'll give on L5 for the next [Wordhack](https://withfriends.events/event/IfGKzXyY/wordhack-feat-lee-tusman-jackie-liu-and-game-poems-magazine/) at Brooklyn's own Wonderville on February 19, and an in-person workshop with L5 at the [Algorithmic Art Assembly](https://aaassembly.org/) at Grey Area in San Francisco on March 26.

## New feature: printToScreen()

![L5 code in the Neovim editor on left and the running code sketch in the center shows drawing lines based on mouse and an onscreen print() output that scrolls]({{"/images/printToScreen-example.gif" | absolute_url}} "Example of printToScreen function in a sketch and rendering print output to the window")  
*L5 code in the Neovim editor on left and the running code sketch in the center showing drawing lines based on mouse position and an onscreen print output that scrolls. Animation is an excerpt of running program, with compressed colors and reduced graphical fidelity/detail*

As mentioned, L5 now ships with a new function **[printToScreen()](https://l5lua.org/reference/printToScreen/)**. Simply add that function to your code somewhere, like in setup(), and then print() output will display onscreen. This allows someone programming in L5 to simply drag-and-drop their program folder onto the Love icon to run it and to see debugging output.

This is a divergence in some ways from Processing and p5.js. Processing is run from the Processing Development Environment (PDE). It has a console for printing debugging output with print() and error messages, on the bottom of the IDE. p5.js can be run directly in a browser through a local server, or hosted online, but the majority of people (I believe) and most beginners are running it through the online [web editor](https://editor.p5js.org). This likewise includes a console that displays error messages and the output of print statements.

L5 is implemented in the Love2d framework and Lua language. To run a program written in L5, one needs to install Love2d, and use a code editor/IDE of one's own choice. For beginners, to see debugging output of the print() function was a higher barrier because it required running one's program from the command line just to see your output.

At the first L5 contributors meetup I had watched experienced programmers who don't use the command line struggle to use it. I had hoped that it would be possible to implement a new *L5 mode* in the Processing PDE for specifically these programmers, but there is still debugging happening in modes, and there will be a series of work to be done to complete this. What's more, not everyone will want to use it. Maybe they are more used to SublimeText or VS Code or other IDEs for example. Through conversation with [Jessica Garson](https://github.com/jessicagarson), who wrote the updated Contributors guide, I showed off how Pico-8 includes all print debugger output onscreen and that we could take that approach with L5. The result is that a programmer that does not use the command line could simply drag-and-drop their L5 sketch folder onto Love to launch it, and see the output of their print() debugging in their sketch window. It took me a couple days of implementing, testing and refining, but the end result is exactly this.

To support print() in the draw(), there is a buffer on the backend that 'scrolls' the print output and displays as many lines of print as will fit onscreen. You can also optionally specify a default onscreen font size for the print output. And all this just from adding **printToScreen()** somewhere in your sketch, typically in the setup().

### What's next

There are still bugs in L5, opportunities for optimizations, fixes and additions to be implemented for drawing custom shapes and bezier curves, as well as need for more tutorials and examples. L5 is part of a proposal by Processing for Google Summer of Code - if accepted it may be possible to have a paid fellow work on L5 this summer. There are also two usability studies being conducted on L5 this spring by University of Washington's Human Centered Design and Engineering.

Other areas of opportunity that could use some work and help, if contributors are interested, are implementing hot-reloading (called 'autorefresh' mode in the p5.js web editor), adding a testing suite, adding documentation for VS Code installation of L5, potentially even forking the Love2d extension for VS code to make a native L5 extension, and further debugging of L5 in general.

Check the [Contributors guide](https://l5lua.org/contributing/), the [issues list for L5](https://github.com/l5lua/l5/issues), and the [issues list for the L5 website](https://github.com/l5lua/L5-website/issues) for more opportunities to get involved.
