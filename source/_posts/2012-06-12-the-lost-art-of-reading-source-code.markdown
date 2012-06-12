---
layout: post
title: "the lost art of reading source code"
date: 2012-06-12 22:32
comments: true
categories: programming open-source
published: true
---

In my _old programming days_ reading source code of libraries that I used was often a hard task. Either the code was closed source or only in binary format.

Today we live in an area in which programmers like to share their code and have the tools to do so. We could not be more lucky. To solve a certain task we can choose from __many different solutions__ that may vary in __quality__ and __functionality__. If one does not fit the purpose we just use the next one.
<!-- more -->
##When unsolvable problems arise
Most open source solutions have a __solid documentation__, otherwise they could not compete with the __high standard__. Still from times to times I am confronted with problems that are not covered in the documentation and can not be solved with the help of Google. Sometimes a colleague asks me a question, sometimes I find a question on StackOverflow with a problem that the person was not able to solve.

When such a problem arises I like to open the library and __dig in the source code__. I have [found](http://stackoverflow.com/questions/8112646/raphael-js-2-0-animate-translation-with-variable-inconsistency-noob/8112744#8112744) [many](http://stackoverflow.com/questions/7506538/scrollto-with-easing-and-a-callback-function/7506799#7506799) [solutions](http://stackoverflow.com/questions/8022926/jquery-validate-plugin-test-value-for-email-pattern/8023132#8023132) by reading and debugging the code of a library (even of libraries I did not use or know until then). _It's fantastic_. You find yourself in a different, uncomfortable zone and can learn so much by just looking. You can uncover hidden gems or APIs inside your library that where not supposed to be directly visible for the public, or you can find details that are missing in the documentation. In the latter case it should be a good coder's duty to help and update the documentation. And you can learn how others try to solve problems which may give you __new perspectives__.

But, you can also get __terrified__ by what you are looking at. It happens rather rarely to me. Once in a while I trip over code that is a mess, is horrible to read or debug, or was just written by an unskilled person. Do not get me wrong here. I have deep respect for everyone who is open sourcing a project, but I do not want to use code that is below my standards. I appreciate these moments, because they help me to form an environment in which I can develop at a steady pace. I do not want to get stuck because of library code.

##What you need to start
Nothing, you do not need anything but __curiosity__. That's the fun part. Most stable open source projects have a fantastic code base that is easy to understand and read. In my opinion this has a rather simple reason: If they do not care for code quality, they soon suffer a painful death in the vicious circle of unmanageable code.

You do not need to understand the whole thing at once but most projects have modules or other encapsulated logic that makes it easy to understand a part of the whole.

So what are you waiting for? Head over to the Github and [check](https://github.com/sinatra/sinatra) [out](https://github.com/jquery/jquery) [some](https://github.com/ASP-NET-MVC/ASP.NET-Mvc-3) [of](https://github.com/git/git) [those](https://github.com/DmitryBaranovskiy/raphael) [great](https://github.com/antirez/redis) [projects](https://github.com/nginx/nginx). And the next time you are stuck within a library or framework crack it open and look under the hood.

Want to recommend a good code read? Just leave a comment!
