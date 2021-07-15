# Conda

## List 

### packages 

````shell
conda list 
````

### environments 

````shell
conda env list
````

### packages within environments

````shell
conda list -n myenv
````

### conda remove packages within environments

````shell
conda remove -n myenv scipy
````


### activate env

````shell
conda activate env
````

### enable conda/pip interoperability

by default conda cannot interact with packages install with pip 
impossibility to for conda to remove package install via pip

````shell
conda config --set pip_interop_enabled true
conda remove -n myenv scipy
````
