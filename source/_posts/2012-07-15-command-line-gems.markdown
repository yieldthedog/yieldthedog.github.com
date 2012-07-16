---
layout: post
title: "command line gems"
date: 2012-07-15 13:44
published: false
comments: true
categories: command line, linux, zsh, productivity
---

As a long time command line lover I have gather a lot of little tools that help me out through the day (and night).


##[ssh-copy-id](http://linux.die.net/man/1/ssh-copy-id)
This is one of my favorites and seems to be rather unknown. `ssh-copy-id` helps you to distribute your public keys on remote servers. No more scp-ing, ssh-ing and chmod-ing and wondering what you have forgotten when passwordless ssh does not want to work. If you live on a Mac you have to `brew install ssh-copy-id`.

##[htop](http://htop.sourceforge.net/)
`htop` greatly improves the old `top` command with easy sorting and scrolling abilities and a much nicer _UI_

##[iftop](http://linux.die.net/man/8/iftop)
`iftop` displays bandwith usage on an interface. E.g. `sudo iftop -i eth0`

##[oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh/)
Oh-my-zsh lets you easily customize your _ZSH_. If you do not use _ZSH_, change your life with `chsh -s /bin/zsh`

##[awk](http://www.grymoire.com/Unix/Awk.html)
ack is a tool like grep, optimized for programmers, see [betterthangrep](http://betterthangrep.com)

##[kill -9](http://linux.die.net/man/1/kill)
Send _KILL_ signal to process

##ctrl+r
Lots of command line users do not know the __reverse search__ with <kbd>CTRL</kbd> <kbd>r</kbd>. Even more do not know that you can hit it __more than once__ if the first match is not the one you were looking for.

##!!
repeat the last command. This is espacially useful if you forgot to `sudo`.

##ssh -f user@host -L LOCAL_PORT:localhost:REMOTE_PORT -N –g
create an ssh proxy

##[sox](http://sox.sourceforge.net/)
the Swiss Army knife of sound processing programs

##[disown -](http://linux.about.com/library/cmd/blcmdl1_disown.htm)
disown a process and let it run after you locked out of a session

##[lsof](http://linux.die.net/man/8/lsof)
list open file handles

##man ascii
list _ASCII_ table in octal, decimal and hexadecimal

##<kdb>alt</kdb> <kdb>.</kbd> , $!, $*
Get the last argument of the last command with <kdb>alt</kdb> <kdb>.</kbd> or $!. <kdb>alt</kdb> <kdb>.</kbd> can be pressed multiple times to skip through the history. If you want to get all arguments from the last command you can use `$*`.

##python -m SimpleHTTPServer 8080 - serves current dir
creates a simple http server

##[strace](http://linux.die.net/man/1/strace)
strace is a power debugging utility for Linux and some other Unix-like systems to monitor the system calls used by a program

##[mplayer](http://www.mplayerhq.hu/design7/news.html)
command line media player with a great feature set and minimal footprint

##units --- man units
convert units

##[Zcat, Zless, Zgrep, Zdiff](http://www.thegeekstuff.com/2009/05/zcat-zless-zgrep-zdiff-zcmp-zmore-gzip-file-operations-on-the-compressed-files/)
you do not have to extract an archive of a log if you want to take a short look into it, just use `zless`and `zgrep`

##kill - pause and continue
you do not have to always kill a process and restart it, kill can pause and start processes, too:

`kill -STOP PID #to stop`   
`kill -CONT PID #to continue`

##[ipcalc](http://linux.die.net/man/1/ipcalc)
perform simple manipulation of IP addresses

##[watch](http://linux.die.net/man/1/watch)
watch – execute a program periodically, showing output fullscreen

e.g.: `watch -d -n 1 "netstat -an | grep :8080"`

##[multitail](http://linux.die.net/man/1/multitail)
if one `tail -f` is not enough

##[z](https://github.com/rupa/z/)
tracks your most used directories, based on 'frecency'.


