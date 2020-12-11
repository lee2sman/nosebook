---
layout: post
title: "Beginner's mind: Programming and Patching and Synthesizing"
categories: programming art teaching tools
---

topics: generative music, beginning programming, code sketching

I've been playing modular synth now for almost 2 years, though it's really only in the past 3 or 4 months that it's become a daily studio practice for me. Meanwhile, for the past several years I've mainted a daily code sketching practice, where I often (sometimes daily, sometimes.....not) make short little projects: games, generative visual art, strange visualizations, collage via code, and the like.

![mini modular]({{"/images/synth.jpg" | absolute_url}})  
*Bless this mess*

I've made experimental music in fits and starts for the past 20 years or so. I've been programming for perhaps the past five or six.

One of the reasons I got into playing modular synth is to enter the music hardware world, as opposed to using software. I wanted to make intuitive changes by twirling knobs, hitting buttons. I wanted to hit a switch and things turned on and away I go. It's not quite that simple. It's taken me a good year and a half to fully feel like I am comfortable with the basics of control voltage, which operates very differently from pure audio synthesis. And now that I'm comfortable, I still want to say that there's a lot that's still magical. As I teach intro programming classes at uni, I can tell for many beginner students that there are moments where something works, or doesn't work, and the students can't say exactly why. Often this comes down to syntax issues, though not always. I'm sometimes in a similar place with my modular, and for this reason, I would definitely say I'm not an expert. And in fact, although I do a lot of teaching, I'd probably want maybe 6 more months under my belt to feel like I'm ready to publicly teach a synthesis class.

But the process of creating music on my eurorack almost daily for the past 3 months has paid off, and I've made rapid improvements to my music output as well as my understanding and my studio workflow. I have a flexible and intuitive ability to rapidly make music and little experiments now, so things have almost switched to where I'm more comfortable on the synth and wish coding could become even more like this. When you do a few lines of experimental code sketching, you MAY create something beautiful. But more than likely, it may just not run. You start with debugging. In hardware synthesis, when you turn on and plug in a cable or two, even if it's not beautiful, it's something! There's sound. And you can immediately patch in a cable and filter the sound or modulate it for example.

We can try to replicate this by having prebuilt libraries, functions (aka "base code") to be used in our code sketches. A modular synth approach to creative coding can be found in Max/MSP/Jitter for example, or VVVV, or TouchDesigner, or PureData, which are all node-based 'patchable' environments for creating interactive art and music. Max's roots go back almost 30 years, and were originally audio patching only, though includes visual tools. VVVV is a younger development environment, which has taken hold in Europe. TouchDesigner is a more commercial tool, also patchable, used for stage, concert, installations, or corporate 'activations'. 

Glitch.com is a current corporate website with development environment, the ability to share and collaborate on code and to deploy to a server. Though not an art and music-focused environment per se, it can be used for creative coding, by using the p5.js library, for example with Ted Davis's [p5live](https://www.teddavis.org/p5live/), or Olivia Jack's [Hydra](https://hydra-editor.glitch.me/) for livecoding as another example. I mention Glitch.com because one thing it does well is support the idea of starting with base code. You can browse someone else's or your own past hosted project, then click remix to make a new copy of this running program that you can then modify and see updates live in the browser. It's a nice way to work. It's still not quite as instant as turning a knob in a modular synth, but it does speed up a bit our previous process of write code, save, wait for server to notice, re-render/display.

To be honest, I haven't put enough time into Max to see if it is a good translation of hardware synthesizers into a soft similar coding environment. When I try to use Max, I simply don't know all the possible commands that are available, and how to plug them together. It's not quite as visually obvious to me what to do the way a synth is when laid out in front of me. But people do share their Max patches, and you can copy and paste them in. Maybe it's time for me to become a student and learn the basics. Then I imagine I should try out PD (PureData), its open-source cousin. I've found it fairly intuitive to jump between the basics of object-oriented programming languages. Perhaps jumping between these two won't be that difficult either.

To wrap up here: 

Hardware where you have the full ecosystem laid out entirely in front of you can be overwhelming but at least gives you the full map of potentialities. There is a built-in "starter" when working with hardware that is nice to try replicate when working in code. All of these things take time to learn; you're not an expert when you first start. But expertise is not necessarily the goal at the beginning: developing some kind of ongoing practice of expression is the goal. From this practice gradually over time one develops the intuition that's needed to be a better practitioner and creator.

