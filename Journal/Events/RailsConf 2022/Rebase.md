---
title:
---


Rebase commands

**Re-order**
- You are able to reoder the commits list by moving the rebase messages up and down
- Important if you want to squash related commits but are not beside each-other

**Squash, Fixup**
Squash allows you to reword your commit messages
Fixup discards the second messages

**Edit**
It really means _edit == pick_and_pause
Git will apply the first commits then stop, which will allow you to apply additional commits then rebase --continue

`git reset HEAD^`
Remove the previous commits but keep the changes


**How to recover**
`git rebase --abort` will return to state before starting to rebase
`git reflog` history of steps made


Orphaned rebased do not disappear and can be viewed again using `reflog`



**Book readings**
Pro Git by 
git-scm.com/book