---
layout: post
title:  "Es6 basic - not even overview"
date:   2017-11-21 18:40:05 -0800
categories: programming
---

## ES6 - an underview

* ES6 came out in 2015 - stands for ECMAScript 2015

### let VS var

* [let vs var](https://www.youtube.com/watch?v=q8SHaDQdul0) tutorial on Coding Train
* OLD: ```var x = 100;```
* NEW: ```let x = 100;```
* OR:  ```(const x = 100;)```

* Why difference?
* var uses *function* scope
* let uses *block* scope
* prevents problems related to hoisting variables (where they are actually silently declared at beginning of function blocks)

## Const

* [const](https://www.youtube.com/watch?v=2iLVFyYwyRA) tutorial video on Coding Train
* use to manage memory efficiently or set values permanently.
* can only be used for variables whose value will *never* change
* also is block-scope

## Anonymous Functions with Arrow syntax

```
button.mousePressed(changeBackground);

function changeBackground() {
	background(random(255));
}

//simplifies

button.mousePressed(function button()) {
	background(random(255));
}

//simplifies

button.mousePressed( () => {
	background(random(255));
}

//brackets are optional so can be simplified

button.mousePressed(() => background(random(255)));

```

# Prototypes
