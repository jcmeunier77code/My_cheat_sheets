# Git for devops

## Use cases 

### Infrastructure as a Code

- many kubernetes configuration files for deployment on kubernetes
- yaml, 
- kubernetees cluster are deployed on aws
- for maintenance, terraform and ansible configuration files 
- on top of that also some bash and python script

All these files should be: 
- tracked - history of changes 
- securely stored in one place
- shareable for the devops teams

So you will use github repository for that 

> git in conjonction with terraform for IaaC

### CI/CD pipeline and build automation
- checkout code, test and build application, ets. 
- need integration for the build automation tool with application git repository
- you need to setup integration with build automation tool and git repository

and there is also specific git command for buildong pipeline 
- getting commit hash of specific commit 
- check if changes happen in frontend or backend code 

> git in conjunction with jenkins for CI/CD pipeline 







