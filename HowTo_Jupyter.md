# How to: Jupyter

## Table of content / internal links  
In table of content: 
```
[loading data](#loading)
```
- To add space character at the beginning of item
  ```
  &nbsp; # repeat the command for more spaces
  ```  
In text:
```
<a name="loading"></a>
```


## Auto reload  
```
# Make sure there are no empty spaces at the end of the lines 
%load_ext autoreload
%autoreload 2
```

## Create kernel
To create a [new kernel](https://anbasile.github.io/programming/2017/06/25/jupyter-venv/):    
``` 
pip install ipykernel  
ipython kernel install --user --name=projectname  
```  
Select the new kernel from the notebook (top-right)

## Uninstall kernel
To [delete a kernel](https://stackoverflow.com/questions/42635310/remove-kernel-on-jupyter-notebook)    
```
jupyter kernelspec list  # to get the paths of all your kernels  
jupyter kernelspec uninstall unwanted-kernel-name # to uninstall your unwanted-kernel-name  
```

## Installing widgets

See: https://github.com/sbonaretti/timeSavers/blob/master/HowTo_ipywidgets.md

```
pip install ipywidgets
jupyter nbextension enable --py widgetsnbextension
# for jupyter lab
jupyter labextension install @jupyter-widgets/jupyterlab-manager  
# make sure the following are updated
jupyter labextension install @pyviz/jupyterlab_pyviz
jupyter labextension install @jupyterlab/toc
```
Restart JupyterLab if it the visualization does not occur


#### itkwidget
```
pip install itkwidgets
jupyter labextension install @jupyter-widgets/jupyterlab-manager itk-jupyter-widgets
```

## Mixing python and R 

#### Prerequisites (on Mac)
- Install last python  
- Install last R 3.3.3   
  (Note on Dec 11, 2018: the older versions of R are compiled with gcc instead of clang, so `pip install rpy2` does not work. To install rpy2 with R > 3.3.3, one has to install the gcc compiler with `conda install llvm gcc libgcc1`. However this downgrades python to 2.7, which means that commands like `autoreload` in Jupyter do not work anymore)
- In terminal:
  - Install rpy2
    ```
    pip install rpy2
    ```
    (it might uninstall some packages - just reinstall them)
- Get R path:  
    ```
    R HOME #to get R home (e.g. /Library/Frameworks/R.framework/Resources)
    ```
  
#### In notebook
```
import os
os.environ['R_HOME'] = '/Library/Frameworks/R.framework/Resources'
%load_ext rpy2.ipython

# example:
# python's pandas dataframe
import pandas as pd
df = pd.DataFrame({
    "cups_of_coffee": [0,1,2,3,4,5,6,7,8,9],
    "productivity": [2,5,6,8,9,8,0,1,0,-1]
})
# R's ggplot2
%%R -i df -w 5 -h 5 --units in -r 200
# import df from global environment
# make default figure size 5 by 5 inches with 200 dpi resolution

# install.packages("ggplot2", repos='http://cran.us.r-project.org', quiet=TRUE) (#uncomment the first time)
library(ggplot2)
ggplot(df, aes(x=cups_of_coffee, y=productivity)) + geom_line()
```
 
#### Markdown  
- Change font color:  
  ```
  <font color='blue'>
  ```
