# Conda

## Basics 

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

## Managing Conda and Anaconda
Verify conda is installed, check version #

`conda info`

Update conda package and environment manager

`conda update conda`

Update the anaconda meta package

`conda update anaconda`

## Check version of conda and of python 

Use the `conda -V` Command to Check Anaconda Version
Use the `conda --version` Command to Check Anaconda Version
Use the `python -V` Command to Check Python Version
Use the `python --version` Command to Check Python Version
Use the `conda list anaconda$` Command to Check Anaconda Version
Use the `conda list` Command to Check Both the Anaconda and Python Version
Use the `conda info` Command to Check Anaconda and Python Version


## Managing Environments

Get a list of all my environments (Active environment shown with *)

`conda info --envs`

`conda info -e`

Create an environment and install program(s)

`conda create --name snowflakes biopython`

`conda create -n snowflakes biopython`

Activate the new environment to use it

`conda activate snowflakes`

Deactivate the environment

`conda deactivate`

Create a new environment, specify Python version

`conda create -n bunnies python=3.4 astroid`

Make exact copy of an environment

`conda create -n flowers --clone snowflakes`

Delete an environment

`conda remove -n flowers --all`

Save current environment to a file

`conda env export > puppies.yml`

Load environment from a file

`conda env create -f puppies.yml`


## Managing Python

Check versions of Python available to install

`conda search --full-name python`

`conda search -f python`

Install different version of Python in new environment

`conda create -n snakes python=3.4`


## Managing .condarc Configuration

Get all keys and values from my .condarc file

`conda config --get`

Get value of the key channels from .condarc file

`conda config --get channels`

Add a new value to channels so conda looks for packages in this location

`conda config --add channels pandas`


## Managing Packages, Including Python

View list of packages and versions installed in active environment

`conda list`

Search for a package to see if it is available to conda install

`conda search beautiful-soup`

Install a new package

NOTE: If you do not include the name of the environment, it will install in the current active environment.

`conda install -n bunnies beautiful-soup`

Update a package in the current environment

`conda update beautiful-soup`

Search for a package in a specific location (the pandas channel on Anaconda.org)

`conda search --override-channels -c pandas bottleneck`

Install a package from a specific channel

`conda install -c pandas bottleneck`

Search for a package to see if it is available from the Anaconda repository

`conda search --override-channels -c defaults beautiful-soup`

Install commercial Continuum packages

`conda install iopro accelerate`

Build a Conda package from a Python Package Index (PyPi) Package

`conda skeleton pypi pyinstrument`

`conda build pyinstrument`


## Removing Packages or Environments

Remove one package from any named environment

`conda remove --name bunnies beautiful-soup`

Remove one package from the active environment

`conda remove beautiful-soup`

Remove multiple packages from any environment

`conda remove --name bunnies beautiful-soup astroid`

Remove an environment

`conda remove --name snakes --all`
