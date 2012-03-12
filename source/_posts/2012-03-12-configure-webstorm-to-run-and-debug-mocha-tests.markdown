---
layout: post
title: "Configure WebStorm to run and debug Mocha tests"
date: 2012-03-12 13:05
comments: true
categories: 
published: false
---
First of all I have to admit that I'm an IDE guy. I'm using command line tools, vi, have gnu tools installed on my windows box and so on. That brings me to the next thing I have to admit: I'm using windows.
I love using [WebStorm](http://www.jetbrains.com/webstorm/) for tinkering with node.js. I love WebStorm for two reasons:

* The javascript syntax completion is somehow crazy clever
* It allows me to stick with my eclipse keyboard schema which is particullary important for me since I'm using eclipse and Visual Studio in my job environment and I don't have enough brain to remember a third keyboard shortcut schema. I guess I'll blog about that in a future post.

When starting with node.js I was using [Nodeunit](https://github.com/caolan/nodeunit) for (unit) testing. While Nodeunit works quite fine it's limited to TDD style tests. Some time ago when coding some [SubSonic](http://subsonicproject.com) I began to like the endorsed test method name syntax in the project that uses the word "should" somewhere in the test method name. That means a unit test that was named "testSquareRootOfZero" would become "squareRootOfZeroShouldThrowAnException" which transports more meaning than "testSquareRootOfZero". As a side effect of this naming schema I was programming (unit) tests slick like chicken shit. For this reason and for pure curiosity I migrated some unit tests to [Mocha](http://visionmedia.github.com/mocha/) that offers a slick BDD style syntax just out of the box.

But I had a slight problem with the Mocha tests in WebStorm: lack of tools support. While this does not really matter for writing the tests nor for running the tests (Mocha has a wonderful console test runner!) but when tests start to fail I want to attach a debugger! And I want to attach my WebStorm debugger with a ton of cool features!

So with a little bit of hand crafting an reading Mocha code It's quite easy to attach the WebStorm debugging tools to Mocha tests.

First install Mocha

    npm install mocha

You may want to install Mocha globally 

    npm -g install mocha 

Next attach the debugger
In WebStorm via Run->Edit Configurations add a new configuration and point the "Path to node App JS File" to \_mocha (can be found under node\_modules in case installed locally or under global modules). Pointing the run configuration to \_mocha is quite important since the main mocha binary spawns a new process you cannot connect via a debugger!

Et voila - Debugging Mocha tests in WebStorm!

Drawbacks: The output is somehow broken, so I'm using the WebStorm runner for debugging while using the mocha console runner for pretty output and continuous tests via watch

