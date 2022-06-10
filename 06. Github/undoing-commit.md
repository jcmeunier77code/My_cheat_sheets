# undoing and changing commit 

## 1. undoing commit 

### reset (for undoing commit locally)
git reset --hard or --soft 

reset hard
hard revert commit and delete/discard the change that where made
```
git reset --hard HEAD~1
```


reset soft or default 
revert commit but keep change in your working directory (just to update)


```
# these two are the same command 
git reset --soft HEAD~1
git reset HEAD~1
```

### git reset (for undoing commit that have been pushed) !!! never on master dev branch

first undo change/commit locally 
```
git reset --hard HEAD~1
```

than force push changes to revert commit in the remote directory 

```
git push --force 
```

> don't do that in master or in dev branch !!!!
> only when working alone in a branch 

ex: 
you reset and forced push it in remote but people already had pull these commit in their local repo 
!!! confusion +++

### git revert (for undoing commit that have been pushed) !!! if needed on master or dev branch 

```
git revert <commit-hash>
git push
```
create a new commit to revert the old commit's changes
so that people are awared of the changes 


> as opposed to git rest <commit-hash> that remove old commit 


## 2. changing commit (for adding changes to existing commit) 

git commit --amend

