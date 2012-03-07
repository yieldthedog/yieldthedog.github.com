---
layout: post
title: "Git to SVN migration"
date: 2012-01-19 07:09
published: false
comments: true
categories:
  - git
  - svn
  - migration
---


##Starting point
    ----------IDEAS-----------
    - migrate to what? DVCS for sure, but which?
      -> git, bazar, mercurial => why git
    - Statistics: How many projects, users
    - git knowledge of users
    - OS mix: windows / mac / Linux
    - user mix: command line geeks and gui freaks
    ----------IDEAS-----------

##Git server setup
    ----------IDEAS-----------
    - setups we considered
      * gitosis
      * gitolite
      * gitorious
    - how to configure and adapt gitorious
    ----------IDEAS-----------


##Migration process 
    ----------IDEAS-----------
    - not possible to do all at once, only incremental steps
    - why it's easier to include the history
    - what is possible to automate?
    - branches, tags?
    - different svn layouts (trunk, branches, tags vs multiple projects in one trunk)
    - scripts we used
    - svn:ignore -> gitignore + github/gitignore
      * different setup for .NET, PHP, Ruby, HTML
    ----------IDEAS-----------
    ----------Missing---------
    - downloadable shell scripts
    ----------Missing---------

Because our code base is that large, a migration over the
weekend was not possible. It had to be done in chunks. First
we needed a list of all repos and persons, who where
responsible for the repo. `svn ls --xml` was our friend,
which gave as an easy to transform output of all repos with
last committer names. That was good for a start.

It soon became apparent that we have some clients with lot
of projects and many clients with less than 5 projects. The
latter was no a problem, but the former had no good
structure and naming conventions in the Subversion
repository. We knew for sure that we did not want to migrate
and end up with the same mess as before. So way layed aside
all clients with lots of projects for discussion and
reorganization.

Next we defined, which projects should be migrated with
history and which not. This was a useless discussion,
because it was easier to always migrate with history, as you
will see later.

Our first steps were trying to migrate by hand:

{% codeblock lang:bash %}
git svn clone [svn url] [repo name]        #clone the svn repo to a git repo
git remote add gitorious [gitorious url]   #add a remote to the git server
git push gitorious master                  #push the repo to the server

# done ... hurray ... no wait ....
{% endcodeblock %}


BIG FAIL

What had we missed?

  - no users / usernames
  - no ignores
  - wrong file structure

So lets fix this step by step.

###Users

The users could be mapped rather easily from subversion to git in our case.
Subversion got the users first and last name and Git uses the uses email
address which in our case is the initial of the first name,
a dot, the last name @ our domain. Some times the Subversion
user had only a first name, but these were only rather old records, so they
could be easily ignored. We ended up writing a small Ruby script, that did the work

{% codeblock lang:ruby %}
#!/usr/bin/ruby
name = ARGV[0].split('.')

if(name.length == 1)
  puts name[0] + " <"+ name[0].downcase + "@DOMAIN>"
else
  puts name[0] + " " + name[1] + " <"+ name[0][0].chr.downcase + '.' +name[1].downcase+"@DOMAIN>"
end
{% endcodeblock %}

Now we can call `git svn clone` with this authors.rb file like this:


{% codeblock lang:bash %}
git svn clone --authors-prog=author.rb [subversion url]
{% endcodeblock %}

###Ignores

Next step is to define standard git ignores for projects and
to migrate the existing svn ignores over to git ignores. We
got a lot of help from the [Github gitignore
project](https://github.com/github/gitignore), which we
disected, combined, stripped,… until we had a default
gitignore file. With these two commands we added the
defaults and extracted the subversion ignores into a
gitignore file:

{% codeblock lang:bash %}
# generate gitignore file
cat PATH_TO/default_gitignore.txt > .gitignore
git svn show-ignore >> .gitignore

#add it to the repository
git add .gitignore
git commit -m'added gitignores'
{% endcodeblock %}

###Wrong file structure

The last point was not to be easily resolved. Some SVN
Repositories had a standard layout (trunk, branches, tags),
others just had all code in the root folder without the
standard layout. In most cases we were not interested in
migrating branches and tags, because those were seldom used.
So it came down to having a trunk or not.

If there is a trunk present you can tell git to use this as
the root directory with `--trunk=trunk`.

###Wrapping things up

Now that we had everything in place, we could start the
migration. Communication paths were installed via email and
a shared excel file, which tracked our progress. We created a shell script that automated most of the steps listed above. Still the migration had to be down partly manualy, which was tedious work.

##Migrate your users
    ----------IDEAS-----------
    - gui tools needed
    - small incremental steps
    - playgrounds suck
    ----------IDEAS-----------

Parallel to the repositories migration we had to train our users on how to master the new tool chain. We knew that we had to provide both command line and gui tutorials, as most of our user base was used to TortoiseSVN. We knew that Git was fundamentally different to SVN, but to our users it was just another VCS. The knowledge base of the users was quite different, so we had to be careful to not leave anybody behind and to not bore others on the other hand.

What we came up with were three training sessions:

- @TODO
- @TODO
- @TODO

##Conclusion
    ----------IDEAS-----------
    - same same but different or was it worth the effort?
    - are things better or worse?
    - what is missing now?
    - external collaboration
    - Stats
      7 Jahre
      14 GB Daten
      83 User
      86 Projekte
      405 Repositories
      30103 Commits
      586756 Files
      Viele viele LOCs
    ----------IDEAS-----------

After everything was done, we had a little time to
contemplate and dig for some statistics. We migrated 7 years
of versioned code, 14 GB of data, 83 Users, 86 projects with
a total of 86 repositories.  30103 Commits were moved to
Git, 586756 files, and many many lines of code.

##Was it worth the effort?

Hopefully time will prove us right. Surely we get some good feedback, but especially for non technical people the learning curve is a bit steep:

> - Did you push your changes?
> - Sure. I pressed the commit button.

On the other hand people were using feature branches from day one, the started exploring advanced features by them selfs. Of course they sometimes f***ed up. Who cares? Shit happens everyday and there are less unresolvable problems with Git, than there were with SVN.
