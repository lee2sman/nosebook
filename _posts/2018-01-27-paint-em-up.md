---
layout: post
title:  "Paint-Em-Up digital drawing software"
date:   2017-11-21 18:40:05 -0800
categories: programming jas
---

# Paint-Em-Up

*UPDATE: 2018-02-04 I made a Paint-Em-Up 2player digital painting software/game thing, and presented it at Coaxial Arts. A [demo](http://lee2sman.github.io/paint-em-up) is up. Arrow keys and WASD are controls.*

![painting screenshot]]({{"/images/painting-shot.jpg" | absolute_url}})

# Painting Programs && code

* [Extending TuxPaint](http://www.tuxpaint.org/docs/html/EXTENDING.html)

# Digital Painting

I'm working with [J.A.S.](http://jas.life) to make (build?) some new painting performance projects - games, perforamnce tools, hardware.

Just stumbled across the old [Action Painting](https://ianmaclarty.itch.io/action-painting) game and [Action Painting Pro](http://ianmaclarty.com/action-painting-pro/). The v1 is better.

I made a painting interactive software thing, even less game-like though maybe. Demo is [here](http://alpha.editor.p5js.org/full/HyQfnq_s-) and the code [here](http://alpha.editor.p5js.org/2sman/sketches/HyQfnq_s-). I'm gonna work and use it as a starter code to make more stuff.

# Variations

* Roguelike
* no paintbrush/canvas control - you can only alter sliders for color, size, speed of bot-brush - everything controlled with sliders
* Vimpaint
* Bot-painter

# Multikeypress

Need multiple keypresses to be recognized at once? ```function keyPressed()``` is not your friend as it has a limitation to how many keys can be identified. keyIsDown() can check if a key is currently down.

Example

```
function draw(){
    if (keyIsDown(DOWN_ARROW)) {
    	y += 5;
    }
    if (keyIsDown(UP_ARROW)) {
    	y -= 5;
    }
    if (keyIsDown(RIGHT_ARROW)) {
    	x += 5;
    }
    if (keyIsDown(LEFT_ARROW)) {
    	x -= 5;
    }
}
```
