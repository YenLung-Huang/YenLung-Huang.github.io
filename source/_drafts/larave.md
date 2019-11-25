---
title: sso-login.md
date: 2019-08-02 21:00:54
tags:
---

### 紀錄上一次訪問的葉面
$fallback = route('users.show', Auth::user());
return redirect()->intended($fallback);
