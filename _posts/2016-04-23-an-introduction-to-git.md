---
layout: post
title: An Introduction to Git
tags: [Git, Version Control, Version Control Systems, VC, VCS]
---

## Background

I have been using Git for quite a while but never really understood what it does under the hood. The [GitHub Universe 2015 videos](https://www.youtube.com/user/github/playlists) that were made available on YouTube this February reminded me of that fact, so I spent a couple of hours trying to understand how it does all that magic.

### Git

*Git* is a program first developed by [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds) and the Linux kernel team in 2005, a Version Control System (VCS) used to handle file history.

You can run it like this

```bash
git <command>
```

With Git, you can create snapshots of files at different times and jump back and forth between them. If you then decide to share the files with other people, you could either use Dropbox or hos it on *GitHub*. The [Git project for instance is hosted on GitHub](https://github.com/git/git). Note that Git and GitHub are completely different things. Git is a software and GitHub is a hosting service.

### Git

This book, [Pro Git](https://git-scm.com/book/en/v2) was more than enough for me. I did not read every chapter but maybe half of them to feel more confident in working wth Git and dealing with its what used to be horrifying terror.

## Survey

I held a small talk introducing the basic concepts of Git last month.

- Version Control (VC)
- Git
  - Woriking directory / Index / Repository
  - Commits and what they consist of
  - Branches, and other pointers to commits
  - Files, blobs and references

The most fundamental concepts of Git such as the commits and how these snapshots are stored and what they consist of. What I don't discuss are commands such as `reset` and `rebase`.

<iframe src="//www.slideshare.net/slideshow/embed_code/key/xHcYEFWGIHnpBp" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"></div>
