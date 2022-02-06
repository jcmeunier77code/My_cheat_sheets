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







