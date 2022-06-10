# Branch concept 

in you want to deleted the deleted remote branches that still appear locally 

```
git fetch --prune origin
```

or configure git to do it systematically 

```
git config --global fetch.prune true
```
