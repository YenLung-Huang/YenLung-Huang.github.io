---
title: find-slow-plugins-in-vim
tags:
---

:profile start profile.log
:profile func *
:profile file *
" At this point do slow actions
:profile pause
:noautocmd qall!

