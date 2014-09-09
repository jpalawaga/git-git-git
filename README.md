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

    I'm James Palawaga, ________ at ________, and we're gonna spend the next 40 minutes hacking on git. Before I start, I'd like to say that I could have serialized all of this into a fancy 500-page-powerpoint that made it looks like I was executing commands, but lets be honest, it's more thrilling for me to try and pull live-demoing something off, and more exciting for you to watch me crash and burn. If you have any questions, please stop me at any time. There will also be a Q&A at the end, which may be a better time to pose any deep philosophical questions.

    ---

    So, who has seen this [image of the various coverletters]. The odds are probable that you've done something like this before. It's nothing to be ashamed of. Well, not yet anyhow. But, with the advent of dropbox, Google Documents, in-editor version control... it's probably less likely.

    Instead... how about one of these? [pause]

    These are more likely candidates, may actually being clutter if you end up sharing this out to other people, or commiting it so some other sort of source control system. Realistically, commented code should really be hiding around in your production-quality code base, and the older versions of the file in source control should give you enough history to eliminate the need for .bak files.

    ---

    Alright, so what is git?

    Git is a Distributed Version Control System.
    A Version Control System is some sort of scheme for managing changes to files, along with also managing "checkpoints" (or snapshots) of your file/codebase.
    A distributed version control system is one where everyone has as complete copy of the codebase, with all versions, and information swap with between any two points. A centralized repository can exist, but doesn't necessary. [Maybe an image of the repositiory web].

?    In this image, you can see the bi-directional flow of code between any two parties.

    You should probably care what git is because:
        - It's fast. Compared to other version control systems, git is among the fastest. You can make an entire separate branch of your code in 40 bytes.
        - It's ubiqutous. Github has started a social coding renassaince that isn't slowing down. "trendy," if that's your thing
        - It's gonna make your life easier. It is a separate way of thinking, but once you master the basics, it's a super-sharp chef's knife.

    Getting started with git is easy. 'git init'. Now you know.

   ---

   I'm going to go ahead and cover all of the basic git commands, and also some git philosophy. I implore you to try and not think of this in terms of another source-control system, because odds are you'll just end up making your life more difficult.

    I'll warn you all now that the general pattern of this is introduce concept, explain it in high-level terms, then explain how it actually works. That said, it's not important that you understand the technical parts, its just there for the geeks in the room. Alright, so, lets get on with it.

    
