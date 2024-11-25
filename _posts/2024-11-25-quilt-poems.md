---
layout: post
title:  "Quilt Poems: A new generative text project 🪡🟨"
categories: programming
---

Every year for the past decade November has meant the month of NaNoGenMo for computational artists and poets. [NaNoGenMo](https://nanogenmo.github.io/), or National Novel Generating Month, is a month where folks dedicate time to writing software that generates a "novel." Originally the event was started as a joke, when ringleader, programmer, artist Darius Kazemi noticed that NaNoWriMo, the much more well-known National Novel Writing Month, specified the definition of a novel minimally as consisting of at least 50,000 words. And with a rallying tweet, dozens of computational artists tried their hand at writing code to generate a novel or at least 50,000 words of text.

Over the years I've participated at least 5 times. It's a good excuse to to come up with a short-term project idea and see it through to completion, including 'publishing' it online. Some of my previous NaNoGenMo projects have taken off and been exhibited, including my 2018 project Pomelo, consisting of generative Yoko Ono-like "instruction pieces" in the style of her book Grapefruit.

Leading up to NaNoGenMo this year I hadn't had much of an idea of what I wanted to do. The way you participate is to announce your intention through an "issue" on the [NaNoGenMo 2024 github issue page](https://github.com/NaNoGenMo/2024/issues). This is akin to filing a bug report in open source software but instead announcing your ideas of what you'll work on. I perused my previous year reports in case that would help generate new ideas for "novels" to generate but none came for a few weeks and I placed it on the back burner.

Last Thursday evening I attended the monthly decade-long [WordHack](https://toddwords.com/wordhack/) event, where there was a release party for the new MIT Press book OUTPUT: an anthology of computer-generated text, 1953 - 2023, edited by Lillian-Yvonne Bertram and Nick Montfort. Several of those presented in the book read their work at the WordHack event, and Nick published a small pamphlet of new works in conjunction with the release of OUTPUT, that I read on the trainride home. That cozy ride home on the train, where I read the software as well as the output gave me the kick to begin planning my own generative poetry. And the next day I quickly got the idea to produce "quilt poems."

Quilt poems were not actually a thing prevously, I don't think. Or if they were, I re-invented them. My idea was that I'd map out the patterns of various formal and informal quilt styles, like Log Cabin, Amish bars quilts, and the like. Then I'd generate visual poems that would place words in the same pattern of a particular quilt style.

Here's an example of a "housetop" pattern for example. The numbers are a recipe that correspond to parts of different strips or blocks in a quilt. The *language* is Lua (thus the double comma comment line).

```lua
{ --housetop
  {7,7,7,7,7,7,7,7},
  {7,6,6,6,6,6,6,8},
  {7,6,5,5,5,5,1,8},
  {7,6,5,4,4,4,1,8},
  {7,6,5,4,2,3,1,8},
  {7,6,5,4,3,3,1,8},
  {7,6,1,1,1,1,1,8},
  {7,8,8,8,8,8,8,8}
}
```

And below is an example housetop quilt. Of course this one retains more of the human element than my simple 8x8 grid. For example, the strip on the right isn't perfectly aligned, which only adds to its beauty.

![Housetop quilt, from The Henry Ford CC BY-NC via Flickr]({{"/images/housetop.jpg" | absolute_url}})  
*Pig Pen (also called Housetop or Log Cabin) Quilt, from The Henry Ford on Flickr, CC BY-NC*

I had in the past made geometric works using ascii/text as input to create images, like the series of experimental [puzzlescript studies](https://leetusman.com/puzzlescript-studies/) programs I'd worked on two years ago.

![Babylon quilt]({{"/images/babylon-quilt.jpg" | absolute_url}})  
*Beats of Babylon, a noise toy. [Code](https://www.puzzlescript.net/editor.html?hack=e0beecad0e66074a237512eb306528e5) and [link to play](https://www.puzzlescript.net/play.html?p=e0beecad0e66074a237512eb306528e5).*

I considered whether I wanted to have a colored output for my new Quilt Poems but decided that the visual poems themselves might be enough.

I did however try out a few approaches to printing text over color blocks.

![Secret Door quilt]({{"/images/secret-door-quilt.jpg" | absolute_url}})  
*Secret Door Quilt uses an Amish bars pattern*

This is a screenshot from my terminal. I knew you could change text and background colors through ANSI terminal commands, and found an ultra minimal single-file library to allow me to do that simply with easy commands. 

But after some tests, although this was kind of fun, I decided to let the poems speak for themselves in just text without color. This might also print more conveniently in black and white when I get to that stage.

I found text libraries of words from Darius Kazemi's [Corpora](https://github.com/dariusk/corpora) github repo, which has great lists of words. I also found a few Wikipedia articles with lists of words that work well together. I tested these many times to see if they generated interesting quilt poems. 

The bodies of text I ended up using were:

* list of adverbs
* list of 1000 common words
* description words
* infinitives
* metals
* common objects
* passages
* personal nouns
* rhymeless words
* words from Amelia
* rooms in a building/house
* words from shakespeare
* "stable" words defined by linguist Swadesh

## The "quilt poem" recipe

The basic algorithm I wrote to define each quilt works like this:

1. Pull in one of the lists of words
2. Pick 8 random words from that list, and number them 1 to 8
3. Pick a random one of the quilt patterns (such as housetop, cross bars, crazy quilt, etc)
4. Run from top left to bottom right, reading in the number of that place on the quilt pattern and subbing in the word assigned to that number
5. When placing a word, keep track of what the longest word is in that quilt, and if the current word is shorter, try placing spaces on either side so words in columns get centered. If the spacing is odd, place an extra space on the left.


### Example output

Try reading these out loud.

```text
Badly Questionably crazy variation quilt

    badly      viciously  questionably   quirkily   questionably   viciously    viciously  questionably 
    badly    questionably   silently     silently     viciously    quirkily   questionably   silently   
  silently   questionably   quirkily     viciously  questionably   mortally     viciously    quirkily   
questionably   silently     silently     quirkily     quirkily   questionably questionably   silently   
  viciously    quirkily     mortally     viciously      badly      quirkily     silently     mortally   
  silently     viciously     slowly      quirkily   questionably   viciously    viciously  questionably 
  quirkily     mortally   questionably   mortally     silently   questionably    slowly    questionably 
    badly      viciously    quirkily     silently     viciously    quirkily     fiercely   questionably 
    
Coil Undress bars quilt

 coil  undress   fade   sprout  cause   hurry    sin    shave  
 coil  undress   fade   sprout  cause   hurry    sin    shave  
 coil  undress   fade   sprout  cause   hurry    sin    shave  
 coil  undress   fade   sprout  cause   hurry    sin    shave  
 coil  undress   fade   sprout  cause   hurry    sin    shave  
 coil  undress   fade   sprout  cause   hurry    sin    shave  
 coil  undress   fade   sprout  cause   hurry    sin    shave  
 coil  undress   fade   sprout  cause   hurry    sin    shave    
 
Pit Staircase Drunkard's Path Quilt 

   pit         pit      staircase   staircase   staircase   staircase   staircase      pit     
staircase      pit         pit      staircase   staircase      pit         pit         pit     
staircase      pit      staircase   staircase      pit         pit         pit      staircase  
staircase   staircase      pit         pit         pit         pit         pit      staircase  
staircase   staircase   staircase      pit         pit         pit      staircase   staircase  
staircase      pit         pit         pit      staircase      pit         pit      staircase  
   pit         pit         pit      staircase      pit         pit      staircase   staircase  
   pit      staircase   staircase   staircase   staircase   staircase      pit         pit     
   
Judgement Day Retirement Amish Bars Quilt 

Judgement Day Judgement Day Judgement Day Judgement Day Judgement Day Judgement Day Judgement Day Judgement Day 
Judgement Day   retirement   inauspicious   retirement   inauspicious   retirement   inauspicious Judgement Day 
Judgement Day   retirement   inauspicious   retirement   inauspicious   retirement   inauspicious Judgement Day 
Judgement Day   retirement   inauspicious   retirement   inauspicious   retirement   inauspicious Judgement Day 
Judgement Day   retirement   inauspicious   retirement   inauspicious   retirement   inauspicious Judgement Day 
Judgement Day   retirement   inauspicious   retirement   inauspicious   retirement   inauspicious Judgement Day 
Judgement Day   retirement   inauspicious   retirement   inauspicious   retirement   inauspicious Judgement Day 
Judgement Day Judgement Day Judgement Day Judgement Day Judgement Day Judgement Day Judgement Day Judgement Day 

Patiently Hint Log Cabin Variation Quilt 

patiently      hint     patiently    correct    patiently      hint     patiently    correct   
patiently   patiently   patiently   patiently   patiently   patiently   patiently   patiently  
patiently    correct    patiently      hint     patiently    correct    patiently      hint    
patiently   patiently   patiently   patiently   patiently   patiently   patiently   patiently  
patiently      hint     patiently    correct    patiently      hint     patiently    correct   
patiently   patiently   patiently   patiently   patiently   patiently   patiently   patiently  
patiently    correct    patiently      hint     patiently    correct    patiently      hint    
patiently   patiently   patiently   patiently   patiently   patiently   patiently   patiently  
 ```
 
I love the musical staccato rhythm when I say these poems aloud. 
 
In keeping with the annual *holiday* I made sure my software spits out enough quilt poems to get me to 50,000+ words. I have it render to a text file, and made a few runs, checking out the generated poems. I picked one of the outputs and opened it in LibreOffice. I created a cover and info pages as well as added my source code and then the poem output.

I'm pretty happy with the rendered "book" and enjoyed reading it. I haven't read all of them, but I think it could make for a fine selection at a future poetry reading and/or WordHack event.

## The final book output

[A PDF rendering of Quilt Poems with cover pages](https://github.com/lee2sman/generative-quilt-poems/blob/main/dev/bw-quilts-output-test2.pdf)

[Example book output as text on GitHub](https://github.com/lee2sman/generative-quilt-poems/blob/main/dev/bw-quilts-output-test3.txt)

### Mini afterword on AI

I thought about some ideas that might use ChatGPT and I'm not completely against the idea but I'm not particularly a personal fan of LLM-generated texts and images. I don't find much inspiration in it. And I think more importantly, I don't think it's "fun" to work that way using a text prompt to create my creative work. The process of writing code, testing, shaping what's created, refining, and problem-solving until I get to a satisfying finished creative work, artwork, experimental computational poetry, and otherwise, feels more compelling when I'm steering the ship more concretely myself. And it feels more like my own work that I can recognize as well.

