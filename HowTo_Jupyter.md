# How to: Jupyter

## Installing widgets
```
pip install ipywidgets
jupyter nbextension enable --py widgetsnbextension
jupyter labextension install @jupyter-widgets/jupyterlab-manager  
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
  
## JupyterLab table of content (toc)  
From: https://github.com/jupyterlab/jupyterlab-toc  
- Not working yet - requires JupyterLab 1.0
```
```
  
  
  
## Jupyter notebook extensions (no JupyterLab -> To test)

From: https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/install.html 

**Installation**  
```
pip install jupyter_contrib_nbextensions
jupyter contrib nbextension install --user
```

List of extensions: https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions.html  




