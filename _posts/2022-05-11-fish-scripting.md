---
layout: post
title:  "Fish scripting 🐟👩🏿‍💻"
categories: [toolbuilding, programming]
---

*Heads-up: this is an article for programmers on how/why to use fish shell!*

Fish shell is a command line shell and language, meant to be a replacement for Bash, the old but venerable command line and scripting language.

*Update: For reasons why I think the command line is relevant in the current year, see my other posts such as [Why I Use The Command Line](https://leetusman.com/nosebook/why-cli)*.

Fish comes with incredible presets: autocomplete, syntax highlighting, vim-keys, memory of recently-visited folders, even attempts at autocompleting based on man(ual) pages and the like. Yes, you could add on modules to zsh for example to try to build the same ulitiy, but fish shell just works. I find it indispensible for working on art and code on the computer, building design projects, websites, or any other work I want to do. I use it every day.

Fish's goals as a scripting language and shell is to be much easier to use than Bash. I'll push back that even though it is much easier, it still causes me plenty of time looking up how to do things, but the documentation is mostly clear and easy to read.

[Fish shell docs on the web](https://fishshell.com/docs/current/index.html) 

Unlike Bash the command 'set' is used to create a variable in fishscript. Like in Bash, putting a dollar sign is how we get the value of a variable. 

Here I'll walk through a basic script I wrote that runs through access logs on a server to find out how many visitors I've had. Note: It can definitely use further refinement and debugging.

We start by creating a variable access_log and storing the location of a temporary copy of the server access logs. 

```
set access_log ~/.temp.log
cat "/home/gemini/access.log" > $access_log
```

I guess I could have just used the cp copy command but I can't remember why I didn't! No matter. This works.

Then we store the current day, month, year, which we can find using the date Linux program.

```
set day (date +"%d")
set month (date +"%m")
set year (date +"%Y")
```

Now we want to find out the number of the previous month, and whether it's the same year. Basically, if we're in January, we'll need to manually say the previous month was month 12 of the previous year, and if so the year of that month was 1 less than the current year. Otherwise the month is one less than now and the same year. All those p variables below stand for previous. 

```
if test $month -eq 1 
 # check whether current month is jan
 set pmonth 12 #set to dec
 set pyear (math (date +"%Y") - 1) #set to previous year
else
 set pmonth (math $month - 1) #set to prev month
 set pyear $year
end
```

Next we need to find out how many days are in the previous month so we can be use to loop through and check the stats for each days in the month in the previous month that we want to check. I thought I could use a special 'cal' command, but it's not installed on the server. So with some brainstorming I created a list (array, in fish) holding the total number of days for each month. Yes, I sang '30 days has september, april, june and november...' in my head to figure this out. Fish's lists begin their index with 1 instead of 0, like Lua. I am not accounting for leapyear.

```
#              J   F M  A  M  J  J  A  S  O  N  D
set month_days 31 28 31 30 31 30 31 31 30 31 30 31
set total_days_prev_month $month_days[$pmonth]
```

If today is the 17th and I want stats for the past 30 days then I'll want to loop from the 17th of the previous month to the last day of that month. Then I'll want to add in stats for the current month. I do this both for the current $USER running the script as well as for the entire tilde server. I'm making extensive use of grep to read through each line of the file and counting the number of lines that match. This part was like a little puzzle to master the date command, like doing code-Sudoku. 

```
for day_counter in (seq $day $total_days_prev_month)
    set user_subtotal (grep $USER $access_log | grep (date --date=$pyear-$pmonth-$day_counter +"%Y-%m-%d" ) | wc -l)
    set entire_subtotal (grep (date --date=$pyear-$pmonth-$day_counter +"%Y-%m-%d" ) $access_log | wc -l)
end

set user_subtotal2 (grep $USER $access_log | grep (date +"%m") | wc -l)
set entire_subtotal2 ( grep (date +"%m") $access_log | wc -l)
```

Ok we've totaled up the total views for the server and an individual user for past month. Then I print it all out and delete the temporary log file afterwards. Basically, for the entire server I just count the total number of lines, since each line is a report of someone accessing any of our gemlogs. I run a similar line for viewing an individual's total number of viewers but filtering it so it only counts if a user's name is in there (having been accessed). For finding out total viewers today I pass in a search for today's date as well.

```
echo "stats for server"
echo "Views today: " ( grep (date +"%Y-%m-%d") $access_log | wc -l )
echo "Views past month: " (math $entire_subtotal + $entire_subtotal2)
echo "Views for all time: " (cat $access_log | wc -l) # just the total number of lines of the log
echo -e "\nGemlog stats for ~$USER"
echo "Views today: " (grep $USER $access_log | grep (date +"%Y-%m-%d") | wc -l)
echo "Views past month: " (math $user_subtotal + $user_subtotal2)
echo "Views for all time: " (grep $USER $access_log | wc -l)
 
rm $access_log
```

FIN.

So this took me some time to surf around the fish shell documentation but ultimately it wasn't too bad.

And that's how you script a fish.
