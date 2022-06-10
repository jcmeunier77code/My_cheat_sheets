# Merge and rebase concept

## 1. Merge requests

>> Best practices: other developper reviews code changes before merging 
>> as master must be stable and ready for production 

use case: big feature, junior developer or expertise in different area
great chanc to learn and grow from each other
sme vlidation before merging : pull request 


## 2. rebase 

If changes are made by two persons on the same branch, 

git push returns error, then you first need to pull 

```
# either 
git pull
# but you'll have an additional commit for merging the two branch : a bit dirty
# or (and it is cleaner)
git pull -r
# rebase meaning that it will first fetch the commit from remote and then add your commit 
```

## 3. merge conflict

if you edit the same line on the same document and on the same branch

```
CONFLICT (content): Merge conflict in my_text.txt
```

then you have to decide manually which change to take

got the your IDE (pycharm: git menu --> merge conflict)

<img width="495" alt="image" src="https://user-images.githubusercontent.com/97024809/172984996-6e9d0f40-b50e-44df-8716-ae78e00dc504.png">

when conflict resolve

```
git rebase --continue
```

<img width="734" alt="git rebase --continue" src="https://user-images.githubusercontent.com/97024809/172985636-a3031728-9e7e-40b8-9866-cc1a71b08ef4.png">

```
#then 
git push 
# so that resovle conflict push on remote
```




