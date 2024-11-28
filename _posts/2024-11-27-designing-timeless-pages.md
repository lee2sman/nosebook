---
layout: post
title: Designing Timeless Webpages For Writing or Portfolio 🌐🕰️
categories: [programming, art]
---

In this post I'm writing on designing for "reading" on the web, as opposed to the crap present on 90% of platform-hosted sites. By the way, after reading this I'm open to receiving feedback and any ideas you have in response to this post. I am just one person, with my own experience, but I am not to be considered a sole source of knowledge or expertise.

Here's the idea:

The web in 2024 kind of sucks because it's full of junk: sidebars, ads, click to acknowledge our cookies, a pop-up to read our article, please sign-in, filler text before you get to the cookie recipe, links to buy a product on Amazon so the New York Times can make a few extra cents, and now AI-written nonsense "articles." AGH. F Off!

A bunch of us have tried to sequester ourselves away, jump ship much of the time from the horridness of what the web's become. Here's an example of what I mean:

## How I do "text-first" browsing

* I use [Ublock Origin](https://ublockorigin.com/), the only free and open source ad blocker I know of that actually blocks all ads including YouTube, Google, and even "good ads" from a certain competing AdBlock company.
* I spend time making and reading gemlogs and browsing [Gemini](https://geminiprotocol.net/), the alternative protocol that's a step more complex than pre-www Gopher and a step less complex than the web. There are curently no ads, minimal media, no companies really involved. So it means most sites on Gemini are blogs and articles by a number of people, maybe numbering in the mid thousands. There are a number of great browsers (clients) for this, including the venerable [Lagrange](https://gmi.skyjake.fi/lagrange/) client. Most of the people posting on Gemini are open source-oriented software folks, so that does limit the kind of people and writing you find there.
* Occasionally I browse the web through alternative browsers like NetSurf and Dillo, maybe Falkon, which don't allow JavaScript or make it easy to block. 
* Sometimes I use text-only browsers like Offpunk, w3m, links. These have no images (or allow them only with some options turned on).
* Sometimes I turn off Javascript. No scripting means little chance of annoying pop-ups, high-bandwidth applications and trackers, etc. Though it does break many sites too.
* There are webrings like the [Low Tech Webring](https://emreed.net/LowTech_Directory) and the [Merveilles webring](https://webring.xxiivv.com/) that collects like-minded artists, game-makers, writers and programmers who have interesting websites full of articles, tutorials or art projects and are fast and easy to read.

What's the point of all this? Trying to make reading on the web a *first class experience,* less full of junk and distractions. That's the web I want most of the time.

It also means a speedier web, where you're not waiting for trackers, scripts and media to load, so these sites serve fast and furious even on old, ancient computers and devices, not requiring the fastest CPU or latest hardware in order to serve basic information.

## Making a reading-oriented site

Okay, so how do we design around readers without having just straight HTML? And how do we do this so our writing reads well across a range of sizes and screens?

If we're talking about designing for the web, there are a few simple things one can do.

First, take a look at these sites and see if you notice some similarities. I've tried to add a few words about the site so you know what to expect to see there.

* [my blog landing page](https://leetusman.com/nosebook/)
* [femi shonuga's sound art site](https://femishonuga.com/)
* [cblgh alternative open source software portfolio site](https://www.cblgh.org/)
* [Lagrange Gemini client software site](https://gmi.skyjake.fi/lagrange/)
* [em reed's writing portfolio](https://emreed.net/writing)
* [snarkmarket, the blog of novelist robin sloan](https://snarkmarket.com/)
* [html energy, a podcast and html writing event](https://html.energy/)
* [james chip's games and software site](https://jameschip.io/home.html)
* [rek's website of illustration and writing](https://kokorobot.ca/site/home.html)
* [eli / oatmeal's blog and wiki site](https://eli.li/)
* [permacomputing wiki](https://permacomputing.net/)
* [helvetica blanc's illustraiton art portfolio site](https://helveticablanc.com/)
* [thimble software site](https://thimble.commoninternet.net/about)
* [iffy books website](https://iffybooks.net/about/)
* [compudanzas creative code projects, wiki and portfolio](https://compudanzas.net/)

Look at the design of these sites? Do you see what they have in common?

What do you notice?

I see:

* limited width of body text, roughly the size of a page in a softback book
* Centered text (usually) oriented around reading
* clear title at top
* if any navigation, usually it's a simple navigation bar at at the top
* just enough color for flavor but limited color palettes
* minimal page load through limited use of photos, almost no video or other media
* photos get lazy-loaded to avoid the big memory loading hit
* page designed around the basic HTML tags and semantically structured (example to follow)
* page designed to look good on multiple screen sizes

Anything else?

These are choices meant to emphasize reading, not to serve advertisers, or getting you to jump away elsewhere as quickly as possible. They're not the latest design trend, whatever that is. They don't look like "bootstrap" sites.

The pages are generally devised around semantic html with body, heading tags, paragraphs, list items, block quote, list items, and links.

They are often pages written in [markdown](https://en.wikipedia.org/wiki/Markdown), then translated to html.

Here's a not-too-overly-simplified template:

```markdown
# Title of the post

![A descripton of an image that complements the article](images/article-photo.jpg)  
*I usually write a caption in italics here*

## Section 1

A paragraph of text. Maybe a [link](https://website.com) elsewhere. Or maybe just lots of fun stuff to read. 

I might have many paragraphs. And after writing all of that, maybe that's all the page has. Stop there. Or maybe on a complex page I have more sections and don't need a section 1 heading above.

## A second section, if necessary

### For complex pages, a third nested heading

More writing can go here.

* And a list item
* Another list item

And so on.
```

Other things you may want to add: codeblocks, blockquotes. Incidentally, I usually keep my navigation bar and footer in a separate file, written in html, and I paste those in later by hand or through an automated process, but maybe I'm getting ahead of myself here.

I often use [pandoc](https://pandoc.org/) to convert markdown to html pages that can be hosted online, but many static website builders allow you to write your pages in markdown as well. This blog is (currently) written in markdown, then converted to html format through my static site builder. 

Let's say you write your above template page and then start filling out and completing an article or post. You have a few options to convert it with pandoc and use an external css stylesheet.

You could put front matter at the top of your markdown file that links to your external stylesheet and adds your title.

To do that, you'd add "front matter" like this between 2 sets of three hyphens:

```
---
title: Title of the article
css: main.css
---
```

Then the magic incantantion in the terminal to translate your post to html looks like:

```sh
pandoc -s index.md -o index.html
```

Replace index.md with your markdown document name and index.html with the output filename. Change the *main.css* in your frontmatter to match the name and location of your CSS stylesheet. If you don't use a static site generator you could manually add a link to your website's index page. And if you're a fan of RSS or curious about it, you could read Everest Pipkin's post on [Handwriting your RSS feed](https://everest-pipkin.com/teaching/handmadeRSS) so other people can subscribe to your site through a RSS reader.

## Some style guidelines

If you barely know enough to hand write a website, that can work with this method. Find a good [classless css](https://github.com/dbohdan/classless-css) to drop in, and see how it looks. If you have minimal or middling knowledge, or are not a great designer but want to try some things out, you could start with one of those and then add your own css alterations after that, like changing the background and foreground text colors. Aim for good color contrast. 

### Start by centering and choosing some color

Some minimal almost-adequate CSS starter code:

```css
:root {
  --main-bg-color: #dbdbdb; /* Replace with your own color choice */
  --main-fg-color: #242424; /* Pick a good contrasting color */
}

body {
  max-width: 50em;
  margin: 0 auto;
  padding: 10px;
  font-size: 1.4rem;

  background-color: var(--main-bg-color);
  color: var(--main-fg-color);
}
```

In the above code, we set a CSS variable for the background color, and a contrasting color for the foreground color. Then we set a maximum width for the body of our site, where our text will appear. By specifying our margin to be set to auto the browser will place equal margins to the left and right side of our centered text. We add a little padding and I often set the font size to be 1.4 times the size of the root element default of the browser, which means a bit bigger than 16 pixels, but change this to reflect what size you like to set.

### Font choice

Next, let's make our text look a little bit nicer than the default Times text. 

We could change the default to a sans-serif, adding this to the body section of our CSS stylesheet.

```css
  font-family: "Helvetica", "Arial", sans-serif;
```

### Spacing

Next, we add some spacing to make our text more readable.

We can add padding, and specify our line-height. 

```css
body {
  line-height: 1.5;
  padding: 4em 1em;
}

h2 {
  margin-top: 1em;
  padding-top: 1em;
}
```

The above spacing suggestions are from the excellent [Web Design in 4 minutes](https://jgthms.com/web-design-in-4-minutes/).

This is also where I found some great styling tips for code snippets. Their starter suggestion to make code blocks more readable:

```css
code,
pre {
  background: #eee;
}

code {
  padding: 2px 4px;
  vertical-align: text-bottom;
}

pre {
  padding: 1em;
}
```

At this point, you can add in secondary colors and custom fonts if you like. I usually try to pick fonts that are minimal in size, locally served (instead of through a service like Google), or go with default webfonts.

For a little bit more, check out the source code (view source) of any of the websites I linked above, or my own [source code](view-source:https://leetusman.com/archiving-artist-spaces/assets/css/main.css) from my [Archiving Artist-Run Spaces website](https://leetusman.com/archiving-artist-spaces/) or this blog (please steal the cute pink stripe on the left side of my code blocks) or my website.

## Accessibility

For any image, make sure you write alt text. Imagine a person reading on a screenreader, or a viewer checking out your site without the benefit of graphics or on a slow connection.

Have high contrast colors between your foreground text and background. Include text transcripts for audio or video. Don't use color alone as a way of conveying information. Make your navigation easy to use. 

The w3c Web Accessibility Initiative provides lots of strategies to make the web accessible to people with disabilities. Their [easy checks](https://www.w3.org/WAI/test-evaluate/easy-checks/) section provides a starting point to assess and plan accessibility in your site.

## Feedback

What have I left out?

Any websites I should be aware of, or alternate ideas? 

What are you using?

Feel free to email (link on my info page) with any of your own tips or suggestions.

