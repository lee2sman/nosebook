---
layout: post
title:  "Jekyll code snippets and links"
date:   2018-02-04 12:11:05 -0800
categories: programming
---

# Some coding snippets for me to control this wiki

### Link to [Jekyll Documentation](https://jekyllrb.com/docs/home/)

* These are all Jekyll snippets

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
