---
layout: post
title: An Introduction to Git
tags: [Git, Version Control, Version Control Systems, VC, VCS]
---

## Background

I have been using Git for quite a while but never really understood what it does under the hood. The [GitHub Universe 2015 videos](https://www.youtube.com/user/github/playlists) that were made available on YouTube this February reminded me of that fact, so I spent a couple of hours trying to understand how it does all that magic.

## Git

*Git* is a program first developed by [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds) and the Linux kernel team in 2005, a [Distributed Version Control System](https://en.wikipedia.org/wiki/Distributed_version_control) to handle file history.

With a Version Control System (VCS), you can create snapshots of files at different times and jump back and forth between them. Git achieves this more or less by reading and writing to files in a directory called `.git/`. This directory is created for each project when running `git init` or `git clone`.

You can run Git like any other Shell program.

```bash
git <command>
```

Each version of a file is stored as a [blob (Binary Large Object)](https://en.wikipedia.org/wiki/Binary_large_object) in the local filesystem and each snapshot of a file or files is stored in a what's called a commit. A commit holds references to blobs included in the snaphost (and other information such as the author, date, commit message and a reference to the parent commit(s)). Again, you can see how these files are managed by looking at the contents of the files in `.git/`, they often contain human readable plain text.

This is the initial content of the `.git/` directory after running the init command.

```
.git
├── HEAD                          // Contains the path to the current branch
├── branches
├── config                        // Contains repository configuration, e.g. the remote origin URL
├── description
├── hooks
│   ├── applypatch-msg.sample
│   ├── commit-msg.sample
│   ├── ...
│   └── ...
├── info
│   └── exclude
├── objects                       // Contains all object files such as blobs and commits
│   ├── info
│   └── pack
└── refs                          // Contains the master copy of all refs, e.g. the branches and stashes
    ├── heads
    └── tags
```

If you decide to share the files with other people, you could of course use Dropbox, but, *GitHub* is probably a smarter idea. The [Git project for instance is hosted on GitHub](https://github.com/git/git). Note that Git and GitHub are two completely different things. Git is a software and GitHub is a hosting service.

### Recommended Reads

If you are interested, this book, [Pro Git](https://git-scm.com/book/en/v2) is probably all you need. I did not read every chapter but maybe half of them to feel more confident in working wth Git and dealing with its what used to be horrifying terror.

A more datailed explanation of the contents of the Git project directory can be found [here](http://schacon.github.io/git/gitrepository-layout.html), including the files that aren't initially created. The article also addresses the deprecation of `.git/branches`.

## Slides

I held a small talk introducing the basic concepts of Git last month after reading Pro Git at my working place. It was really about the basics, similar to what I've written previously in this post but covers the following topics.

- Version Control (VC)
- Git
  - Woriking directory / Index / Repository
  - Commits and what they consist of
  - Branches and other pointers to commits
  - Files, blobs and references

<iframe src="//www.slideshare.net/slideshow/embed_code/key/xHcYEFWGIHnpBp" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"></div>

## Other

The motivation behind the development of Git was that the Linux Kernel team couldn't continue to use BitKeeper, another Version Control System (VCS) due to some trouble with the owners (Wikipedia: They revere engineered the BitKeeper protocols). They simply descided to create their own.
