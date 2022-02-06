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




#### State, release, and feature branches: branches enhance structure & workflow

- different types of branches...
- ...fulfill different types of jobs
