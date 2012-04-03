---
layout: post
title: "Dependency Management in iOS projects"
date: 2012-03-30 11:16
comments: true
categories:
published: false 
---


Writing an iOS application is not that hard, judging by the current N apps in the iTunes AppStore. Once you have basic understanding of object oriented programming, you look at some iOS tutorials (and Apple has a lot of them), get confused by all these brackets in the objective-c programming language, drag some Controller and Labels together in the interface builder, and after a couple of weeks you get a more or less expedient app (depending on your initial idea).

The hard part is not writing an application, the hard part is writing a big, long-living and maintainable application. (This is actually true for every software product, app, website, etc .. but for the point of this article, we'll focus on Mobile-Apps).

### Architecture of an iOS Project

The maintainability of an application is based on a couple of prerequisites: Separation of Concern, Testibility and Readability .. thus: easy to refactor.
When is start working on a new application, my initial tasks after creating a new XCode project are the following:

1. Deleting all the groups & folders XCode created for me
2. Creating my own folder structure (which is basically very influenced by a RubyOnRails web application) (( screenshot !! ))
3. Identifying and installing the dependent libraries for the application (more on this later).


Step 2 gives me a basic folder structure, in which I'm comfortable working in. Since an iOS Application is basically following the MVC Design pattern, i create folders for my controller, model, view and helper-classes (a web-developer will notice the resemblance to a rails project).

### Using Libraries / Frameworks (core libraries / 3rd party libraries)

Step 3 is more dependent on the type of application: identifying the dependencies. For most of the projects that means libraries to make web-requests, load images into a table-view, parse json or xml data and to save all that stuff into a database. And sometimes we have other types, more UI based libraries, like the typical "drag to refresh" widget in a table-view or some rotating controls, stuff like that.

The hard part here for a long time was to actually manage these dependencies, like libraries, frameworks or own code snippets, and not just copy/drag them into your application, thus making your code base bigger and more difficult to maintain.


### handling dependencies with git submodules

Since most of the 3rd party libraries for iOS programming are hosted on github.com, my initial approach was to use git submodules in my xcode project.

### handline dependencies with cocoapods

#### bundler vs pod

#### cocoapods usage

#### how to write a podspec

### using cocoapods to write your own libraries, re-usable code

#### host podspec on your own git-server

### using cocoapods to write modules / features in a big ios project

#### workflow

#### benefits (clean code, interfaces, private/public methods, etc)

#### caveats

