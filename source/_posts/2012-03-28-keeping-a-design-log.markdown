---
layout: post
title: "Keeping a Design Log"
date: 2012-03-28 10:35
comments: true
categories: design
published: true
---

Ever wondered why it's hard for you to argue design decisions? Ever said "We should not go for that, we had some problems in past projects, but I have no clue what project or problem that was" in a meeting. Ever made the same design failure twice? I do, or more precise I did but I quit!

Some time ago I was really annoyed of not being able to argue a design decision, and I've no clue what decision that was, with real arguments but with the words "We just should not do that!". So I started by design/architecture log in which I'm recording as a retrospective design decisions with their consequences and context.
<!-- more -->
{% img full-width https://lh4.googleusercontent.com/-lc6XtAHSKlU/T3NwN7D5CaI/AAAAAAAAAMU/PxMov3JKC-Y/s1069/IMG_9885.jpg %}

I'm using [Evernote](http://evernote.com) for keeping my design log because I'm using Evernote for more or less anything I (think I) need to remember, good search support and it's mobile apps. So I have my design log searchable and always with me.

I'm using the following pattern to record my design decision evaluations

> ### Name
> Name the design decision! That is the tricky part. I'm doing that at last. The name is important for me because I'm referring to the name in discussions with team members and in discussions with myself.
>
> ### Context
> Outline of the context, what forces are involved, what requirements need to be satisfied including non functional requirements.
>
> ### Example
> A short example, that helps me best to understand the "design decision".
>
> ### Consequences
> What were the consequences of the design decision? Pros and Cons, reflects the requirements and is in context of the forces that led to that decisions.
> What actions need to be taken to avoid/force this pattern?

I'm keeping track of good and bad decisions here. Consequences for me

* Frees my mind
* Makes me argue
* Forces reflection on design decisions, even the ones not recognized as decisions
* I can use wise ass terms like "Limit your Abstractions" in meetings

What it's not

* It's not my personal design patterns catalog, this is more high level

And here it is, one example pattern found in my _Design Log_, "**The early pragmatic**"

> ### Early pragmatic
> When starting a project early decisions I take are too pragmatic. This leads to missing abstractions early in the process. Which leads to an eroding architecture and design, which makes the whole project an inconsistent pile of non decisions.
>
> ### Example
> Workflow/State Machine implementation in Project XXX (I left that out for reasons...)
>
> ### Consequences
>
> * Figure out a catalog of limited abstractions early. Decide which to use.
> * Reflect on missing abstractions or infrastructure!
> * Make it a ritual to check the code for missing abstractions, leaky abstractions or duplications! Use an (automated) duplicate code finder!
> * Don't over architecture, a clear defined list of abstractions will do it.

