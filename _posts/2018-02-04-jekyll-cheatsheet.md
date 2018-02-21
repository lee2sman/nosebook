---
layout: post
title:  "Jekyll code snippets and links"
date:   2018-02-04 12:11:05 -0800
categories: programming
---

# About Jekyll, the framework I'm using to publish this site

This Nosebook is technically a sub-site currently of my main [website](http://leetusman.com). It is built with [Jekyll](https://jekyllrb.com/), a framework for creating websites that allow pages to be added over time, like a blog or wiki. Jekyll is a *static site generator*. Each time you create a new file like a blogpost and save and run Jekyll it takes that page, applies a template to it, and then pops out all of the code you need to publish your site using your predefined templates. In contrast, database-driven sites use Javascript and query a server to find the right page to load and serve when someone is looking at your website. Jekyll creates these pages in advance and converts to simple HTML so pages load much faster and don't have the same kinds of security problems that a database-type system may have.

Jekyll aims to be beginner-friendly, and it is if you want to do something simple, but it actually allows quite complex customization. I am running Jekyll on GitHub, using a custom domain, in a subdomain repository. I can edit my files online on GitHub, on my phone, on my computer with any editing software or in the Terminal. I like this flexibility.

New posts are put into a ```_posts``` folder. Their file name should be *YYYY-MM-DD-file-name.md* New pages can be put in the home directory. Posts are written in [Markdown](http://kirkstrobeck.github.io/whatismarkdown.com/) and contain a snippet called *front matter* at the top. This section specifies a page template to use when converting it to HTML, as well as the title, keywords and the date. [Here](https://raw.githubusercontent.com/lee2sman/nosebook/master/_posts/2018-02-04-jekyll-cheatsheet.md?token=AHCT9ExA7jHtTOaU8sBDfNjUW_NKSLYLks5alhaAwA%3D%3D) is this post's markdown file with front matter.

Below I have placed lots of code snippets. These are not general Jekyll snippets. These are specific to my own needs. I often refer to these when I am trying to remember how to do something. These snippets have been collected from around the internet. The Jekyll [documentation](https://jekyllrb.com/) is fine and extensive but does not have a comprehensive section with info on special notes and code you need if you are hosting on a custom domain with a subdomain. There are lots of tricky issues relating to file paths as a result of hosting my site on GitHub. The below snippets may be useful but are otherwise unorganized. If you just want to get started with Jekyll you should read [this](https://jekyllrb.com/docs/quickstart/) Quickstart guide instead. 

Of note, Jekyll's templates are written in [Liquid](https://shopify.github.io/liquid/), an open-source templating language developed by *Shopify*. One challenge I've found is that it can be difficult to integrate blocks of instructional code as well as Liquid template snippets in the same file. I have had to do various workarounds because of this.

# Collected code snippets for use in editing this wiki

# Link to Jekyll Documentation

[Here](https://jekyllrb.com/docs/home/)

# Typical Workflow

1. Create a new file in the _posts folder with naming scheme ```YYYY-MM-DD-file-name.md```. 
2. Copy over the front matter below and change the name, date and keywords.
3. Write the rest of the post. Use the below snippets for figuring out how to add images, links, etc on my subdomain.
4. Save.
5. In the project repository folder (for me that's ```nosebook``` ) run ```jekyll serve --baseurl ''```.
6. Go to ```localhost:4000``` in my web browser and make sure everything looks fine. If not, edit my file again.
7. Add the file in git. Commit it. Push it to the repository. That's it.


```
git add _posts/2018-02-20-file-name.md
git commit -m "added 2018-02-20-file-name.md"
git push
```

# Example Front Matter

```
---
layout: post
title:  "Jekyll code snippets and links"
date:   2018-02-04 12:11:05 -0800
categories: programming
---
```

# Path to images 

For use in Markdown when using a custom domain for your username repo and you have a separate project repo with Jekyll on GitHub pages.

Note: this information is correct as of Jekyll 3.3 - If you try to google an answer to this you get a bunch of not-useful information. Here's how you do it.

#### ![alt text]]({\{"/path/to/image.jpg" | absolute_url}})

# Site preview with Jekyll serve if you have a custom URL

Always do your build in the root folder. Running ```jekyll serve``` throws strange building errors if you run it in the _posts folder for example.

Next section is a tip on maintaining proper permalinks and paths when using a custom domain and subdomain, especially with GitHub pages.

Here I'll explain the proper jekyll serve command if you have that set up. (I do). If you are not using baseurl then you don't need to do this. This is just so the local  serve will render your site properly in the browser so you can check it out before deploying.

```jekyll serve --baseurl ''```

# Set it and forget it: url structure

* I use a custom domain on my github username page: i.e. *github.lee2sman.io* re-routes to [leetusman.com](http://leetusman.com)
* This messes up URL and paths for pages, relative links and CSS path on my repo for this jekyll site

# To fix the URL file structure

1. Open ```_config.yml``` and set ```baseurl``` to ```/project-name``` which here is ```nosebook```
2.  When referencing CSS files in your _layouts directory , use ```{{ site.baseurl}}path/to/css``` which for me looks like ```<link rel="stylesheet" type="text/css" href="{{ site.baseurl}}/css/main.css">```
3.  For links from pages, use this same form. Example, for my link to home \<a href="{\{ site.baseurl }}/">Home</a>
4. For internal links or permalinks, format is exactly this: **{\{ site.baseurl }}{\{ post.url }}**

# Using a post template

In the *front matter* you can set what template to use with ```layout: template-name```. There needs to be a corresponding template with that name in the ```_layouts``` folder.

# Making a direct URL for a post

Instead of the default posted ```/year/month/day/title.html``` you can add a line to the frontmatter to get a direct URL link.

```
permalink: title.html
```

# Where to create Pages (not Posts)

For example, this wiki has an *about.html* which is a page, not a ~~post!~~.

**Very simple!**

2 options:

1. Place named HTML or Markdown files for each page in your site’s root folder.
2. Place pages inside folders and subfolders named whatever you want

When Jekyll runs it will place the page in the root of the _site folder or in a subfolder depending on whether you've placed into a subfolder or not. The permalinks will mirror the subfolder structure.

# Internal links to other posts

[Info here](https://jekyllrb.com/docs/templates/#linking-to-posts)

* useful in case I change my domain/permalinks

# More documentation of Categories

[Categories doc page](https://jekyllrb.com/docs/collections/)

# Things to explore

I'm interested in the Tachyons framework for web prototyping. Some links relating to that below.

* [Tachyons](http://tachyons.io/) - essentially CSS framework and component library
* [Jekyll-tachyons](https://github.com/tachyons-css/jekyll-tachyons) a Jekyll Tachyons boilerplate
* [Jekyons](https://joshosbrn.github.io/jekyons/) - another jekyll and tachyons framework
