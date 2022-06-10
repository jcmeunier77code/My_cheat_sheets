# Branch concept 


## 1. Merging branches 

context: commits have been done on features branches and on master.  Before feature to be pushed, want to merge/import changes frome master 

on feature 
```
git add .
git commit -m "my changes on feature"
```

on master 
```
git add .
git commit -m "my changes on master"
```

<img width="641" alt="image" src="https://user-images.githubusercontent.com/97024809/173018969-fa87bfb9-be83-4bd3-a4dd-d4da624f8a9f.png">


<img width="421" alt="image" src="https://user-images.githubusercontent.com/97024809/173019047-baa6f834-8ef1-4d55-9148-13f0731a6a8b.png">

on feature 
```
git merge master 
```

<img width="423" alt="image" src="https://user-images.githubusercontent.com/97024809/173019131-952de297-d9c1-4aa8-934d-fd7d38a39159.png">

then push feature to remote feature
```
git push
```

Then on remote (UI), you can send a PR for merging feature with remote master  

<img width="479" alt="image" src="https://user-images.githubusercontent.com/97024809/173020306-eabab4c2-d872-4d07-ae5c-19124bde43d9.png">



## Pruning branches

in you want to deleted the deleted remote branches that still appear locally 

```
git fetch --prune origin
```

or configure git to do it systematically 

```
git config --global fetch.prune true
```
