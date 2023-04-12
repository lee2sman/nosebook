---
layout: post
title: Computer Systems as Social Networks 🖥️
date: 2021-02-12
categories: programming
---

## Setting up a tilde server for a small group of Linux beginners 

This semester I'm teaching a computer science class called "Social Software." Some of the topics we are studying include open source software, version control, collaboration project teamwork, working with servers, a history of social software, early networking, Linux, and experimental and esoteric social media.

The first few weeks we looked at predecessors to social media and social software from the pre-internet era such as telegraphs, radio call-in shows, personals ads and the like. We moved into looking at early networking such as Community Memory, the proto-message board set up in Berkeley in the 70s, and about timesharing, the era when large mainframe computers would have maybe dozens of connections from remote 'dumb terminals' where people would log in to run programs on the shared computer system.

We also talked about the finger protocol and I demonstrated ssh, finger, and moving around and working with a Linux system. Then I introduced the idea of a tilde server and we talked about what that is.

With that, I let students request a login username, then gave them a complex password, and showed them how to login via ssh on the classroom computers (Macs) or via Git-Bash on Windows.

### Creating the server

I looked for a free server such as the Google Cloud Compute, but I couldn't find a free tier price that allowed 20 users (unless I'm mistaken). Alternatively, I could and probably should have set up a server on a Pi or other old computer. Instead, I signed up to create the cheapest instance I could find, which looked to be $2.50 monthly on vultr.com, cheaper than Digital Ocean for example. They have you add money to your account, which I believe was $10 minimum, so I added this amount, selected their cheapest plan, and created a "cloud compute" instance. I want to point out that with the estimated usage amount I have, my plan will actually work out to about $6 a month. I don't know why it's higher but caveat emptor. I've filed a ticket to request an explanation and will update this once I get a useful response.

(update 2021-09-27: Vultr responded that only their Atlanta data center allows for $2.50 monthly service, and that often it is 'sold out.' This information is not stated on the signup page, nor even on any FAQ page. The customer service response was fairly rude (my email wasn't), and I will probably not use Vultr again).

When you create the server there are lots of OS choices, including Arch, Debian, Ubuntu, and many other choices. You can also choose the server location. I chose Ubuntu 20.04 since I have a lot of experience with that and wanted things to work quickly and be able to debug myself without having to do much searching when setting up for my class. I selected a New Jersey data center, the closest to my own school's location.

### Logging in as root and setting up 

After about 10 minutes the server had been initialized and I had a generated complex root password. Vultr has a web-based virtual 'console' I used, which fired up a Terminal shell and had a prompt for me to enter my root password, which I entered. 

I did the standard update procedure.

```
sudo apt update
sudo apt upgrade
```

I like to edit text files with Neovim, so I installed it with sudo apt install nvim. For my students they should definitely learn nano instead, so I installed sudo apt install nano.

Some people think you should learn to drive manual before driving automatic. Some think you should learn music theory before doing improv. Some think you should learn Bash before trying a shell with completion like Fish. I certainly do not think that. In fact, I think fish shell is a great way to quickly pull in Linux newbies who could get stymied by a shell. 

```
sudo apt install fish
```

Other things I installed:

```
sudo apt install bsdgames fail2ban finger cowsay figlet python ansiweather w3m sl
```

Out of all of these, fail2ban is essential (to prevent hacker/bot attacks).

Set up timezone.

```
timedatectl set-timezone America/New_York
```

Great, we're in business.

### Security: Setup fail2ban and remove root login

I used rlafuente's started jail.local file

```
sudo apt install fail2ban
wget https://tilde.pt/~rlafuente/files/jail.local
sudo mv jail.local /etc/fail2ban
```

I cd'ed to the fail2ban folder and edited the jail.local file. I commented out the apache stuff since I'm not running an apache/web-server.

To test:

```
fail2ban-server --test
```

If all works okay, launch it now and it will launch each time server starts up:

```
sudo systemctl start fail2ban
```

I also turned off the ability for root to login remotely.

In the file /etc/ssh/sshd_config you should find the line PermitRootLogin and change it to no (or add this line if it didn't exist). Save.

You can always check attempted connections to your server via 

```
cat /var/log/auth.log | grep Failed
```

### Setting a Message of the Day

I edited the /etc/motd/

```
#!/bin/sh

echo "Who is logged in?\n"

users | tr ' ' \\n | uniq

Hello and welcome to anti-soft.

This is a single computer ("in the cloud") that we are all sharing together. 
This is a fun Linux server for exploration and learning. There are lots of resources online for learning about Linux. 

TIP: If you get stuck, you can cancel out of many commands with Control-C or force quit/exit is Control-D.

To log out of anti-soft, type exit at the prompt.

Run "getting-started" for a list of software and commands to try.
```

### Adding custom starter functions for all

I added two custom functions for all users on the system. Fish functions (the equivalent of Bash aliases) need to be installed inside /etc/fish/functions for all users to be able to access them by default.

getting-started is a cheatsheet of beginner linux commands and specially installed software on the server.

getting-started.fish

```
function getting-started 
    echo "cd <foldername> to jump to a directory or cd .. to go back (and cd by itself to go home)
    ls to list files in current directory
    pwd to display current directory (aka folder) name
    cat <filename> prints out a file
    touch <filename> creates a new file
    nano <filename> edits a file
    man <command> displays the manual for a command. arrows to scroll. q to quit.
    mkdir <directory-name> creates a folder (directory)
    rm <filename> deletes a file permanently (careful!)

    Read any Linux resource for more info on basic linux commands.

    Special for our server:
    who  - lists everyone currently logged in
    wall \"my message\" - broadcasts your message (and Control-L to clear screen of messages)
    write <username> - starts a direct live message
    cowsay "my message" - for important announcements
    sl - When you type ls backwards
    figlet - for creating banner images
    weather - fetch a 5 day weather forecast for Purchase, in fahrenheight
    w3m <url> - web browser
    python - the programming language
    finger <username> - displays info on a user
    fish - our shell (already running)

    We also have many games installed: adventure, arithmetic, atc, backgammon, battlestar, bcd, boggle, caesar, canfield, countmail, cribbage, dab, go-fish, gomoku, hack, hangman, hunt, mille, monop, morse, number, pig, phantasia, pom, ppt, primes, quiz, random, rain, robots, rot13, sail, snake, tetris-bsd, trek, wargames, worm, worms, wump, wtf 
    "
end
```

weather.fish

```
function weather
  ansiweather -l "Purchase, NY" -u imperial -s true -f 5 -d true
end
```

### Turn on ssh

```
sudo ufw allow ssh
sudo ufw enable
```

This turns on ssh as well as the firewall.

You could make changes to /etc/ssh/sshd_config as well to configure security and connection settings such as if you require folks to login with a public-private key pair instead of a password.

### Add users

When a user gets created they will have a folder on the server. I want each person to have a hello.txt file ready and waiting for them. So I added the skeleton file inside /etc/skel/. Files in this directory will be copied to a home directory each time a user is created.

/etc/skel/hello.txt

```
Hello and welcome to anti-soft tilde server

Programs to try out:

cowsay
figlet
and many more. 
Message your admin ~lettuce with requests for other software.
```

All of my students were asked for their preferred username. 

Then I created new accounts for each of them, along with a complex password. I added them 

```
adduser <username>
```

When prompted I created a hard password and wrote it down and handed the password to my students. They are free to change it themselves later. 

I wanted students to have fish shell by default. Since I installed it already on the server, I just had to change their default shell. This probably should be automated, but I only have 20 students so typed up and changed their name and then hit enter, 20 times.

```
chsh --shell /usr/bin/fish <username>
```

### Make yourself an admin

Are you still logged in as root? Let's make a new account and make it an admin.

Create yourself as a user as above. Then in addition change your permissions:

```
adduser <my-name>
chsh --shell /usr/bin/fish <my-name>
sudo usermod -a -G sudo <my-name>
```

This will add you to the sudoers.

Now is a good time to exit from the web console and try ssh'ing in as your new admin username if you haven't already.

## Activity: Finger someone

Finger was one of the THE original computer-based 'social media.' 

To view info on someone, finger <username>

Or to view a remote user: finger jroig@finger.farm

To set up your own finger profile and plans and project: chfn (aka, change finger)

Then create plaintext files at either or both ~/.plan ~/.project. They will be added to your profile when someone fingers you.

## Chat locally

See who is logged in with the who command.

Post a message for everyone to see who is logged in:

```
wall "my message"
```

People will be interrupted and can clear it with Control-L or Control-C to escape out.

To start a dialog with one other user logged in,

```
write username
```

Thereafter you can just type and hit enter and messages will be delivered between you.

### And explore further

You could add html and gemini hosting and many other pieces of software.

Additional custom software can be added to /usr/local/bin.

I encouraged my students to test out all of the bsdgames, create and edit files, leave messages for each other, and just generally mess around.

Note that I did not add apache because I did not run a web server (students already have free webspace on campus).

Good luck. Have fun.

# Sources and Links

Some information drawn from:

[The Origin of the Finger Command](https://groups.google.com/g/alt.folklore.computers/c/IdFAN6HPw3k/m/Ci5BfN8i26AJ?pli=1 )  
[HOWTO setup a Tilde server on a Raspberry Pi](https://tilde.pt/~rlafuente/docs/howto-tilde-rpi/)  
[Setting Up Your Own Tilde Club](https://www.edwinwenink.xyz/posts/47-tilde_server/)  
[What Are Tildes and How You Can Use Tilde Computing](https://journal.tildeverse.org/entries/what-are-tildes-and-how-you-can-use-tilde-computing)  
[Tildeverse Zine Issue 1](https://zine.tildeverse.org/issue-1.html)  
[Community Memory](https://en.wikipedia.org/wiki/Community_Memory)  
