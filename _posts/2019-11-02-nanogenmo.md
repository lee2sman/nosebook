---
layout: post
title: "Pomelo, my Yoko Ono Grapefruit Generator for NaNoGenMo and 2 more"
date: 2019-12-02 15:00:30 -0800
categories: [programming, art, tools]
---

Every November is National Novel Writing Month (abbreviated: NaNoWriMo), an annual tradition where thousands of participants attempt to write a novel, defined as writing a book of at least 50,000 words. In 2013, internet artist [Darius Kazemi](https://tinysubversions.com/) proposed National Novel Generating Month via a tweet.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Hey, who wants to join me in NaNoGenMo: spend the month writing code that generates a 50k word novel, share the novel &amp; the code at the end</p>&mdash; Darius Kazemi (@tinysubversions) <a href="https://twitter.com/tinysubversions/status/396305662000775168?ref_src=twsrc%5Etfw">November 1, 2013</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

Since that initial dashed-off idea an annual tradition has sprouted up and a community of computational artists, programmers, experimental poets and other coders have formed and run with the idea. The rules of NaNoGenMo are quite simple: 

> The only rule is that you share at least one novel and also your source code at the end. 

The first year 2013 had dozens of participants. But it wasn't until 2016 that I began to participate.

Originally I had the [idea](https://github.com/NaNoGenMo/2016/issues/22) to generate a version of Yoko Ono's book Grapefruit, a book of instruction pieces originally published in 1966. The book had been republished mutiple times, and a later book Acorn, another book of instructional poems was published in 2013. 

My 2016 generated novel *'Pon The Road* was intended as a new version of Jack Kerouac's On The Road. I fed in the full text of the original scroll text and used a Markov chain text generating scheme implemented through the Python Markovify library. A Markov chain is a fairly simple method for generating data. The algorithm doesn't look at text over time but essentially uses a specified location's word (or words), finding and matching together text from anywhere in the source text that best matches to complete a phrase. In contrast to machine learning, this is a quite shallow generative process, and so text output can have a scattershot feel. While this poorly suits many projects, it can work for tweets for example and I felt it simulated the tone I was attempting to replicate: a new stream-of-consciousness novel using the previous Kerouac novel as source data.

![Pon The Road]({{"/images/PonTheRoad-cover.png" | absolute_url}})

The ending of ['Pon The Road](https://github.com/lee2sman/PonTheRoad-NaNoGenMo2016), credited to Jack Khrouac:

> The bus groaned up Grapevine Pass and yet definitely in it together. «Since Denver, Sal, a San Francisco burning green and wondrous from our aerial shelf.
You going with me. He fished out some long canvas bags from the floor on cushions, Dean and his fears. Dean, why did you like teaching high-school French?» he yelled.
> The boys were shooting pool at his side, watering all over the long bar to the ticket and not only that, but my brother was let off there. Carlo had a beer, and casually Bull went in to me and looked like a cruiser. He didn't have to drive on. Remi was gone and a night at his raving wheel, with eyes of the interior of the whirring blades. And another matter of months and Inez had a twenty-dollar Buick back in line when another car came out red through the streets. «Where we going, man?» I moaned.
> Dean came back red-faced mad. Their food bill was over anyway, so I picked up everybody on the truck to meet them all, late as hell.

I took off from participating in NaNoGenMo for a few years but I've continued to make generative art and computational text projects. I teach Yoko Ono's Grapefruit and instruction pieces as a type of Fluxus [event score](https://en.wikipedia.org/wiki/Fluxus#Event_score), connecting it in a lineage leading to algorithmic and computational art. 

This year I dediced to return to the idea and to write a generator to create my own Yoko Ono-inspired instruction pieces, a project idea I dubbed *Pomelo*. 

![Yoko Ono's Grapefruit]({{"/images/grapefruit.jpg" | absolute_url}})

The main tool I chose was Kate Compton's [Tracery](http://tracery.io), a tool and *Little Language* to create story-grammars. A grammar is a *dictionary* (in the programmer's sense of that word) of key-value pairs. For example, you may have the key *Job* and the value paired with it could be an array with *librarian, baker, banker, teacher, race car driver, plumber, astronaut, programmer*. Incidentally, this sounds like it comes from a list of job titles from a [Richard Scarry book](https://everythingbusytown.fandom.com/wiki/List_of_Busytown_characters). 
Other tools I used include the [p5.js](https://p5js.org/) Javascript library, which while not essential I now consider a basic simple starter for many of my web projects. I also used a corpus of text, including copied out text fragments inspired from Grapefruit, and many words gathered from Darius Kazemi's [Corpora](https://github.com/dariusk/corpora) collection. 

At first I had some difficulty figuring out Tracery's save feature, which allows essentially a variable name chosen earlier in a story to be re-used later in a story. Because I used the p5.js library's function calls to create separate html tags to generate titles as headers and body text and endings as paragraphs I was creating separate calls to Tracery to flattan story-grammars. Essentially I was generating text phrases multiple times and based on my structure this prevented me from having variables from Tracery carry on to later parts of a generated instruction piece.

While I could continue to work on my Pomelo generator there is a hard deadline to finish by the end of November, so I'm considering my work to be at a presentable stage.

Some early versions of the Pomelo generator:

![Yoko Ono's Grapefruit]({{"/images/pomelo/0.png" | absolute_url}})

![Yoko Ono's Grapefruit]({{"/images/pomelo/1.png" | absolute_url}})

![Yoko Ono's Grapefruit]({{"/images/pomelo/2.png" | absolute_url}})

Some later generated pieces:

![Yoko Ono's Grapefruit]({{"/images/pomelo/3.png" | absolute_url}})

![Yoko Ono's Grapefruit]({{"/images/pomelo/4.png" | absolute_url}})

You can generate your own Grapefruit-style instruction pieces by visiting the [Pomelo page](http://leetusman.com/pomelo).

#### From [Pomelo's GitHub repo](https://github.com/lee2sman/pomelo):

> Grapefruit was originally published in a limited edition of 500 copies by the Wunternaum Press in Tokyo in 1964.

> The 1970 edition contained material from the original, and pieces and drawings done in subsequent years by Yoko Ono.

> This book was generated using Lee Tusman's Pomelo, created for NaNoGenMo 2019, three years after he formulated the idea to make generated Grapefruit instruction pieces. This work was generated using Kate Compton's Tracery tool to develop the grammar and text expansion and programmed with the p5.js javascript library.

> The list of food items is courtesy The New York Public Library. The book's content is Public Domain CC0. The license for the code is MIT. The license for Tracery is Apache License 2.0.

### 2 Nano-NaNoGenMo entries

In addition to my Pomelo project I took a break to create two mini Nano-NaNoGenMo projects. The idea for a Nano-NaNoGenMo comes from my friend Nick Montfort, a proposal for folks to make tiny (< 255 char) NaNoGenMo entries, which could be tweeted out (for example). Inspired by another Nano-NaNoGenMo entry, 50,000 Meows, I decided to make a text implementation of this meme. 

![Cat Meme - Don't Ever Talk To Me Or My Son Ever Again]({{"/images/catmeme.png" | absolute_url}})

I used [cowsay](https://en.wikipedia.org/wiki/Cowsay) the hacker joke ascii program that has a cow (or other ascii image file) saying a specified text phrase. I added my own cow file using a cat ascii image from one of many hundreds of ascii cats on the incredible 1995-era [website](https://user.xmission.com/~emailbox/glenda.htm) by Glenda Moore. I copied another cowsay file, replaced the ascii art, and I was good to go.

##### The short code in Javascript/node:

```
node -e 'let d=\'son\';for(let i=0;i<333;i++){let m="Don\'t talk to me or my "+d+" ever again.";console.log(m);d="son\'s "+d}' | cowsay -f cat
```

#### Preview from the top:

```
 _________________________________________
/ Don't talk to me or my son ever again.  \
| Don't talk to me or my son's son ever   |
| again. Don't talk to me or my son's     |
| son's son ever again. Don't talk to me  |
| or my son's son's son's son ever again. |
| Don't talk to me or my son's son's      |
| son's son's son ever again. Don't talk  |
| to me or my son's son's son's son's     |
| son's son ever again. Don't talk to me  |
| or my son's son's son's son's son's     |
| son's son ever again. Don't talk to me  |
| or my son's son's son's son's son's     |
| son's son's son ever again. Don't talk  |
| to me or my son's son's son's son's     |
| son's son's son's son's son ever again. |
| Don't talk to me or my son's son's      |
| son's son's son's son's son's son's     |
```                                     

#### And at the bottom:

```
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
| son's son's son's son's son's son's     |
\ son's son's son's son's son ever again. /
 -----------------------------------------
     \
      \
         ,_         _,
         |\.-"""-.//|
         `         `/
        /    _   _
        |    a _ a    |
        '.=    Y    =.'
          >._  ^  _.<
         /   `````
         )           (
        ,(           ),
       / )   /      (
       ) (   )   (   ) (
       ( )   (   )   ( )
       )_(   )   (   )_(-.._
      (  )_  (._.)  _(  )_, `
       ``(   )   (   )`` .' .'
    jgs   ```     ```   ( (`
                         '-'
```

There is a [gist](https://gist.github.com/lee2sman/2859eced66ea5a84938809f8bc5a1ad0) with code, methodology and cowsay file.

### Lucifer Bimbisara or Francois unsuperscribed

Finally, I created one other experimental Nano-NaNoGenMo piece. I recently learned about the existence of the [words](https://en.wikipedia.org/wiki/Words_(Unix)) file ```/usr/share/dict/words``` that comes standard on Linux/BSD computers (including Macs). It's a line-delimited list of words.

                                             
Inside ```usr/share/dict``` are these text files:

```
README
connectives
propernames
web2
web2a
words
```                                                      

I thought that would make a good corpus for a Nano-NaNoGenMo entry, Nick Montfort's [2019 challenge](https://nickm.com/post/2019/11/nano-nanogenmo-or-nnngm/) #NNNGM to generate a novel using < 255 chars. Although all are worth investigating, I only ended up using *words, connectives and propernames.*


For this entry, I decided to try my hand at scripting in [Fish shell](https://fishshell.com/). I'm a big Fish shell fan and have been using it for a number of years but always avoided getting into the nitty gritty of fish shell scripting, which is supposed to be more regular than Bash scripting, but not compatible with it. With some searching I found this [tutorial](https://nicolas-van.github.io/programming-with-fish-shell) by Nicolas VanHoren and decided to try my hand at scripting with Fish. 

As this is a sub-255 character program, a significant part of the creativity lies in the coding approach, at least as important potentially than the actual output generated. I came up with a very simple formula to generate my text: a proper name, a *connective* word, a *word* word, and then start the loop anew until I hit about 50,000 words. This is obviously an overly-simple formula. For me, the fun and creativity was figuring out how to generate the text, learn a bit in a new to me language, and work my way through inevitable bugs and challenges in this tiny program. If I wanted to go deeper or extend this, I could use the other word files in the ```usr/share/dict``` directory (especially intrigued by ```web2a```), and write more complex grammar generators.

You can find a [sample wordlist](https://users.cs.duke.edu/~ola/ap/linuxwords) online. 

My ```fishwrap.fish``` code:

```
for q in (seq 16666 -1 1)
    cat propernames | head -(random 1 1308) | tail -1 | tr '\n' ' '>>f
    cat words | head -(random 1 235886) | tail -1 | tr '\n' ' '>>f
    cat connectives | head -(random 1 150) | tail -1 >>f
end
```

Note: I could get this filesize down further by renaming the files propernames, words and connectives to a single letter for example but this satisfies the size requirement.

#### Example generated text excerpt:

```
Lucifer Bimbisara or
Francois unsuperscribed did
Neal prudish mr
Manuel hypalgia make
Eddie anomaloflorous even
Ilya gummous man
Mott zoea against
Peter flunkyite which
Santa leafboy she
Mott brob time
Danielle turnipwise is
Lui menorrhagic me
Rafael Powhatan take
Spock Sikkimese did
Naresh went from
Gregor wedset both
Piete circovarian another
Hui inhalant so
Robert pictured good
Nhan chafer these
Niels anorthosite also
Terry nonbankable we
Jelske elderbrotherly where
Mario cohere came
Ronald Leonist made
Leila poppel way
Emma jaunce little
Miles cacochymic man
Walter otiorhynchid more
Scott mesozoan an
Santa exsurgent what
Doyle derangement could
Werner sirupy each
Becky girr never
```

There is a [gist](https://gist.github.com/lee2sman/6c9426d81d0dcc64a4902d6c4cb6af7d) with description, full methodology, and code walkthrough.

And that's my report for my participation in NaNoGenMo 2019! To see many other entries over the years, check out the [NaNoGenMo website](https://nanogenmo.github.io/).
