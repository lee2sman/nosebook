---
layout: post
title: How to use Pandoc variables (to create a custom website) 🖻🪄
categories: [open source, programming]
---

## Background

This is a very short tutorial on working with Pandoc variables in markdown. I use this when creating my own static site generators. I'll keep it extremely basic, because I found this info difficult to search for online when I was first starting out.

A website builder is used when you're making a website with a large number of pages, particularly ones that would benefit from template files. I've found that Pandoc, the free, libre and open source document conversion tool, is perfect for scripting my own templated website generator.

I've been working on a site generator recently to build an archive consisting of a landing page with images and titles/descriptions, and each of these link to a separate page that contains details like a title, image, links, descriptions, tags, etc.


![A working draft of Cabinet of Curios]({{"/images/log/curios.webp" | absolute_url}} "A working draft of Cabinet of Curios")  
*Current working draft of an archive site I'm building.*

This is a perfect use-case for a static site generator, which is basically a templating system for building websites. I (once again) thought about using Hugo, and I've used Jekyll a ton. But this past year I built [panblog](https://tildegit.org/exquisitecorp/panblog) due to my own frustrations with those tools. If you're using someone else's webite portfolio design as a design template for your whole site, something like Hugo or 11ty might be much better for you, as there's a lot of templates you can use to build a professional website. 

But I'm building from scratch for a few reasons: I don't want to make corporate-style sites or something that looks like its someone else's site. And I'm trying to build for minimal page load without JavaScript. Even on site builders for more artist-designed sites (like Cargo), I've found their use of a database and Javascript makes the page load unecessarily long. So I prefer this simple-style site that I'm building from scratch. I'm not even using panblog as I think I'm creating something even simpler, and Pandoc itself is perfect for this.

### Basic building blocks

I'm currently building an Archive site consisting of a landing page that looks like a gallery page. Clicking on an individual item should jump to that item's page with its title and description, photo, etc. 

So I need a template html document for an individual item page. 

### Using variables on page templates

Here's how to use variables when using Pandoc to convert markdown to html.

Let's say I have a **template.html**:

```html5
<h1>$title$</h1>
<p>The output file is $outputfile$.</p>
$body$
```

Let's go through each line. This template says to put the variable $title$ inside h1 tags. This is a variable I have to set manually.

Then the following line starts with "This is a template file. The output file is " and then will stick in the name, a filename followed by .html. This will get filled in automatically when you run Pandoc, because it is a [built-in variable](https://pandoc.org/demo/example33/6.2-variables.html). It is not something you manually set.

Finally, the $body$ variable is built-in and means that Pandoc will copy through verbatim any other text from your source file and put it into the outputted html file.

For example, I have an individual post I'm writing **test-post.md**:

```markdown
---
title: My new post
---

This is my test post.
```

This is a markdown post with the variable *title* specified in the [front matter](https://rsdoiel.github.io/blog/2020/11/11/Pandoc-Metadata.html) section enclosed in three undescores each. The body of this new post is the single line "This is my test post."

Now to process and build the page. I run this in the command line:

```sh
pandoc test-post.md --template=template.html -o testing.html
```

So running this command will result in the output file **testing.html**

```html
<h1>My New Post</h1>
  <p>The output file is testing.html.</p>
  <p>This is my test post.</p>
```

The template used the title specified in the front matter, output it between h1 tags. All output files made with this template also include the following line which specifies the output file name, which is not practical, but I just put this in here in case you need to build up a pipeline in your static generator with link names. For example, I am adding in generating [opengraph tags](https://ogp.me/) (so that a preview image and sentence) pop up correctly when posted to social media. Finally, the actual text from the individual post is added on the last line.

Here I should note that front matter variables can only be used in template files. You [cannot place them in individual pages](https://github.com/jgm/pandoc/issues/1950).

### A small pipeline to build a website

If I have a folder of markdown files like **item1.md**, **item2.md**, etc I can create a very simple script like the following:

```sh
touch index.html
for file in *.md
  echo "Processing $file"
  output=(basename $file)
  pandoc $file --template=template.html -o $output.html
  echo "<p><a href="$output.html">$output</a></p>" >> tindex.html
done
```

In this bash script above we have a different style of bash variable. We set with the equal sign, but we get a variable by prefixing it with a single $ dollar sign, which is different than working inside pandoc templates when we surround our variables with a $ dollar sign on each side.

In the script above I start by creating an index.html file that will be the landing page.

Then my script runs a loop through all the markdown files in the directory, gets the basename without the .md suffix, uses Pandoc to process the page with the template file, and save under the output filename consisting of that stripped basename with .html suffix added to the end. 

Lastly, I use echo to output the name of the page onto the index.html, linking to each individual item's page. This is pretty simple and in practice I build on top of these fundamentals to make more complex designed sites.

Beyond this, it's really about adding variables to your frontmatter section, building out your templates, and your input data, adding in navigation bars or anything else needed.

Hopefully this has been helpful to anyone looking to build a simple Pandoc-based site builder and trying to understand the fundamentals of working with variables in Pandoc.

### Resources

* [Metadata and custom templates in Pandoc](https://pandoc.org/MANUAL.html#extension-yaml_metadata_block)
* [Variables](https://pandoc.org/MANUAL.html#variables)
* [Default html template](https://github.com/jgm/pandoc-templates/blob/master/default.html5)
