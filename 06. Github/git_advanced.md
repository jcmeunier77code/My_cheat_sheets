# Git & github

## perfect commit 

- add the right change 
- find the right message 

### perfect commit message 
1. subject = cooncise summary of what happened 
2. Body = more detailed explanation 
    - what is now different than before ?
    - what is the reason for the change ?
    - Is there anythhing to watch out for/anything particularly remarkable ?

If difficult to stay concise, it is maybe an hint that you put to many thing in the commit

### Steps

To add change 

    git add

To add change at a patch level (chunk)

    git add -p

To commit 

    git commit 

In the vim 

    press i to insert 

    write git message 
    - decription 
    - enter (so git know you pass to the details)
    - give details 
    - press :wq to save and escape 

Go to logs to check change 

    git log 

    press q to escape log

## Branching strategies

### A written convention 

Agree on a branching workflow in your team

1. Git allows you to creeate branches - but it doesn't tell you how to use them!
2. You need a written best practice of how work is ideally structured in your team - to avoid mistakes & collisions.
3. It highly depends on your team/team size, on your projects, and how you handle releases.
4. It helps to onboard new team members ("this is how we work here").

### Integrating changes & structuring releases

1. Mainline development ("always be integrating")
2. State, release, and features branches

#### Mainline development "always be integrating"

- fews branches
- relatively small commits
- high quality  testing & QA standards

![branch1](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/branch1.png)


#### State, release, and feature branches: branches enhance structure & workflow

- different types of branches...
- ...fulfill different types of jobs

![branch2](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/branch2.png)

### Two main types of branches 

#### 1. Long-running branches 

- exists through the complete lifetime of the project
- often, they mirror "stages" in your dev life cycle
- common convention: no direct commits!
    - commits are never directmy added to these branches: commits should only make it to the long term branches through integration (i.e. through merging and rebasing) 
    - reasons:
        -   quality: don't add untested code to your environment  
        -   release bundling and scheduling: release new code in batches  
    - if commits each time small changes to main/long running branches, keeping an eye on what's released become difficult  

Typically:
- main or master branch
- but also develop/staging/productipn branches: represent states/stages in the development process

![branch3](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/branch3.png)



#### 2. Short-lived branches

- for new features, bug fixes, refactoring, experiments...
- will be deleted after integration (merge/rebase)
- typically based on a long running branch
    - after having done some commits to debug or fix problems, reintegrating back into main (after having safely merged or rebased, your feature branch can be deleted)

![branch4](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/branch4.png)

### Two example branching strategies

#### 1. Github flow

- very simple, very lean: only one long-running branch ("main") + feature branches
 

![branch5](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/branch5.png)

#### 2. Gitflow

- more structure, more rules
- long-running: "main" + "develop"
- short-lived: features, releases, hotfixes

![branch6](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/branch6.png)


### The "best" branching model ? 

- consider your project, release cycle, and team
- take inspiration from existing models (like "GitFlow" or "GitHub Flow")
- ...and create your own model!


## Pull requests

### Communicating about and reviewing code

Without pull request

![pr1](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/pr1.png)

With pull request

![pr2](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/pr2.png)

![pr3](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/pr3.png)

> Pull request are always based on branches and not on individual commits !

> - creating a new branch where we request changes to be reviewed


### Contributing code to other repositories

Think about popular public repositories: 
- you might have nice ideas... 
- ...but you're not allowed to push code and/or to make changes

![pr4](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/pr4.png)

For that purpose, creating a fork which is a personnal copy of a repository

![pr5](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/pr5.png)

![pr6](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/pr6.png)


### How to proceed to fork a repository,make changes appropriately and send pull requests

1. On GitHub

    - fork the repository to make a copy on your own GitHub
    - get the code (button on the up right corner) of your GitHube copy of the repository

2. In command line interface

    - Clone the repository locally

    ```shell
    cd path_where_to_put_the_cloned_repository
    git clone https://github.com/my_github/repository_name.git
    ```

    - Go inside the repository
    
    ```shell
    cd repository_name
    ```
    
3. (optional) Creating a PullRequest if you want your changes to be reviewed be the code owner

    - Create a new branch (branch where you'll make the changes) 
    
    ```shell
    git branch new_branch_name
    ```
    
    - Go to this branch
    
    ```shell
    git checkout new_branch_name
    ```
    
    - After you've made the changes you want to submit
    
    ```shell
    git status
    git add (* for all or only file_changed)
    git commit -m "the changes I've made"
    ```
    
    - Push the changes in your remote repository (your GitHub page)
    
    ```shell
    git push --set-upstream origin new_branch_name
    ```
    
    - On your GitHub forked repository, the changes have been made and GitHub detect automatically that this is a forked repository and ask if we want to send a pull request to the code owner

![pr7](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/pr7.png)

    
## Merge conflicts

1. When they might occur 
2. What they actually are 
3. How to solve them


### How and when conflicts occur

When integrating commits from different sources

![mc1](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mc1.png)

> All these commands perform some kind of integration and this is where merge conflicts can happened


### Merging changes in Git 

A flawless process, most of the time!

![mc2](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mc2.png)

But when **contradictory** changes happen

![mc3](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mc3.png)

> This situation requires a decision from a human

Other situations where it can happened:
- when a file was modified in one branch and deleted in another
- ...


### How do you know when a conflict has occured ?

Don't worry: Git will tell you :-)

![mc4](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mc4.png)


### How to undo a conflict and start over ?

You can always undo and start fresh!

```shell
git merge --abort
```

or 

```shell 
git rebase --abort
```

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mc6.png" width="500"></p>


### What conflicts *actually* look like

Just characters in a file!

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mc7.png" width="600"></p>

### How to solve the conflict 

Simply **clean up** the file with, for example, a mergetool which allows you to select the changes to keep/to suppress

[see pycharm mergetool](https://www.jetbrains.com/help/pycharm/resolving-conflicts.html)

Or, in command line interface

```shell
git mergetool
```

![mc8](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mc8.png)

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mc9.png" width="600"></p>


## Merge vs. Rebase

### How a merge works

#### A simplified scenario

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mr1.png"></p>

A fast forward merge

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mr2.png"></p>

#### A more realistic scenario

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mr3.png"></p>

A merge commit: 
- When two or multiple branches move forward differently, git has to make a commit on the merge 
- this commit contains the difference between them
- normally commit is created by the user, but this not the case for merge commit: 
    - automatically created by Git
    - do not content content documentation/descritpion of the changes; need to go to the branches' commit history to see what was changed 

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mr4.png"></p>

### How do a rebase work

#### A straight line of commits

Not better or worse than merge, just different
If you don't want to go with the automatic merge commit and want the project history looks like a straight line

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mr5.png"></p>


#### Rebase - step by step

1. The starting situation

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mr6.png"></p>

2. Starting the rebase 

```shell
git rebase branch-B
```

Step 1

First git remove all commits on branch-A that happen after the split (saved somewhere temporarily)

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mr7.png" width="1000"></p>

Step 2

Then Git makes a new commit that applies to branch-B

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mr8.png"></p>

> At this stage,  temporarily, both branches look the same

Step 3

The parked/saved commit is re-integrated (rebased) on top of the commits integrated in branch-B 

<p align="left"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/mr9.png"></p>

> Results is that the commits history looks like a straight (there is no merge history)

#### Warning notice

One thing to understand with rebase:
- it rewrites commits history
- Commit c3 has an *: has the same content as c3 but is effectively different because it has now a different parent c4 (whereas c1 before the rebase)
- it creates a completely different commit history
    - not a problem for commit that have not been published or pushed yet 
    - but if you do so on commit that already have been published/pushed to a remote repository, you might get in trouble (because other developpers might have based their work on the commit c3 (which is no longer here, the new one is c3*)

> do **not** use rebase on commits that you've already pushed/shared on a remote repository !

> instead, use it for cleaning up your local commit history before merging into a shared team branch
