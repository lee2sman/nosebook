---
layout: post
title:  "Jekyll code snippets and links"
date:   2018-02-04 12:11:05 -0800
categories: programming
---

# Some coding snippets for me to control this wiki

### Link to [Jekyll Documentation](https://jekyllrb.com/docs/home/)

* These are all Jekyll snippets

# Path to images in Markdown when using a custom domain for your username repo and you have a separate project repo with Jekyll on GitHub pages

Note: this information is correct as of Jekyll 3.3 - If you try to google an answer to this you get a bunch of not-useful information. Here's how you do it.

### ![alt text]]({\{"/path/to/image.jpg" | absolute_url}})

# Site preview with Jekyll serve if you have a custom URL

Next section is a tip on maintaining proper permalinks and paths when using a custom domain and subdomain, especially with GitHub pages.

Here I'll explain the proper jekyll serve command if you have that set up. (I do). If you are not using baseurl then you don't need to do this. This is just so the local  serve will render your site properly in the browser so you can check it out before deploying.

```jekyll serve --baseurl ''```

# Set it and forget it: url structure

* I use a custom domain on my github username page: i.e. *github.lee2sman.io* re-routes to [leetusman.com](http://leetusman.com)
* This messes up URL and paths for pages, relative links and CSS path on my repo for this jekyll site

## To fix:

1. Open ```_config.yml``` and set ```baseurl``` to ```/project-name``` which here is ```nosebook```
2.  When referencing CSS files in your _layouts directory , use ```{{ site.baseurl}}path/to/css``` which for me looks like ```<link rel="stylesheet" type="text/css" href="{{ site.baseurl}}/css/main.css">```
3.  For links from pages, use this same form. Example, for my link to home ```<li><a href="{{ site.baseurl }}/">Home</a></li>```
4. For internal links or permalinks, format is exactly this: **{\{ site.baseurl }}{\{ post.url }}**

# Front Matter

## My basic frontmatter

```
---
layout: post
title:  "Jekyll coding cheatsheet"
date:   2018-02-04 12:11:05 -0800
categories: programming
---
```

## Using a post template

In the *front matter* you can set what template to use with ```layout: template-name```. There needs to be a corresponding template with that name in the ```_layouts``` folder.

## Making a direct URL for a post

Instead of the default posted /year/month/day/title.html you can add a line to the frontmatter to get a direct URL link.

```
permalink: title.html
```

## Where to create Pages (not Posts)

For example, this wiki has an *about.html* which is a page, not a ~~post!~~.

**Very simple!**

2 options:

1. Place named HTML or Markdown files for each page in your site’s root folder.
2. Place pages inside folders and subfolders named whatever you want

When Jekyll runs it will place the page in the root of the _site folder or in a subfolder depending on whether you've placed into a subfolder or not. The permalinks will mirror the subfolder structure.

## Internal links to other posts

[Simple!](https://stackoverflow.com/questions/4629675/jekyll-markdown-internal-links#9195560)

* useful in case I change my domain/permalinks


## More documentation of Categories

[Categories doc page](https://jekyllrb.com/docs/collections/)

# Things to explore

* [Tachyons](http://tachyons.io/) - essentially CSS framework and component library
* [Jekyll-tachyons](https://github.com/tachyons-css/jekyll-tachyons) a Jekyll Tachyons boilerplate
* [Jekyons](https://joshosbrn.github.io/jekyons/) - another jekyll and tachyons framework
