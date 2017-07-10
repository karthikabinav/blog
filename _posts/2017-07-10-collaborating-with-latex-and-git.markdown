---
author: karthikabinav
comments: true
date: 2017-07-10
layout: post
published: false
slug: collaborating-with-latex-and-git
title: Collaborating with Latex and git
categories:
- Research
---


In this post, I will describe a setup I recently settled upon, which makes writing papers when collaborating easy. This setup is especially
useful, when one or more of the collaborators aren't tech-savvy and can't use git. 


In our group, we have been using Dropbox as the default sharing service to keep common latex files. It is convenient and we don't have to exchange
files over emails. We usually face the following two issues:
1. Dropbox does not have a version control and we usually resort to creating folders which looks like *backup-mm-dd*, *old_copy_blah*, etc. Not once have these
backups been useful. In fact, more often than not, it only creates more confusion.
2. Inevitably, we end up using *fancy* Latex packages and one or more of the co-authors complain they are unable to compile it.


Solution to (1) is using git. However, git comes with a *tiny* bit of learning curve which most people get intimidated by. In principle, we just need one of the 
collaborators to be comfortable with using git. Solution to (2) is to use a online latex compiler such as sharelatex, overleaf, etc. In an ideal world, you would want *one* solution
which solves the issue of cloud storage, version control and online compilation of Latex. That ideal world is expensive (i.e., paid versions of sharelatex, overleaf support all three simultaneously).
Now I will describe the work-around we use which is **free**.


We use Dropbox for cloud storage, overleaf for online latex compilation and git for version control. The procedure is described assuming a Mac operating system. The setup is as follows.
1. Create a folder in Dropbox containing the main files. For this example we will call the folder FOCS'36 (see <http://www.scottaaronson.com/blog/?p=253>), with the follwing path
~/Dropbox/FOCS36
2. Let us setup a *local* version of this folder. I am going to name it 


