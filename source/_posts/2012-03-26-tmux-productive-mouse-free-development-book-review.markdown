---
layout: post
title: "tmux - productive mouse free development - book review"
date: 2012-03-26 22:04
comments: true
categories: tmux, terminal, linux
published: false
---

{% blockquote from the tmux homepage, http://tmux.sourceforge.net/%}
tmux is a terminal multiplexer: it enables a number of terminals (or windows), each running a separate program, to be created, accessed, and controlled from a single screen. tmux may be detached from a screen and
continue running in the background, then later reattached.
{% endblockquote %}
<!-- more -->

##A love hate relationship - a brief history

A while ago I installed tmux on my Ubuntu box and gave it a try. As always I immediately over used it's functionality and ended up with a splitted screen with about eight panes. Each pane was too small to be of much use and I refused to use windows, because I thought that I have my terminal tabs for this. The multiple panes were great, I could easily switch between them, thanks to some keyboard shortcuts, that I copy and pasted blindlessly into my tmux conf. I got everything I needed. At least I thought so.

I know that I will get a good beating for the next sentence, but still it's the truth: I'm a hybrid keyboard and mouse user. So the first shock was pre-grogrammed. How can I use the mouse to scroll back, _f**k_, there's no way. Next one: Ah, I'd like to mark this passage with my mouse and ... - _f**k_ - the selection goes right over the other panes. Ok lets rearrange those panes, so I can mark and copy this line and paste... - _f**k_ - I cannot paste with the middle mouse button.

You get the story. The beginning of my tmux relationship didn't have stumbling blocks, but giant boulders. I was rather frustrated and the drawbacks were greater than the advantages. I gave up, end of story.

The really hard thing in the beginning is, that there is no good beginners documentation out there. You find a lot of ultimate tmux.confs, but there is nothing out there that gets you started.

##A letter from Andy

So I let tmux live it's own life, until recently a letter from PragProg arrived, advertising «tmux - productive mouse free development» by Brian P. Hogan. PragProg had a link to this [inspiring video](http://youtu.be/JXwS7z6Dqic), that showed me, how easy it was to accomplish things with tmux. In this video Brian removes his hands so sporadic from the home row and still shows how to do the basic tmux commands - amazing.

<iframe width="640" height="480" src="http://www.youtube.com/embed/JXwS7z6Dqic" frameborder="0" allowfullscreen></iframe>

The book was quite cheap, so I thought: tmux, you get one last try, if you let me down again, you will go to hell.

##Starting slow

Like in Vim it's important to start slow. As you can not remember all commands at once, you need to focus on the basic stuff, that gets you going. Copy and pasting stuff gets you nowhere, as long as you do not understand, what it's for. Brian acknowledges this fact and starts by showing how to create new sessions, windows and panes. No crazy shortcuts just plain tmux commands. What I especially liked was the summary of the commands at the end of each chapter. This helped a lot, when I went back to a chapter to look up a command.

Next he introduces you to the `.tmux.conf` file and it's secrets. This is the starting point of a slowly evolving configuration, that is improved through out the book.

##Gaining velocity

Scripting customized tmux environments is in my opinion one of the most important chapters, in which Brian shows you, how to build scripts to quickly start your development environment the way you want. He mentions the [tmuxinator](https://github.com/aziz/tmuxinator) project, which is one of the most useful tools, when working with tmux. It lets you configure your windows and panes in a simple to read YAML file. It's no wonder that due to it's roots in the Ruby world, tmuxinator has a configuration skeleton for Rails applications, but this can easily adapted to serve the needs of any project. The introduction to tmuxinator was the breaking point for mer. That was, when I started to comprehend, that I could easily build a prject specific environment, that reduces the friction when opening a project - pulling in changes form the server, start background processes, open your editor, you named it. Tmuxinator is only the starting point for a tmux noob like me to see and comprehend it's power.

The next chapter was one that I would have needed on my first tmux day. It describes how to navigate your buffer, copy and paste and how to communicate with the system clipboard. As with many commands in Vim copy and pasting in tmux uses keys that are rather awkward to use on a German keyboard. [ and ] are just to far out of reach to not disturb you in your normal typing speed.

##Maximum velocity

The chapter on pair programming was one of those, that I looked forward the most, because I saw real power in sharing a session. I was not disappointed. Brain clearly shows the limits in which you can move and presents different techniques to share a session. It is a pity that I had no practical use for it till now, but no question time will come.

##Conclusion

{% img right http://imagery.pragprog.com/products/291/bhtmux_xlargecover.jpg?1330443523 %}The book is rather short with only about 70 pages. Still, it shows you the basic and advanced techniques in tmux, that are rather hard to learn your own. I can truly recommend it, if you are like me struggling to find your way through tmux. Along the road Brian showed some useful tricks (not completely tmux related), that can make your life easier, e.g. remapping the useless <kbd>CAPS LOCK</kbd> key to another key - a thing I should have done a long time ago.

So if you like to use a terminal, have many tabs, various ssh sessions open at the same time, go grab a copy of [tmux - productive mouse free development](http://pragprog.com/book/bhtmux/tmux) and get some order in your chaos.
