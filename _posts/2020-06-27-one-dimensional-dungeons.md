---
layout: post
title:  "One-Dimensional Dungeons"
categories: programming
---

![One Dim Dungeon]({{'/images/roguelike/1dimdungeon.jpg' | absolute_url }})  

Over the past few days I built my first working roguelike game.

A [roguelike](https://en.wikipedia.org/wiki/Roguelike) is a specific genre of oldschool game. Going on about 40 years as a genre, they are distinguished by turn-based gameplay instead of continuous action; simple tile graphics or often ASCII text as stand-in for features; algorithmically-generated increasingly-difficult levels, enemies, objects and other gameplay elements; no ability to save your status, which is known as permadeath. There are some other associated themes and gameplay mechanics as well, the essentialness of which is often hotly (and perhaps unneccesarily) debated by fans.

I think at this point I've tried to make a roguelike game at least 5 or 6 times. Each time I've tended to start from scratch and try to implement each feature of this genre by hand. My [past](http://leetusman.com/everyday/81/) [attempts](http://leetusman.com/everyday/21/) [have](http://leetusman.com/everyday/19/) been very simple, and not quite compelling gameplay.

![hellth]({{'/images/roguelike/hellth.gif' | absolute_url }})  
*hellth, a mini roguelike I made in p5.js*  

To be honest, my current game One Dim Dungeon is not the most compelling game. It certainly wouldn't be as well-loved by someone other than me. But there's some surprise and delight on my end, and a sense of triumph of creating my first working roguelike prototype, and doing it on my own from scratch, in Javascript.

Creating a complete roguelike without a pre-made library or game engine is a layer of difficulty not recommended! I've attended [Roguelike Celebration](https://roguelike.club/), and I'm aware that [Entity Component Systems](http://www.roguebasin.com/index.php?title=Entity_Component_System) are *de riguer*, and I'd love to have made that, but instead I built improvisationally, without a complete understanding of all of the systems and mechanics, which produced significant *anti-patterns*. This means I have an anti-robust system and all of the bugs and spaghetti code that entails. Now that I have a baseline I'm looking forward to adapting this start and turning it into such a system eventually. Or perhaps I'll start again some point in the future!

As opposed to 99% of other roguelikes, I made a strange choice: this is a 1-dimensional roguelike. You can only go forward and back. Why? It's easier to implement than having to procedurally build out and manage an entire 2d grid level, building out rooms procedurally. I thought I'd simplify with constraint in order to allow me to concentrate on essential mechanics that still felt within the domain of the genre.

Here are some of my game mechanics:

#### procedurally generated floors

The map is algorithmically generated anew each game, and each time you descend the stairs (<) to a new floor. I chose some magic number percentages so that each turn there is a certain percent chance that a monster could be spawned along an edge or gold could be spawned in the dungeon. I've adopted the full set of lowercase and uppercase letters as standins for monsters. Their power is determined when they get spawned, based on probabilities relating to the strength of the player and the level they are found on.

#### Turn-based

I used the javascript readline function so that my whole game loop runs each time a button is pressed. This is a pretty simple mechanic.

#### Permadeath 

Permadeath means that when you lose, you restart from the beginning. I print out the player's stats and save them to the filesystem in a score file that is printed the next time the game is played.

#### ASCII graphics

This alone is quite a hassle because it means I keep trying to work with the commandline for output/'drawing'. This is a tradition in roguelikes, a genre going on 40 years old, and its age shows. ASCII text is charming to many who are fans, including me, but downright offputting to the majority of casual players. I thought I'd make a system that could be played in the terminal, as well as in the browser if I implement my own graphics with the browser's canvas and the [p5.js](https://p5js.org/) library I use so often, but I haven't completed that yet.

I don't have much experience with Curses, the standard text-mode interface library for the Terminal, or npm's [blessed](https://github.com/chjj/blessed) package. Instead I chose to clear the screen after each button press. This little hack saved me some research time and implementation though is worth revisiting later.

### Gameplay

Each time the player descends a floor there is a chance that gold can be present (*) on the level and there will almost definitely be monsters (k, b, m, T, etc..) present. While the player moves around there is a chance each turn that additional monsters can be spawned and appear by walking from the edge of the dungeon. Monsters have various levels of aggression, which determines if they approach or attack the player. To attack a monster, a player simply walks into a monster. When a monster dies it is removed. Text descriptions of events and game stats are printed above the game area. No two games are exactly the same as each level will be a different length, have different monsters, items, and values. The game ends when the player is killed (usually) or if the player makes it down to the 16th level and grabs the amulet of Yendor. By the way, this quest goal is a standard mechanic in classic roguelikes, and I thought I'd keep it in for this game.

I have future plans of a one-dimensional roguelike that plays more like a walking sim or flatgame where instead of monsters and attacks you meet poets and or partake in conversations. Well, I stuck to the stereotypes of the genre for this one.

### More one-dimensional games

I was a big fan of the one-dimensional puzzle roguelike game [Cosmic Crown](https://umbrella-isle.itch.io/cosmic-crown-android) by Alice L. Unfortunately, it is no longer available for iOS and I haven't been able to get the web version to work. Cosmic Crown has 8bit graphics and animation and polished gameplay. Rather than a hack-and-slash style roguelike with monsters it features puzzles like leaping past toxic sludge, razor sharp blades and the like.

<iframe width="560" height="315" src="https://www.youtube.com/embed/JjrynUdyec4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

In a web search I was able to find another one-dimensional ASCII roguelike, one that was created in less than a day in a jam. It's [Stutter Step](https://evgeniipetrov.itch.io/stutter-step), a pretty minimal game by [Evgenii Petrov](https://evgeniipetrov.itch.io/). Incidentally, if you're looking for gameplay ideas in making a one-dimensional roguelike, there are some tips and ideas from a 2013 forum post [here](https://forums.roguetemple.com/index.php?topic=3460.0) (backed up just in case here: [1](https://web.archive.org/web/20141213031620/https://forums.roguetemple.com/index.php?topic=3460.0) [2](https://web.archive.org/save/http://forums.roguetemple.com/index.php?topic=3460.15).

One other strange minimalist one-dimensional game is the celebrated **Line Wobbler**!

[Line Wobbler](https://wobblylabs.com/projects/wobbler) is by Robin Baumgarten. It is not a roguelike because the gameplay remains the same each time rather than different levels and puzzles created procedurally. But it is a very silly *dungeon-crawler* with preset levels and puzzles (or enemies) played using a spring door stop as a controller and a long beautiful multi-color LED strip as the display. 

Wikipedia helpfully [describes](https://en.wikipedia.org/wiki/Dungeon_crawl) a dungeon crawl game as *a type of scenario in fantasy role-playing games in which heroes navigate a labyrinth environment (a "dungeon"), battling various monsters, avoiding traps, solving puzzles, and looting any treasure they may find.*

<iframe width="560" height="315" src="https://www.youtube.com/embed/UZ_5ol_kyL4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Line Wobbler was included in the [UCLA Game Art Festival](http://festival.games.ucla.edu/2015/) I curated at the Hammer Museum several years ago. I also live close to Wonderville, the bar and indie arcade in Brooklyn, and have been able to play the game there a few dozen times. It's a delight to play. I love the strong connection between the player's handling of the vibrating door stop controller and the motion of the colored dot ('the player') travelling along the one-dimensional LED strip. 

#### More one-dimensional games and resources

Corey Johnson made [URL Hunter](http://probablycorey.com/url-hunter/), also using ASCII text. The game is played in a website's URL bar. You are a hunter (O) trying to capture animals (a) by pressing the spacebar. Click the link and look at the URL to begin playing.

There are several one-dimensional chess variations. There is a version designed by mathematician and puzzle-maker Martin Gardner. I wrote about his game Hexapawn previously in my post on [chess variants](http://leetusman.com/nosebook/chess-variants-and-inspiration). Gardner's games and many other one-dimensional chess variants are listed on the [Chess Variant Pages](https://www.chessvariants.com/shape.dir/onedim.html) (and backed up [here](https://web.archive.org/web/20180808220452/http://www.chessvariants.com/shape.dir/onedim.html)). [One Ring Chess](https://www.chessvariants.com/shape.dir/oneringchess.html) is another strange variant built along a loop. 

![1dimensional chess]({{'/images/roguelike/1dchess.jpg' | absolute_url }})  
*1dimensional chessboard, image, tutorial and new rules by [Alex Z](https://www.instructables.com/id/One-Dimensional-Chess/)*

One day I'd love to make my own hardware one-dimensional roguelike. Robin Baumgarten gave a [talk](https://www.youtube.com/watch?v=TTJmfhR12ys) on the making of Line Wobbler for A MAZE several years ago. 

Game creator Will of 14hour lunch break made [One Dimensional Arcade](https://14hourlunchbreak.itch.io/one-dimensional-arcade) which includes one-dimensional versions of Tetris, Frogger, and Breakout. I didn't find them much of a challenge.

[Wolfenstein 1d](http://www.wonder-tonic.com/wolf1d/) looks pretty silly. There is [video](https://www.youtube.com/watch?v=QSvECzuaYn0) of the gameplay.

```
                  _\<
                 (   >
                 __)(
           _____/  //  ___
          /        \\ /  \\__
          |  _     //       ||
          | | \    \\  / _   ||
          | |  |    \/  | \  ||
          | |_/     |/  |  | ||
          | | \     /|  |_/  ||
          | |  \    \|  |     >_ )
          | |   \. _|\  |    < _|=
          |          /_.| .  \/
  *       | *   **  / * **  |)/)    **
   \))ejm97/.,(//,,..,,\||(,wo,\ ).((//
                             -  \)
You died!
You were killed by a jackal on level 2
You killed: 10 monsters and found 3 gold.

goodbye
```


