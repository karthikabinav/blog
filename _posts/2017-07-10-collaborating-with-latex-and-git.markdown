---
author: karthikabinav
comments: true
date: 2017-07-10
layout: post
published: true
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
collaborators to be comfortable with using git (In this post, we are going to assume you are that person).
Solution to (2) is to use an online latex compiler such as sharelatex, overleaf, etc. In an ideal world, you would want *one* solution
which solves the issue of cloud storage, version control and online compilation of Latex. That ideal world is expensive (i.e., paid versions of sharelatex, overleaf support all three simultaneously).
Now I will describe the work-around we use which is **free**.


We use Dropbox for cloud storage, overleaf for online latex compilation and git for version control. The procedure is described assuming a Mac operating system. The setup is as follows.
1. Create a folder in Dropbox containing the main files. For this example we will call the folder MyPaper, with the following path
```
~/Dropbox/MyPaper
```
2. Let us setup a *local* version of this folder. I am going to name the folder "localDropbox" and the corresponding path to be 
```
~/localDropbox
```
3. We will first install this awesome software [Gitobox](https://github.com/remram44/gitobox). If you have [pip](https://pip.pypa.io/en/stable/installing/) installed, you can simply run
```
pip install gitobox
```
Now go into the previously created folder and initialize an empty git repository.
```
cd ~/localDropbox
git init
```
4. Fire up gitobox, which continuously "monitors" changes in your dropbox folder. Run the following command
```
gitobox ~/Dropbox/MyPaper ~/localDropbox/.git
```
5. Finally, "clone" a copy of this to get your local working copy.
```
git clone myWorkingPaper localDropbox
```

The above steps completes the steps for working with dropbox and git. You can make all your local changes in myWorkingPaper, while keeping gitobox running (line 4).
Once you are ready to commit, follow the usual commands
```
git commit -a -m "Your commit message"
git pull origin master
git push origin master
```

This will commit your changes to the localDropbox git folder. The running gitobox will *automatically* take care of syncing this with the dropbox.

The second thing I will now describe is to sync it with an online editor (we predominantly use overleaf since it allows access via git). For this post, let the git url be
<https://www.overleaf.com/abcdefghij>. First go into the myWorkingPaper folder and perform the following command. This command essentially adds overleaf as a remote and *forces* the 
history to be the same as the one maintained locally. This step is needed since overleaf creates a default initial commit.
```
git remote add overleaf https://www.overleaf.com/abcdefghij
git push --force overleaf master
```

A word of caution, *force* push only if the document in overleaf is empty. If there are already some changes in overleaf and you want to merge unrelated histories, there 
are better ways. Since, for this post, we are assuming that the overleaf is new, we won't worry ourselves with it :)

Once the above commands are done, overleaf will now have a working copy that is on your local computer. Now, there are *three* copies of the same file, one on dropbox, one in your local computer
and one in overleaf. Assuming that people made edits on *both* dropbox and overleaf, while you made edits on your local copy, here are the series of git commands to sync them all.
```
cd ~/myWorkingPaper
git commit -a -m "Commit message"
git pull overleaf master #Retrieve from the overleaf copy
git pull origin master #Retrieve from the dropbox copy
#Fix merge issues, if any
git push origin master #push changes to the dropbox copy
git push overleaf master
```

This setup is so organized that it serves everyone. Let me know if you have found better alternatives.

P.S.: You need to keep gitobox running in the background. Everytime you restart a computer, make sure to first start gitobox (Using command in line 4) and then start working!






