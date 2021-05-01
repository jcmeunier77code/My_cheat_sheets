# Installing packages


## 1. pip freeze   

- pip freeze to get list of all installed packages
- Copy all the names into a text file name it pkg.txt
```Python
pip freeze
pip uninstall -r pkg.txt
```

- Write all modules to a txt file
```Python
pip freeze > requirements.txt
```

## 2. Remove all packages (or install all in your env, e.g. docker) 

- one by one 
```Python
pip uninstall -r requirements.txt
pip install -r requirements.txt 
```


- all at once
```Python
pip uninstall -r requirements.txt -y
pip install -r requirements.txt -y
```


## 3. When jupyter pip unable to uninstall packages (in the command line) 


```Shell
python -m pip uninstall package-name
python -m pip install package-name
```
