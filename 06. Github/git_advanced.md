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

o to logs to check change 

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

1. Long-running branches 

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



2. Short-lived branches

- for new features, bug fixes, refactoring, experiments...
- will be deleted after integration (merge/rebase)
- typically based on a long running branch
    - after having done some commits to debug or fix problems, reintegrating back into main (after having safely merged or rebased, your feature branch can be deleted)

![branch4](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/branch4.png)

### Two example branching strategies

1. Github flow

- very simple, very lean: only one long-running branch ("main") + feature branches
- 

![branch5](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/branch5.png)

2. Gitflow

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

    'cd path_where_to_put_the_cloned_repository
    git clone https://github.com/my_github/repository_name.git'


    - Go inside the repository
    
    'cd repository_name'

3. (optional) Creating a PullRequest if you want your changes to be reviewed be the code owner

    - Create a new branch (branch where you'll make the changes) 
    
        git branch new_branch_name
    
    - Go to this branch
    
        git checkout new_branch_name
    
    - After you've made the changes you want to submit
    
        git status
        git add (* for all or only file_changed)
        git commit -m "the changes I've made"
    
    - Push the changes in your remote repository (your GitHub page)
    
        git push --set-upstream origin new_branch_name
    
    - On your GitHub forked repository, the changes have been made and GitHub detect automatically that this is a forked repository and ask if we want to send a pull request to the code owner

![pr7](https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/.img/pr7.png)

    
## Merge conflict


    
    
    
