# Basic concept of git

## Initialize a git repository locally 

- Project locally is not a git repository yet 

create a local git repository with 

```
mkdir my_repo
cd my_repo
git init
```

at this stage, no remote repo configured yet 

```
git remote add origin https://github.com/jcmeunier77code/dbr-training.git
```
command to set ut the remote repository 
origin = your remote git project/repo

!!!
now the repo is connected 
BUT branch is not connected yet 
so I cannot push it directly 

```
$git push                                  
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin master
```

use instead the propose command 

```
git push --set-upstream origin master
```

## 2. Concept of branch 

### Master branch = main branch
- is created by default, when initializing a git repo
- how to know the state of the repo if every code put all things on the same branch

>> best pactice is to created new branch for each feature and for each bugfix

- developpers with branches can commit without worrying to break main branch
- merge complete branch
- new feature can be deployed 

>> big feature branches long open, increase the chance of **merge conflicts**

- with branches you achieve a stable main (master) branch --> which is deployed

>> branch is based on master
>> branch starts from same codebase

### Two ways to create a branch 
- in the UI

to know locally that a new branch has been created 
```git
git pull
```
at this stage the new branch is not yet set locally, one way to do so:
```git 
git checkout <new-branch>
```

- from the cli
more convenient and easier 
always checkout on master when creating a new branch as the new branch should on the code base of the master branch
```shell
git branch my-new branch 
# creating a new branch
#or
git checkout -b my-new-branch
# creating new and switching to it 
```

but the remote repo doesn't know about the new local branch, so:
```
git push 
# works if remote branch already exists, otherwise and this is the case here 
git push --set-upstream origin feature/database-locally
# and this will created the new branch on the remote repo
```

### two type of branches: master and develop branches  

1. dev branch

intermediary master
during sprint: features and bugfixes into dev 
end of sprint: merge into master 

2. master branch 

ready for production 

### master branch only vs. master + dev branches 

1. master only

- for continous integration/delivery
- pipeline is triggered whenever feature/bugfix code is merge into master

```mermaid
flowchart LR
A[test] --> B[build] --> C[deploy]
```
- you want to deploy evry single feature/bugfix rightaway

> best practice for devops as it is aligned with the CD/CI 

2. master + dev branches

- features/bugfixes are collected in dev branch
- !! dev branch often bewomes "work in progress" branch











    






