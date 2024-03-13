---
layout: post
title:  "Command line alternatives to cloud products and platforms 🚫☁️"
categories: [programming, permacomputing]
---


Most web products from file hosting to chat to banking software are made up of a tech 'stack' within a large software ecosystem. These are built for 'scale' and designed to be administered by a company providing you a more or less turnkey product at various levels of services. You pay for increasing levels of convenience, either with your private information being tracked, or with recurring expenses. This could mean paying annual fees for a 'creative editing suite', downloading and running a health tracking app that invisibly sells your data to data brokers, or accessing a social media account that sells your data to advertisers. And there are many more examples you can imagine or read about in the news.

Lately a number of folks in my online community have been discussing the problems of the platform Discord, from issues of centralization, monetization of community conversation and labor, accessibility issues, to the inability to archive or save discussions or content. Some folks have gone back to using a combo of blogs and the old chat system IRC. In my own communities I've cut back in my participation in Discord and created alternative self-hosted forums or piggy-backed on Mastodon instead.

Inspired by a CLI asciicinema recording by software and hardware developer Phil Hagelberg on how to use IRC I started to think more seriously about the idea that many cloud services could be replaced by some Linux software or some lines of Bash code gluing programs together.

First, I want to address some straightforward question or critique someone might have. Namely, why use the (Linux) command line instead of a simple web platform? Another criticism of this approarch might be that using the command line could appear to just be retro nostalgia, or unnecessarily complicated.

To answer these: I think using tools that don't cost much or any money, that we or others can modify and share, and that we can combine together to meet our needs is empowering. I have a bicycle where I can fix a flat tire, replace the chain, and do minor maintenance like adjust the breaks. Sometimes I spend money at the bike shop such as when I needed generator lights installed and wasn't confident in my own work. The bike is what I use to commute to my studio, and how I get around town. And yet I feel okay working on it, and the knowledge gained from trying lets me step in and fix something when I need to. Though I'm not afraid to get extra help at a bike shop or from knowledgeable friends. This isn't a perfect analogy, but it'll do.

Likewise, working with computer tools and software doesn't need to be intimidating. You can learn a bit at a time, try things out, find tutorials, and look for community to help you along the way. It's also a good way to resist commercialization. Rather than buying 'products' and the need for incessant upgrading, annual subscriptions or throwing out old products to get access to the latest products, you can opt out. Like riding a bike command line and text user interface software can be beautiful, elegant, luxurious or just minimally works. With some basic Bash knowledge you can get pretty far. 

I'll admit that some Free, Libre and Open Source Software can be ugly or clunky. I am also sympathetic to resisting pure retro-nostalgia, but I don't think continuing to use the command line in 2023 (or whatever year you are reading this) is simple nostalgia. Bash and the shell predates GUI software, and while I won't make a definitive prediction, it could even potentially outlast it. The shell never disappeared, and the amount of command line software has increased exponentially in the past number of years. And most of it continues chugging along to work year after year. It's not that uncommon to be reading a command line software man(ual) page and it lists the year in the 80s! And it's still useful.

On Linux, our basic automation tool is the command shell. As opposed to cloud software and GUI software it's often much easier to develop and certainly to glue together command line software. The term 'glue' here means to combine command line software together in various ways, sometimes envisioned by the developer but othertimes not. The software will have ways to take input, to be modified or configured, and has standard ways to produce output. All this allows it to be composed together with other command line software. We still don't have a great way to 'glue together' GUI software in this intuitive way that we weave together software in Bash. Using Bash to glue tools together is such a fundamental advantage on Linux systems because it was intentionally built in from the beginning to Unix. 

Glue code is often considered to be a form of 'duct tape programming.' It's fast. And glue code solutions might be considered a 'hack' approach, not necessarily implying the original term hacker here. And while this could imply that glue code doesn't last long it could also be thought advantageously as well. For the same reason that cloud services and platforms are black boxes where you input money or privacy/data and get out a simplified output or software product, Bash and other glue codes let you pick and choose, customize, see its innards, test your own idea by typing it and running it in the command line REPL. You continue to refine it until you find a solution, and then you can automate your solution, with scripts, cron, and the like.

Without further adieu, I present some sketches of ideas, recipes and speculative ideas on how to glue together your own alternatives to FAANG and other startup products in the command line. Some of these are easy peasy for those new to the CLI. Others will require a bit more knowledge and experimentation.

Some of these will run on your own computer. For others you'll want to access a server, either because you need to 'sync' with someone(s) else, to store info remotely that can be accessed by multiple people or other reasons. You could join a tilde community or you can...

## Run your own server

For many of these solutions, if you have your own server, either a spare old laptop, raspberry pi, or a remote server, you won't be as reliant on cloud services. 

For an easier-to-configure server for this kind of thing, try yunohost.

[Yunohost](https://yunohost.org)

Setting up a server is beyond the scope of this article, but there is lots of documentation online if you do a search, or read the yunohost website.

### Word Processing

Nano and WordGrinder are simple and attractive text user interface-controlled word processors.

Alternatively, text editors such as Emacs, Vim, Neovim are old faithfuls.

[WordGrinder](http://cowlark.com/wordgrinder/index.html)

[Micro](https://micro-editor.github.io/)

### Live collaborative text editing

Use ttyshare or tmate or even tmux with ssh to create a shared terminal session. Then both open your text editors.

Alternatively, use Vim's server capability.

[Vim: enable server capabiliity](https://vim.fandom.com/wiki/Enable_servername_capability_in_vim/xterm)

### Version control and collaboration (not 'live')

Git or Subversion plus a shared remote server, perhaps one you set up with yunohost.

### Git server

You can use Gitea.

[Gitea](https://docs.gitea.com/)

Or even simpler, bare git on a server, see:

Idiomdrottning's How to host git repos on their Gemlog.

[How To Host Git Repos](https://idiomdrottning.org/hosting-git-repos)

### minimal calendar program

[when](https://www.lightandmatter.com/when/when.html)

### Synced calendar

[khal](https://lostpackets.de/khal/)

### Pick a date

Put a spreadsheet on a server that others have access to editing. Or use email. Or host a form on a server using cgi. Have people select the best option. Schedule an email to you or all at the end date with the results. You could set it up with cron or just mark on your calendar to check back on a certain day.


### Todo list

I save my todo list as a textfile. There's also todo.txt project.

### Radio

Pyradio is excellent.

[Pyradio](https://www.coderholic.com/pyradio/)

### Image editing

Imagemagick is incredible. Lots of recipes are available online.

[ImageMagick](https://imagemagick.org/)

[ImageMagick Recipes](https://github.com/ImageMagick/Usage)

### Image browsing online and offline

I use chafa to browse images in the command line. If I'm going through directories of images I use fff, a vim-like file manager. Pressing i over an image file will open it inline overlaid in the terminal.

[chafa](https://hpjansson.org/chafa/)

[fff](https://github.com/dylanaraps/fff)

The terminal emulator Terminology can also show images inline in the terminal. For example tyls is like the linux ls command setup to display images of all files.

For browsing the web in the command line there are a number of great programs but w3m has the w3m-img plugin that renders image in the command line. Add the -H flag to get 'high quality' images. 

links text browser has the -g flag that enables graphics mode in the command line. 

### Image sharing

I have a simple bash script that generates html image galleries that I host on my web server. I use imagemagick to resize.

cyclenerd has an example called gallery.sh that automates this.

[gallery.sh](https://github.com/Cyclenerd/gallery_shell)

Alternatively you could use nextcloud to share images. I haven't tried yet so you'll have to explore on your own. 

### Social media

If you use mastodon, try toot.

[toot](https://github.com/ihabunek/toot)

twtxt is a minimalist social media protocol like a minimal distributed twitter (sorry for the birdsite comparison!). You can use a web client or browse and post in the command line. 

[twtxt usage](https://twtxt.readthedocs.io/en/latest/user/usage.html)

### File sharing

Looking for a dropbox or wetransfer alternative? Try The Null Pointer

[The Null Pointer](https://0x0.st/)

Or alternatively, upload to your own server. For sharing files on your own server, use scp.

[How to use scp to securely transfer files](https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/)

For backups, rsync.

[automatic backups with rsync](https://www.makeuseof.com/automatically-backup-files-to-with-rsync/)

### Forums

On Ctrl-c club tilde we use the iris command line forum software with hundreds of users on a single shared server. We love it.

[iris](https://github.com/Calamitous/iris)

### Weather

This is a fun category. You can check the weather a few ways.

```sh
curl wttr.in 
```

There are some other options you can pass in too. 

Or use ansiweather.

[ansiweather](https://github.com/fcambus/ansiweather)

## Conclusion

Many of these solutions, systems and recipes are barely more complex than using a cloud service alternative. And they won't be mining your data, selling your info to advertisers, or trying to sell you additional services. With a little bit of elbow grease they can be put to good use. Help is often a search engine query away, or why not try posting on IRC? Many of these programs can be tailored to your own use-case. These programs are almost always free and some take donations. Beyond initial setup (if any), these programs also eschew all of the advertisements, pop-ups alerts and notifications and other cruft that contribute to mental exhaustion while using some of the commercial platforms these programs are replacing. 

This also doesn't need to be an all-or-nothing affair. Pick and choose what works for you. That's the beauty of having access to free and open source software.

I hope you find some solutions to your own needs, and glue together your own software ecosystem. 

