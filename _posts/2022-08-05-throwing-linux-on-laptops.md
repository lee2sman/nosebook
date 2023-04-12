---
layout: post
title: Throwing Linux on low power laptops 💻
date: 2022-11-08
categories: [reuse, consumption, organizing]
---

*tl;dr: This post contains some code, instructions and remarks for setting up Linux on a low power laptop*.

![Chromebook booted into GalliumOS]({{"/images/chromebook.gif" | absolute_url}})  
Chromebook booted into GalliumOS, dithered low bandwidth and retro style image

Recently at the request of a student I helped secure her a laptop that she could use in my intro computer science class but that wouldn't cost her any money. My school does laptop loans, but we decided to build up a Linux machine she could use as well. Since I use Linux myself, I thought I'd write a little about it.

I asked friends for suggestions of where to get a near-free functional computer, and I received a suggestion to look in local thrift stores for old Chromebooks. Unfortunately, that's not really a viable option in NYC. There are few thrift stores around, and those that do generally do not sell electronics, much less old Chromebooks. 

But Craigslist is thriving here, and I saw a variety of cheap Chromebooks for sale. Would they be powerful enough to run Processing? I looked online. It looked like it was very possible if I could boot into a Debian-based distro, but it was not definitive. There were some listed options for using a chroot to run Ubuntu, but it appeared slow and everything was years old. I wasn't sure the current state. I also saw a variety of difficult options for installing Ubuntu (or another *buntu on top of ChromeOS). 

How hard could it be? I was particularly interested in showing my student how easy it is to install Linux and how easy it is to use. Ideally it should only take 20 minutes to make a USB drive iso and then boot from that drive and install a light Ubuntu variant, right? 

With a little searching I wasn't filled with confidence as it was immediately clear you can't just flash an ISO to a USB, launch an installer and call it a day. No. For this reason, I decided to install it myself in case I got stuck for hours or days in the process.

Here's my convoluted process.

1. Acquire laptop

I found someone on Craigslist selling a near-new Chromebook for $50. I met up with them at Grand Central, and ended up trading $40 for the laptop. They seemed glad to part with it.

I read a dozen websites and fora trying to come up with a plan. It looks like years ago it was pretty easy to flash Ubuntu and there were many options. Now Google has really locked down the computer. The main approach is to:

* Turn on insecure legacy boot
* Update firmware
* Other stuff

### Steps

Start up the Chromebook and connect to WIFI.

I have a Samsung Chromebook 3 which comes withe Braswell firmware. When I looked it up, I read it must be updated.

I rack my brain and decide I will try to run Linux off an external drive and see if that's viable.

## Turn off secureboot So we can boot off a USB

Procedure:

1. Enable developer mode
2. Turn off verified boot
3. Enable dev usb boot

Details:

### Boot into recovery mode

Press Escape + Refresh key (3 buttons to the right of escape) + Power button. Let go of power and it'll start up in Recovery Mode.

When it starts up it tells me to insert a USB. Nah, not yet. Press Ctrl-D to turn off verified boot. Wait 10 seconds and when prompted I press enter. It'll reboot and asks me to hit enter again to confirm. I make sure it says OS Verification is OFF. Press Ctrl-D again. It begins reflashing my drive and booting into developer mode. It takes about 5 minutes.

### Enable Dev usb boot

Eventually it starts back up and I see the traditional welcome screen on ChromeOS. I skipped signing in and clicked Sign in as Guest in the bottom left so I don't need to make a Google account. 

When I finally get into the desktop environment I open the Terminal with Ctrl-Alt-T. 

I type shell and enter to get a Linux command line.

I switch to bash with root privileges to make changes to booting by typing sudo bash and hitting enter.

I get the typical warning about sudo 'with great power comes great responsibility' mumbo jumbo. I type enable_dev_usb_boot and enter. A success message appears.

### Set up dev boot legacy

I open the terminal with Ctrl-Alt-F2 (right arrow). I login to 'chronos'. No password. I type sudo crossystem dev_boot_legacy=1 and then my prompt. First weird thing occurs. The prompt tells me instead to try dev_boot_altfw instead. Hmm. I run sudo crossystem dev_boot_altfw=1 and get no error so maybe this is alternative firmware and it worked?

### Update firmware

I'm on a Samsung Chromebook 3 which runs Intel Braswell, so I saw it needed its firmware updated. I ran the update firmware automation script from mrchromebook.tech.

```
cd; curl -LO mrchromebox.tech/firmware-util.sh
sudo install -Dt /usr/local/bin -m 755 firmware-util.sh
sudo firmware-util.sh
```

This brings up a menu.

I tried to select 2 Install/Update UEFI Firmware but I couldn't because WriteProtect was enabled since I wasn't able to take off the back of the machine to remove a screw. But I could do 1) and update the current Legacy BIOS firmware.

## Make a flash drive iso

I downloaded a GalliumOS iso even though it's not maintained anymore. I had been thinking I'd download Lubuntu but against my better judgement I decided to try Gallium since it was built specifically for Chromebook. I used Balena Etcher to write the iso to USB.

[GalliumOS](https://galliumos.org/)

### Start up with your USB drive loaded with linux

Once written to disk, I plugged in the USB drive to the Chromebook and start up in recovery mode by pressing Escape + Refresh + Power to start up. 

Press Ctrl-U to start from the USB. Or was it Ctrl-L?

It starts up and I run the installer, which is self-explanatory like picking keyboard, city and the like. It takes just a few minutes. I shut down and remove the USB installer. Fingers crossed....

## Startup

It works! Each time the computer is turned on we need to run Ctrl-L to escape the regular startup process and boot into Gallium.

Once it's started, I have a really nice looking desktop and the machine (despite being pretty low power) is fast! I opened up the terminal and sudo apt updated and sudo apt upgraded. Then I tried out the package manager App Grid Software Center and installed LibreOffice, Solitaire, Tetris and some other software for my student. There was already a variety of basic apps for playing music, displaying images, file manager, etc. I visited the Processing website and downloaded the latest version, 4.0.1 and downloaded it. I used tar to uncompress and then ran the bash installer file. This installed Processing to the desktop and placed its icon in the launcher menu under Development. I wrote a basic Processing Hello World program, tested it ran, and saved it.

Lastly, I downloaded a picture of my college and set it as the desktop background. Before class I presented the computer to my student and she was excited to get it. She began using it that day.

I hope it will be useful for her classes, browsing the web, doing homework and practicing coding in Processing. 


## Other flavors of *Buntu

There are a variety of other Ubuntu-derived free Linux distros.

## Lubuntu

In the summer I was an artist in resident at a museum. There's a drawer with old tech gear, including mixers, speakers and cables. I set up a temp recording studio to work on electroacoustic music with a friend. In a drawer we also found an old computer, a HP Envy, I think from 2010. It has Windows on it, but I had to start up in Safe mode to even try it out because I didn't know the admin password, and the computer didn't have 'service pack 1' installed which prevented the browser from being updated! When I finally got the darn thing running I saw it had Windows 7. Okay! So my next step: wipe the computer and put a new Linux OS on it. But which one?

Since the laptop I found is 13 years old, I needed a lightweight distro. I wanted the computer useable by friends here without any previous Linux experience, and I didn't think a minimal tiling window manager like i3 would be a good experience for them. So I thought I remembered that Lubuntu was the lightweight Ubuntu - so should I try that? 

> The project’s goal is to provide a lightweight yet functional Linux distribution based on a rock-solid Ubuntu base. Lubuntu provides a simple but modern and powerful graphical user interface, and comes with a wide variety of applications so you can browse, email, chat, play, and be productive. Lubuntu was formerly a distribution for low-end hardware, but we have refocused.

I downloaded the iso, wrote it to usb with dd, plugged it into the laptop and restarted. In a minute it was up and running. I double clicked the installer and about 10 minutes later I was up and running. I had never used Lubuntu before, which comes with Openbox as its window manager, which I don't think I've used before. But it was obvious what to do: Open the menu in the bottom left. I found the menu categories and built-in basic apps pretty usable. I found the qt-terminal, sudo apt updated and sudo apt upgraded, quickly downloaded some basic programs (neovim, curl, w3m, tldr, kate, kitty, amfora, can't remember what else) and some basic art/music programs (krita, audacity, puredata, rhythmbox, love2d).

For a 13 year old laptop, the thing is fast. Installing with aptitude is almost as quick as my much more modern laptop. This old clunky computer practically flies. Because I've used Ubuntu so long I didn't feel like I needed to learn anything. I have two complaints so far that I haven't solved: it's not obvious to me how to pin programs to the built-in taskbar. And I Can't seem to get the keyboard keys for special characters to match up with the character printed on the key. My guess is because I use english and this is a european keyboard, but when I tried to switch to danish I still had an issue. It's not an issue for me (i write in Dvorak anyway), but I can tell it's confusing to the other artists here that I am showing Linux too. One person used it in a web workshop I taught and was a little confused looking for forward slash, brackets and the like. But those are the only issues I've had so far. Sound works great. The audio interface I plugged in seemed to work fine. And everything looks pretty nice.

Would recommend!

[Lubuntu official site](https://lubuntu.me/)  
[Lubuntu on Wikipedia](https://en.wikipedia.org/wiki/Lubuntu)
