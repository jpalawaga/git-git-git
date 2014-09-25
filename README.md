Git-git-git
===========

Excuse the dumb name. This is the space that I'm going to be using to organize my git-talk.

Format
======

This talk will be presented in the course of 40-some minutes and will go a bit, but not too far, in depth.

### Introduction [8 minutes]
    - A story about a version control-less world
    - What is git?
    - Why would I want to use git?
    - What I'm going to tell you.
        - How we're going to break this up (beginner/expert)

### Body (so affectionately named) [20 minutes]
Each of these will broken down into:
    - a new command
    - graph theory view of what it is?
    - what does it do
    - why do I want to use it

### Close out [2 minutes]
    - What I just finished telling you
    - Q&A / Why this is important

### Q&A [10 minutes?]
    - Given an example in git __if easily setup__

Ideas
=====
    - Show what the graph theory looks like (how? Separate image? Whiteboard? 'cat'?)
    - should cover HEAD, also ^ and ~ and .. notation
    - Commands to consider
        - status
        - add
        - commit
            - cover commit hash, ranges, sane messagesj
        - log
        - diff
        - branch
        - push
        - pull
        - fetch
        - checkout
        - stash
        - cherry-pick
        - reset
        - rebase
        - remote / fork <- separate sections
        - reflog
    - should I cover working / stage / repo?

Inspiration
===========
    - http://zachholman.com/talk/more-git-and-github-secrets/
    - https://github.com/schacon/git-presentations/blob/master/basic_git_talk/BasicGitTalk.pdf


Introduction
    - A story about a version control-less world
    - What is git?
    - Why would I want to use git?
    - What I'm going to tell you.
        - How we're going to break this up (beginner/expert)

    Welcome.

    I'm James Palawaga, ________ at ________, and we're gonna spend the next 40 minutes hacking on git. Before I start, I'd like to say that I could have 
serialized all of this into a fancy 500-page-powerpoint that made it looks like
I was executing commands, but lets be honest, it's more thrilling for me to try
and pull live-demoing something off, and more exciting for you to watch me crash
and burn. If you have any questions, please stop me at any time. There will also
be a Q&A at the end, which may be a better time to pose any deep philosophical
questions.

    ---

    So, who has seen this [image of the various coverletters]. The odds are 
probable that you've done something like this before. It's nothing to be 
ashamed of. Well, not yet anyhow. But, with the advent of dropbox, Google 
Documents, in-editor version control... it's probably less likely.

    Instead... how about one of these? [pause]

    These are more likely candidates, may actually being clutter if you end up sharing this out to other people, or commiting it so some other sort of source control system. Realistically, commented code should really be hiding around in your production-quality code base, and the older versions of the file in source control should give you enough history to eliminate the need for .bak files.

    ---

    Alright, so what is git?

    Git is a Distributed Version Control System.
    A Version Control System is some sort of scheme for managing changes to 
files, along with also managing "checkpoints" (or snapshots) of your 
file/codebase.

    A distributed version control system is one where everyone has as complete
copy of the codebase, with all versions, and information swap with between any
two points. A centralized repository can exist, but doesn't necessary. [Maybe
an image of the repositiory web].

?    In this image, you can see the bi-directional flow of code between any two
parties.

    You should probably care what git is because:
        - It's ubiqutous. Github has started a social coding renassaince that 
          isn't slowing down. "trendy," if that's your thing

        - It's gonna make your life easier. It is a separate way of thinking,
          but once you master the basics, it's a super-sharp chef's knife.

        - It's fast. Compared to other version control systems, git is among the
          fastest. You can make an entire separate branch of your code in 40 
          bytes.

    Getting started with git is easy. 'git init'. Now you know.

   ---

   I'm going to go ahead and cover all of the basic git commands, and also some
git philosophy. I implore you to try and not think of this in terms of another 
source-control system, because odds are you'll just end up making your life more
difficult.

    I'll warn you all now that the general pattern of this is introduce concept,
explain it in high-level terms, then explain how it actually works. That said, 
it's not important that you understand the technical parts, its just there for 
the geeks in the room. Alright, so, lets get on with it.

   ---

   Alright.
   Let's start.
   I'm going to start by introducing six commands. These ones are all pretty
elementary, so it shouldn't be blowing any minds. The commands we'll cover are:
init, clone, status, add, commit, and log.

   SO. I've told you already that git init is the way to get started with git.
This will create some hidden folders and initialize an empty repository inside 
of your folder. The other way to get started is by cloning an existing repo,
and this can be done using git clone.

I'm going to go ahead and initialize a new repository right now.

<git init>

... and in this folder, I'm going to create a new file.

<vi recipes.txt>

And now, we're going to add this file to git. Before we add it though, we're 
going to take a look at the status of our repository. There is a git command
called (convieniently) status. It will show you the current "status" of each of
the files that live in your current directory, that do not match rules inside of
your .gitignore file.

<git status>

You can see that git recognizes that I have added a new file inside of the
directory tree that git controls, although you can also see that git is not
currently tracking it. Let's go ahead and track that file now.

<git add recipes.txt>
<git status>

Cool. You can now see that the file is now staged for add.

A digression on terminology:
    - Files that you've changed, but haven't told git to worry about (add/rm)
      are in the working area. Git knows not a lot about these files. These
      show up as red.
    - Files you've added or removed are in the "staging area". When you write a
      change to the repository, the file statuses in the staging area are
      written ("committed") the history. These show up as green. Git remembers
      these files in the current status. Changes you make after adding it will
      not be recorded to the commit. So if we make a change to our recipes file,
      
      < make change >
      < git status >
      
      You can see that git will make a distinction between what the working copy
      is, and what the staged copy is. Again, only the staged copy will get
      written to the history.

     
Now, you may have been super clever and noticed that I mentioned a "git ignore"
this file lists all of the file extension or directory patterns that we do not
want git to track. You may have noticed that <git status> didn't just show
my recipes.txt file, but also a swap file that was automatically created by my
editor. We don't want to track these files, so we'll go ahead and get git to 
ignore these.

<git status>

We can see that git now ignores these files. Note, .gitignore itself is version 
controlled. Additionally, we have our updated copy of our recipes. This seems
like a good place to save our progress.

Instead of writing out all of the filenames for git add, we can tell git to add
all of the working-copy changes to the staging area simply with git .. The .,
fyi, is shorthand for "everything in this directory," and yes, that includes
subdirectories and their contents.

< git . >
< git status >

Alright. Lets make some magic. To write these files to the repository, we need
to commit to the changes. We do

< git commit >

And when we do so, git prompts us to write a message. Generally, the first line
should not excede 50 characters in length, and be concise about what the changes
are. You write much more on the lines below, but really try to keep our messages
50 chars or under. If you need more, chances are you probably should've commited
something earlier. This means that

"Today, I've started the beginning of what I hope to be the world's greatest
recipe compendium" is way too long. How about "Adding recipes text and git
ignore". Yep. that'll do. short, concise. We don't need to even include any
extra information, but we can if we want to.

<write/quit>

And that's it! If we check out status, we can see that our staging area is now
empty. 

< git status >

Now, for the final part of our introduction to git, we'll see our commit in the
log.

< git log >

There it is! Magical. Commits are recorded with your name, the date, and your
message. A bunch of information is combined to generate a hash that is specific
to this commit. These hashes are cool, and we'll look at them later. They're
supposed to uniquely identify any given set of changes, regardless of time,
content or author.

