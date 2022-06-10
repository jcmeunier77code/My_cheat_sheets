# Git stash

in case you made change change but you don't want to commit them (temporarily, ork in progress)

ex, if you made change on feature branch, want to checkout to master for other purpose but you can't as you haven't commit your change 

```
git stash 
```

put/save changes in temporary place (hiding them), then you can chacout on other branches 

when you're back on the branch 

```
git stash pop
```

