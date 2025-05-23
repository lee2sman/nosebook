---
layout: post
title: RIP Pocket - Exporting and downloading articles after the end of Mozilla Pocket 🗞️🎒
categories: [open source, programming]
---

Today Mozilla made an [announcement](https://getpocket.com/farewell) they're winding down Pocket. Pocket was originally Read-It-Later, a browser extension from 2007 that saved articles for later reading, and then rendered them through Reader mode. I used to use Read-It-Later and was bummed when they were sold as I knew that the service would change. 

Sure enough, Mozilla added on some options. Thankfully they left alone the basic service for free, but offered freemium services that let you change the font and other display items. In the past couple years Mozilla started to offer alternative article suggestions on the landing page, which I **never** found useful. Think listicle type articles.

> While Pocket is shutting down, Mozilla continues with our commitment to high-quality content recommendations in Firefox. We take an “algotorial” approach to curating the best of the web for the millions of users who make Firefox their window to the internet. We use machine learning algorithms to scour the internet for high quality content that will appeal to Firefox’s large and diverse user base, while relying on a human editorial team to provide oversight to ensure that the recommendations on Firefox New Tab are trustworthy, engaging, and high quality.

Gross. I'm not looking for 'algotorial'. I'm assuming they had some business model in mind with that part such as advertorial placement, perhaps selling analytics. I don't know. The core service: saving articles for reading later in a clean interface is all I wanted. Maybe you could focus on that? 

So several years ago I made [Bookmobile](https://tildegit.org/exquisitecorp/bookmobile), a command line tool that takes article URLs and processes an article with Reader mode and exports simplified html, markdown, re-themed html/css or epub files depending on whether you want to read on an ebook reader, your computer, or what-have-you. While not as easy as an integrated browser button to save articles, Bookmobile works well enough. I've used it for years. The main reason I continued to use Pocket was because my Kobo ebook reader that I purchased last summer has Pocket integrated, which allows wifi based loading of new articles. Without that, I believe I have to download my articles saved through Bookmobile to my hard drive, then move them to the Kobo's microSD card and plug them into the Kobo. It's not the end of the world, but it is a couple extra steps.

I just want to point out there is [Wallabag](https://wallabag.org/), a Pocket-like alternative that has a hosted service as well as open source self-hosted versions and can work with feed readers. I do not believe that works on my e-reader, but it is an intriguing tool.

With the announcement of Pocket's winding down I decided to build a bulk article downloader using Bookmobile. You can request an [export](https://support.mozilla.org/en-US/kb/exporting-your-pocket-list) of your Pocket list, which comes as a downloadable CSV data file consisting of article titles (sometimes), URL of each article, and maybe your tags. 

My script runs through your list of articles and exports them in mass. Unfortunately, Pocket isn't giving up their copies of the saved articles, so if an article is missing from the web now, my program won't be able to retrieve it (unless I figured out a simple way to add in Wayback machine mode I guess). 

My [convert-pocket](https://tildegit.org/exquisitecorp/bookmobile/src/branch/pocket-export/convert-pocket.fish) script is online in a git branch and ready for use by commandline programmers. It requires downloading Bookmobile to run, which has dependencies on pandoc and rdrview. I may go back and build more documentation and tooling if anyone requests it, but for now I think it's okay as is.

## Steps to download your articles from Pocket using Bookmobile and the Convert-Pocket script

### Setup

1. [Download Bookmobile](https://tildegit.org/exquisitecorp/bookmobile/)
2. Install needed programs fish shell, pandoc, and rdrview if needed. All are available in most Linux distributions and Mac via Homebrew. If needed, these can also be built from source.
3. Download the [Convert Pocket](https://tildegit.org/exquisitecorp/bookmobile/src/branch/pocket-export/convert-pocket.fish) script and place in the Bookmobile directory.
4. Request an [export](https://getpocket.com/export) of your Pocket articles. It will send you a link to download a zip file. Open that up and save to the Bookmobile directory.

By default, the Convert Pocket script will download and convert each article to a local reader-mode html file. If you want to instead save the files as epub for an ebook reader, be sure to change line 27 to:

```fish
    ./bookmobile $line --format epub --output pocket-articles/
```

Other options include *html*, which saves the original html file unchanged (not reader mode), and *markdown* which saves a simplified markdown file.

### Bulk download

Run the Convert pocket script from the bookmobile directory. It will create a *pocket-articles* directory and place the downloaded article files in there.

```sh
fish convert-pocket.fish pocketfile.csv
```

Replace pocketfile.csv with the name of your data file of articles.

If you have a lot of articles it could take a VERY long time. Bookmobile is verbose so you'll see each step it takes and whether it's successful at finding the article and converting it or not.

I hope this was useful for someone. It was certainly very useful for me.

## How it works

The first step was to parse Pocket's export data file, which consists of a comma-separated file with headers. Parsing data is not trivial and warnings about parsing abound on the internet. I noticed the CSV file sometimes had titles for articles and other times it didn't. So I couldn't just grab the second comma-separated value on each line for example. When I posted about this to Mastodon Darius Kazemi gave me the suggestion of just splitting the CSV file by comma first. So I did that, and then just save lines beginning with http in the resulting list.

```fish
cat $argv | sed 's/,/\
/g' | grep 'http*' | uniq > list.txt
```

Then I created a list out of those article URLs.

```fish
set a (string split " " (cat list.txt))
```

And finally we process them.

```fish
mkdir -p pocket-articles
 for line in $a
   echo -e "\nProcessing $line..."
   ./bookmobile $line --format reader --output pocket-articles/
end
```

This iteratively runs through our list saving the reader html version of all of the articles to our pocket-articles folder. 

Bookmobile is [available online](https://tildegit.org/exquisitecorp/bookmobile), along with [Convert Pocket](https://tildegit.org/exquisitecorp/bookmobile/src/branch/pocket-export/convert-pocket.fish).
