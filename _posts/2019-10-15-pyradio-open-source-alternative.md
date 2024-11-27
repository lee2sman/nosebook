---
layout: post
title: "PyRadio: An open source alternative for internet radio"
date: 2019-10-15 18:00:30 -0800
categories: [programming, art, tools]
---

*Note: this article was originally written by me and [published on OpenSource.com](https://opensource.com/article/19/11/pyradio) CC BY-SA.*

[PyRadio](http://www.coderholic.com/pyradio/) is a convenient, open source, command-line application for playing any radio station that has a streaming link. And in 2019, almost every radio station (certainly, every one that has a web presence) has a way to listen online. Using the free PyRadio program, you can add, edit, play and switch between your own selected list of streaming radio stations. It is a command-line tool for Linux that can run on many computers, including Macintosh and tiny computers like Raspberry Pi. To some, a command-line client for playing music might sound needlessly complicated, but it\'s actually a simple alternative and one that serves as an instant text-based dashboard to easily select music to listen to. 


A little background about myself: I spend a lot of time browsing for and listening to new music on [Bandcamp](http://bandcamp.com), on various blogs, and even Spotify. I don\'t spend time casually listening to app *radio* stations, which are really algorithmically-generated continuous streams of similarly tagged music. Rather, I prefer listening to non-profit, college and locally-produced independent radio stations that are run by a community and don\'t rely on advertisements to sustain themselves.

I have always been a huge fan of community radio, from Drexel University\'s great reggae weekends on WKDU; the uncanny experimental WFMU from Orange, N.J.; and WNYC\'s eclectic schedule, including New Sounds. In my college days, I was a DJ on Brandeis\' WBRS 100.1FM, playing experimental electronic music on the show Frequency. And as recently as 2018, I helped manage the station managers and schedule for [KCHUNG Radio](https://kchungradio.org/), an artist-run internet and low-power AM station run out of Chinatown, Los Angeles.

![The PyRadio interface](https://opensource.com/sites/default/files/interface_0.png "The PyRadio interface").

Just as a car radio (in days of yore) had buttons with presets for the owner\'s favorite radio stations, PyRadio lets me create a very simple list of radio stations that I can easily turn on and switch between. Since I spend most days working, researching, or writing to music, it\'s become my go-to software for listening. In an era where many people are used to commercial streaming services like curated Spotify mood playlists or Pandora \"stations,\" it\'s nice to be able to set my own radio stations from a variety of sources outside of a commercial app and sans additional advertising.

Importantly, by not using commercial clients in the cloud, nothing is sending my user data or preferences to a company for whatever purposes they see fit. Nothing is collecting my preferences to build a profile to sell me more things.

PyRadio just works, and it\'s easy to use. Like some other Linux software, the hardest part of using PyRadio is installing it. This tutorial will help you install and run PyRadio for the first time. It assumes some basic knowledge of the command line. If you have no experience working in the terminal, I recommend reading a beginner-friendly [introduction to the command line](https://www.redhat.com/sysadmin/navigating-filesystem-linux-terminal) first.

## Installing PyRadio

In the past, I\'ve used the Python package installer [pip](https://pypi.org/project/pip/) to install PyRadio, but the latest version is not yet installable from pip, and I couldn\'t find a package on Homebrew for my Mac. On my laptop running Ubuntu, I really wanted the latest version of PyRadio for its excellent new features, but I couldn\'t find an installation on Apt.

To get the current version on these computers, I built it from source. You can download the latest release from [github.com/coderholic/pyradio/releases](https://github.com/coderholic/pyradio/releases), and then unzip or [untar](https://opensource.com/article/17/7/how-unzip-targz-file) it. Change directory into the PyRadio source folder, and you\'re ready to begin.

Install the dependencies using your distribution\'s package manager
(such as **dnf** on Fedora or **apt** on Ubuntu):

* python3-setuptools
* git
* MPV, MPlayer, or VLC

On a Mac, install [Git](https://git-scm.com/), [sed](https://www.gnu.org/software/sed/manual/sed.html), and [MPlayer](http://www.mplayerhq.hu/design7/news.html) dependencies using Homebrew:

``` bash
brew install git
brew install gnu-sed --default-names
brew install mplayer
```

Once all dependencies are resolved, run the installer script, using the
argument **3** to indicate that you want PyRadio to build for Python3:

``` bash
$ sh devel/build_install_pyradio 3
```

The installation process takes about a minute.

## Using and tweaking the station list

To launch the application, just run **pyradio**. You can navigate up and down the default station list with the arrow or [Vim](https://www.vim.org/) keys and select a station with Enter. The artist name and track title currently streaming from the station should be displayed, if they are available. Typing **?** brings up a help text box that lists available commands. You can change the interface color themes with **t** or modify your configuration with **c**.

Out of the box, PyRadio comes with an extensive list of internet streaming stations. But I wanted to add my favorite public radio and college radio stations to the list, as well as some online music playlists. You can find streaming URLs on your favorite radio stations\' websites or by browsing online station directories such as [Shoutcast](https://directory.shoutcast.com/). In particular, I recommend the variety of excellent stations from [Soma FM](https://somafm.com/). You\'ll need to input the station\'s streaming playlist file, a URL that ends in **.pls**. You can also enter direct links to streaming audio files, such as MP3s.

The easiest way to add a station is to type **a**. PyRadio will ask you for the name of the station and its streaming URL, and you can press Enter to add it to your **stations** file. To delete any station, navigate to it and press **x**. You\'ll be prompted to confirm. The default station list is stored in **\~/.config/pyradio/stations.csv**. The station list is a two-column CSV file with the station names and the stream URLs.

![Adding a station to PyRadio](https://opensource.com/sites/default/files/pyradio-add.png "Adding a station to PyRadio").

Those are the basics of PyRadio. You can find additional information in its [GitHub repo](https://github.com/coderholic/pyradio). I hope you have many hours of audio enjoyment ahead of you. If you have any other PyRadio tips or suggestions for stations, please leave a comment below.

*Note: You can't leave a comment in this archived version originally published on OpenSource.com and republished here*.
