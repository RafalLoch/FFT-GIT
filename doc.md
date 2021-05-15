# 1. What is GIT
# 2. How to work with GIT
## Autohotkey
Download link: 
> https://www.autohotkey.com

Settings:
<br>GitHotkey.ahk
```
; **git-specific

::gs::git status
::glo::git log --oneline
::gd::git diff
::gc::git commit -m
::gcae::git commit --allow-empty
::gck::git checkout
::gr::git rebase -i 
::gb::git branch -a
::gp::git push
::gpo::git push origin
::gst::git stash
::ga::git add -p
::gai::git add -i
::gf::git fetch
::gmnff::git merge --no-ff -e -
::-h::--help
::gk::gitk --all
::githelpme::git reset ORIG_HEAD
::gcrerere:: git config rerere.enabled true
```

## Windows Terminal
