---
title: tmux in windows
draft: true
date: 2019-10-10 13:30:29
tags:
---

How to run Tmux in GIT Bash on Windows

Tmux running under Git Bash default terminal with two shell processes

I know everyone uses Cmder, but it didn’t work for me. It hung a few times, it has way too many options, it has issues sending signal to kill a process. I gave up on using it. I work with carefully configured default Windows console and believe it or not, it serves the purpose. I also know you can use Windows Subsystem For Linux under Windows 10, which is truly amazing, but I am just talking about the cases where you need standard Git for Windows installation.

When I worked with Unix I liked GNU Screen, which is terminal multiplexer. It gives you a bunch of keyboard shortcuts to create separate shell processes under the same terminal window. The problem is, it is not available under GIT Bash. But it turns out, its alternative — Tmux is.

I did a little research and have found that GIT Bash uses MINGW compilation of GNU tools. It uses only selected ones. You can install the whole distribution of the tools from https://www.msys2.org/ and run a command to install Tmux. And then copy some files to installation folder of Git. This is what you do:

Install before-mentioned msys2 package and run bash shell
Install tmux using the following command: pacman -S tmux
Go to msys2 directory, in my case it is C:\msys64\usr\bin
Copy tmux.exe and msys-event-2-1-4.dll to your Git for Windows directory, mine is C:\Program Files\Git\usr\bin. Please note, that in future, you can see this file with the version number higher than 2-1-4
And you are ready to go. Please note, that I do this on 64-bit installations of Git and MSYS . Now when you run Git Bash enter tmux. My most frequently used commands are:

CTRL+B, (release and then) C — create new shell within existing terminal window
CTRL+B, N — switch between shells
CTRL+B, a digit — switch to the chosen shell by the corresponding number
CTRL+B, " — split current window horizontally into panels (panels are inside windows)
CTRL+B, o — switch between panels in current window
CTRL+B, x — close panel
This is everything you need to know to start using it. Simple. There are many other options which you can explore yourself, for example here http://hyperpolyglot.org/multiplexers.

Update 1: Users in comments are reporting the method not always works. If you have any experiences with this method please feel free to comment, so that we can figure out what are the circumstances under which it works

Update2: I managed to run this on Windows 7, Windows 2012 R2 and Windows 10. My Git installation is set up to use MinTTy console and tmux works only when run from this console, not from default Windows command line console. Still haven’t figured out what are precise requirements for this trick