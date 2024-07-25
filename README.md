Nosebook
========

This is the repo for my nosebook.

The 👃📓 site was originally intended as a personal wiki for online research, tutorials, notes and ideas. And now it's transformed into a space for me to share my writing and tutorials in a digital notebook – a personal collection of writing by [Lee Tusman](http://leetusman.com), an artist, curator, programmer, organizer working on artwork, websites-as-works, games, experimental and speculative software and artware, bots, radio and more. My interests include DIY creative community and how it lives online; tools for experimental digital artmaking; generative art; socially-engaged software; artist-run spaces; new forms of performance, collage; and sharing knowledge in a community. Send me your blogs/wikis as well!

This site is built in Jekyll on GitHub by [Lee Tusman](http://leetusman.com).  
All content is [Creative Commons CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

Allways under construction.  
![under construction gif](/images/construction.gif)

## Reinstalling ruby/gems/bundler when this thing breaks every 6 months

this worked as of july 2024

1. Move Gemfile and Gemfile.lock to old.Gemfile and old.Gemfile.lock
2. ```sudo gem install bundler jekyll minima``` (i had to run this a few times. it failed once or twice. argh)
3. ```bundle install```

Then it worked to do: ```bundle exec jekyll serve --baseurl '' ``` (what a pain. switch to eleventy?)
