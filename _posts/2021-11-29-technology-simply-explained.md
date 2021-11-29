---
layout: post
title:  "Technology Simply Explained"
categories: programming
---

# Technology Simply Explained

![Technology Simply Explained](https://user-images.githubusercontent.com/7377908/141535976-eef81b5d-4913-45f3-a3d4-387ff4ec1f36.png)  

This November I participated in NaNoGenMo, National Novel Generating Month, an annual event coinciding with NaNoWriMo, the National Novel Writing Month. The original idea harkens back to 2013 when artist, programmer, botmaker Darius Kazemi tweeted out the idea on a whim when he wrily noted that NaNoWriMo defined a novel as a book with 50,000 words or more. 

This is the 4th NaNoGenMo I've participated in. I browsed the Project Gutenberg website looking for public domain books for inspiration, with the idea that maybe one or more could serve as a corpus of text I could use. I stumbled across the book [Gas and Oil Engines, Simply Explained](https://www.gutenberg.org/ebooks/27286) and was inspired by its language, especially its introducion: 

> My object in placing this handbook before the reader is to provide him with a simple and straightforward explanation of how and why a gas engine, or an oil engine, works. The main features and peculiarities in the construction of these engines are described, while the methods and precautions necessary to arrive at desirable results are detailed as fully as the limited space permits.... 

With this inspiration I began initial code sketching. I used regular expressions to prepare and clean up the text, and using the simple Linux program *shuf* I tried pulling out sentences at random. To my untrained eyes, the rearranged text was as convoluted and confusing as the original *simply explained* descriptions. I decided to generate lots of entries on various technology. Using the [New Technologies](https://github.com/dariusk/corpora/blob/master/data/technology/new_technologies.json) list from Darius' Corpora, I iteratively built up something of a simple recipe:

1. Pick a technology
2. Give an initial instruction
3. Pick between 8 to 15 sentences at random from the book to describe that technology
4. Replace engine words with whatever technology was selected for the section
5. Drop in random diagrams and pictures
6. Repeat this until you have 50,000 words and don't forget to add the intro back in

This recipe was scripted with Fish, a shell language similar to Bash but meant to be a bit more regular. I didn't generate the diagrams or photos at run time but rather pre-generated hundreds with Processing and then randomly selected from them in my Fish script. If I re-wrote such a program from scratch I might use different languages and process, but this was what developed in my iterative approach.

To generate the diagrams: I wrote a basic Processing program to generate a series of print-quality diagrams, each one including between 2 and 7 procedurally created ellipses or rectangles with letters and a short caption describing the diagram at the bottom.


![Diagram example inline](https://user-images.githubusercontent.com/7377908/140012086-033225ff-aa56-4bf4-a4e6-48b92ae23bc0.png)

For the photos, I visited flickr.com and did a Public Domain image search for *machines, technology* and the like. For October I had been working on various code-sketching projects in p5.js to create a procedurally-generated visual zine, that I then did some test prints on a risograph printer at Shandaken Projects in New York. I ported my own code to Processing because it's easier to write to disk. First with a simple fish script I looped through my directory of public domain machine images, converted them to black and white and removing their background, using imagemagick. In Processing I picked one to three images, rotated slightly, and then blew the image up one to five times, cutting out a particular image size, and like the diagrams, adding a short procedurally-generated caption.

![Image with caption example](https://user-images.githubusercontent.com/7377908/140707338-44ceb315-dd55-4466-994c-bd1162b401fa.png)  

The program is capable of producing an endless supply of different versions of Technology Simply Explained. 

But here's the one I've created for NaNoGenMo 2021. The resulting book is *almost* readable. It's fun to skim at least though I'd be hard pressed to read the entire *novel* straight through.

I may end up creating a print copy.

### Links:

[Completed book](https://github.com/lee2sman/technology-simply-explained/blob/main/books-editions/technology-simply-explained1.pdf) (PDF) of Technology Simply Explained

[Project repo](https://github.com/lee2sman/technology-simply-explained)

[Development log](https://github.com/NaNoGenMo/2021/issues/25), written in an issue for the NaNoGenMo 2021 event repo
