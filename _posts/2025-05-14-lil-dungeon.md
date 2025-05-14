---
layout: post
title: Programming a lil dungeon 👹🕹️
categories: [open source, creative code, programming]
---

![Lil Dungeon]({{"/images/log/lildungeon.jpg" | absolute_url}})  

=> [Lil Dungeon on itch.io](https://notapipe.itch.io/lildungeon)

This is a game created for the TweetTweetJam 10 to make a game in 500 characters of code or less. I used 499 characters.

This was my first attempt at sizecoding in Pico-8/Lua and I found this quite a challenge. I attempted to balance my ambition (make a dungeon crawler) within the constraints. That said, the game is closer to something like the old [Chase / Daleks / Robots game](https://en.wikipedia.org/wiki/Chase_(video_game)) than a true roguelike.


## Goal

You are a cat descending levels in the dungeon. Try to reach the stairs ▒ (yellow cross-hatch symbol) to go down one level. You will die if you get eaten by any of the red demons. See how many levels of the dungeon you can descend before getting eaten! That's it!

Your only control is the arrow keys. Reload the page to begin a new game.

## High Scores

**15 and above**: God-level.

**10 and above**: True catpunk.

**5 - 10**: Not bad, kittypunk.

**Less than 5**: You're not too good at this.

## Code

Current code as of 2025-05-14.

```lua
r,x,y,f=rnd,3,3,1function _init()
e={}a=l()b=l()
for i=1,5do e[i]={x=l(),y=l()}end m()end
function _draw()v=btnp()
if(v==2)x+=1;m()
if(v==1)x-=1;m()
if(v==4)y-=1;m()
if(v==8)y+=1;m()end function m()c=114;d=16for y=0,c,d do for x=0,c,d do
fillp(r(9999))rectfill(x,y,x+d,y+d,2)end end
?"▒",a*d+4,b*d+5,9
?"🐱",x*d+4,y*d+5
?f,2,2,3
for j in all(e)do
j.x+=(r(3)-1)\1
j.y+=(r(3)-1)\1
?"😐",j.x*d+4,j.y*d+5,8
if(j.x==x and j.y==y)f=1;stop()
if(x==a and y==b)f+=1;_init()
end end function l()return r(8)\1end
```

## Comments/questions

If you have any further sizecoding suggestions, or better yet, some solutions to the following bugs/unfair things that would keep me within 500 characters, let me know!

## known bugs/limitations

* The monster spawner is not very smart. When it creates a new level a monster could spawn on top of you, killing you. I wasn't able to fit a correction to this in within the strict limits
* Technically the monsters can walk offscreen and then back on, so they could kill you if you're on the outer ledge and they walk into you
* The monsters can move 8 directions orthogonally while the player cannot. Again, this was a limitation based on my inability to fit in an either/or X/Y movement mechanism for the monster within the code length limitations.
* The left-behind screen residue/artifacts are a result of not redrawing the screen background, and I think are both visually interesting and make the game slightly harder. I like it!

