---
title: vim 安裝
date: 2019-08-03 16:18:53
tags:
---

## windows 10

透過choco 安裝 gvim 要使用插件的時候，需要透過

```
# 檢查 python2
:echo has('python2')

# 檢查 python3
:echo has('python2')
```

檢查是否安裝

```
Here is an approach that I used to get VIM 7.x to work with Python 3.x.

Install a VIM of your preference. Suggestion: get the latest version from VIM.org, though this site seems to have only 32-bit versions. If you want 64-bit (my preference) get a pre-built at https://bintray.com/veegee/generic/vim_x64 or choose your own pre-built elsewhere, or build your own.

Type the command :py3 print("hello")

It probably will not find the python dll, in which case it gives an error message like cannot load pythonXX.dll where XX is a two-digit number. In my case, VIM was looking for python35.dll, which comes from Python 3.5.1 (and probably any Python 3.5.x). The number will vary depending on the version of VIM you use.

Go find a matching Python distribution. Matching means that both VIM and Python must be either 32-bit or 64-bit, and the DLL that VIM wants (in step 3) is present. So for example, it appears that Python 3.5.x provides python35.dll. Install it.

I don't recall having to do anything special to get VIM to find the python DLL, other than ensuring that the directory it is in should be in the path, and I think it already was. If not, add the directory with the DLL to your path.

Retry step 2. It should work now.

If in the future you upgrade VIM or Python, you may need to upgrade the other one at the same time, to ensure that the test in step 2 still works.

```
