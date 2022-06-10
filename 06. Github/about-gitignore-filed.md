# .gitignore file

- add .gitignore file to your project (root directory)
- to exclude certain folders or files from git to be tracket

use cases 
- files/folders specific to your editor (.idea in pycharm)
- build folders, where compiled code is located
- datasets, models...

add .gitignore in your IDE and add (asked by editor) and add to it files/folders not to be considered 
then add, commit and push 

if folder push by mistake 

```
# remove recursively from cach
git rm -r --cached .idea
``` 

the add, commit and push 

