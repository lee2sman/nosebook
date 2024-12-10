---
layout: post
title: New panblog static site generator 🍳🚧
categories: [programming, websites]
---

Each year for the past decade I've needed to create roughly half a dozen new websites a year, from simple websites for a class, to a devlog for an ongoing project, to documentation sites.

Years ago and continuing to this day, most "personal" websites were built on wordpress, an open source but "heavier" database-backed website system. Sites can be slow to load and are sometimes hacked. They also require a build process on a server, generally cost more to host online, and need to be updated to deal with security issues. About a decade ago one of the sites I had paid a designer to create for a professional project of mine was hacked, and I needed to hire a collaborator of the designer to debug and fix it. You may have seen sites like this where an article has dozens of spam comments underneath it, all saying something like "Very interesting" and a link to a spam site. Ugh. As I got better at web development myself, I manually converted that site to a static site. A static site means the output site has no database or running processes on a server. It is unlikely or impossible to be hacked by spambots.

About a decade ago so-called "static site generators" started to become popular. Generally, these are simpler than wordpress, without the need for any of the database or server-side code. They are more resilient. But they usually don't have simple text-entry boxes for the website builder/writer ([Lichen-Markdown](https://codeberg.org/ukrudt.net/lichen-markdown/src/branch/main/README.md) being one of the few exceptions). Usually, you write text files, create or modify a theme, then run the build script. Some of the most popular are Jekyll (which is built-in for GitHub pages free website hosting), Hugo, Eleventy, Pelican, and others.

I created panblog because I was frustrated with my regular jekyll static site generator, which ironically is used to generate the blog you are likely reading from right now if you are reading my nosebook blog. The reason for my frustration is that these static site generators usually involve installing and maintaining a chain of dependent software files. Web development is a fast-growing ecosystem, and web developers constantly update themes, build systems, dependency-management, etc. That's fine, but it's not pleasant if you have to constantly re-install and debug your website-building system every couple months, and that's what started happening for me, and for many of my art-coder friends that complain about this online on social media.

For many of the sites I create, particularly for class websites, I had increasingly turned to pandoc over the years to convert markdown to html. Pandoc is a commandline software swiss army toolkit, capable of converting between dozens of text formats. A typical use is to convert a text file to a docx file, or a markdown file to a html website, or a html file to a pdf, etc. It can do all of this and more, and be automated. I'm using it often to convert simple text files, blog posts and the like into a website that can be hosted online, with "theme" files that require little to no configuration.

Pandoc was created by [John MacFarlane](https://philosophy.berkeley.edu/people/detail/1), Professor of Philosophy at Berkeley.

> If you tried to figure out what philosophical logic was by looking in the literature, you might easily become confused. *--John MacFarlane, from the Preface to Philosophical Logic, A Contemporary Introduction*

That's a fun quote and a nice way to test out blockquotes in my css theme, but not related to textual conversion engines. That's okay. I like a well-rounded programmer-philosopher.

## panblog software and demo site

panblog is currently hosted on a [Tildegit repo](https://tildegit.org/exquisitecorp/panblog).

There is a [demo site](https://exquisitecorp.tildepages.org/panblog-demo/) built with panblog, that is a minimalist-style web blog.


### How panblog works

When learning pandoc, the basic way to convert a markdown document to html is:

```sh
pandoc -s index.md -o index.html
```

That command specifies the input file as markdown text and the standalone output file as a html webpage.

Pandoc provides many more options. For example, the current command I'm using to build the site index for panblog is below and is at the heart of what panblog is: a glorified wrapper around pandoc. Note, you'll never have to type this yourself. It's part of the build script in panblog.

```sh
  pandoc --standalone --template templates/site_template.html -s $site_folder/index.md --metadata title="$site_name" -B templates/header.html -A templates/footer.html --metadata theme="css/$site_theme" -o $site_folder/index.html
```

This means roughly:

* Pandoc will create a complete (standalone) html file
* using the site_template.html file that has variables for placeholders
* converting the previously-generated index markdown file
* adding in the site name from the config
* adding in the header template
* adding in the footer template
* using the specified css theme from the config file
* outputting to the output folder specified in the config file

Of course, you'll never have to type that in directly, so you can forget all of that if you want, but it's also here to refer to if you ever want to go back and modify panblog yourself.

panblog is public domain software. You are free to modify and use the code however you wish.

## How to use panblog

panblog has documentation on its [project repo on tildegit](https://tildegit.org/exquisitecorp/panblog) and at this point assumes some basic understanding of working on the command line, though I'd love to have it work with the Lichen-Markdown "content management system" at some point so that it can be run from a graphical front-end like Wordpress.

### To install:

```sh
git clone https://tildegit.org/exquisitecorp/panblog.git
cd panblog
chmod +x build.sh
```

You also need to have installed pandoc. And if you're on OS X, you may need to install coreutils to have tac and basename working.

### The basic quickstart is this:

* Modify the posts in the posts folder, or remove and replace them. The frontmatter section at the top of each post is optional.
* Modify the config.conf file in the root directory, and change the website title, url and anything else you desire
* Modify or add new pages in the the pages folder
* Modify the templates, especially templates/header.html and templates/footer.html
* Potentially you may want to switch out the CSS theme, or modify mine. I use classless CSS, so out of the box you don't need to add any special markdown beyond the normal headers, paragraphs, links and the like in your text files.

### To build your site:

```sh
./build.sh
```

You can find the rendered output site in the default _site folder. 

### To view it locally:

Go to your _site folder and run a local server there. See the project repo for more info on [testing your site](https://tildegit.org/exquisitecorp/panblog#testing-your-site).

### Uploading your site

You can [host your new website](https://tildegit.org/exquisitecorp/panblog#getting-your-site-online) on your own domain or at a free domain. You can use neocities.org, GitHub pages, Tildepages, or your own server. The details of how to upload or (s)ftp vary by program and server. This [demo site](https://exquisitecorp.tildepages.org/panblog-demo/) is hosted via [Tildepages](https://tildepages.org/).

For more info and to try it out, visit the [panblog project repo](https://tildegit.org/exquisitecorp/panblog). I'm also open to any feedback, suggestions, or requests from help from artists or other creative coders looking for some assistance getting started.

## Built during December Adventure 2024

I started on panblog a couple years ago, but had stopped development for a while. In 2023, the programmer Eli Mellen announced December Adventure, a month-long casual online programming project where folks sign up to work on projects during December and to blog about their work. I worked on completing a panblog "alpha release" during my [December Adventure 2024](https://leetusman.com/december-adventure-2024/).
