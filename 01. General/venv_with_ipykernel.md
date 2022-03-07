# Working with virtual environment in jupyter notebook 

## Setting up virtual environment

Checking which version of python
```
python3 -V
```

Installing and setting up virtualenv (in bsh/zsh) 
```
sudo pip3 install virtualenv
```

creating virtual env 
```
python3 -m virtualenv env_name
# or
python3 -m venv env_name
```

activate 
```
source env_name/bin/activate
```

update pip
```
python3 -m pip install --upgrade pip
```

Install ipykernel
```
python3 -m pip install ipykernel
```

Setup new kernel
```
python3 -m ipykernel install --user  --name=long-tail-kernel
```

Install jupyter notebook
```
pip install jupyter notebook
```

## Managing kernels

List all existing kernell
```
jupyter kernelspec list
```

remove unwanted kernel 
```
jupyter kernelspec uninstall unwanted-env
```
