# Installing pytorch with conda


## 1. Update conda version  

```Shell
conda update -n base -c defaults conda
```

## 2. Creating a virtual environment (python 3.8) and activate it 


```Shell
conda create -n NLP-project python=3.8
```

```Shell
conda activate NLP_project
```

## 3. Installing pytorch (check pytorch website for command compatible with cuda for GPU)


```Shell
conda install pytorch torchvision torchaudio cudatoolkit=11.1 -c pytorch -c conda-forge
```

## 4. Creating jupyter notebook kernel for connecting to the environment 

```Shell
conda install -c anaconda ipykernel
```

```Shell
pip install --user ipykernel
```

```Shell
python -m ipykernel install --user --name=NLP-project
```

## 5. Remove environment and kernel

```Shell
conda deactivate
```

```Shell
conda env remove -n NLP-project
```

```Shell
jupyter kernelspec list
```

```Shell
jupyter kernelspec list
```

```Shell
jupyter kernelspec uninstall nlp-project
```

## 6. What eventually worked with cuda version on my laptop


```Shell
(base) C:\Users\jcmeu>conda create -n NLP-project python=3.8
(base) C:\Users\jcmeu>conda activate NLP-project

(NLP-project) C:\Users\jcmeu>conda install pytorch==1.7.1 torchvision==0.8.2 torchaudio==0.7.2 -c pytorch
(NLP-project) C:\Users\jcmeu>conda install -c anaconda ipykernel
(NLP-project) C:\Users\jcmeu>python -m ipykernel install --user --name=NLP-project
```


