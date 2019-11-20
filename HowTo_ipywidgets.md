# How to: ipywidgets

## Installation
```
pip install ipywidgets
jupyter nbextension enable --py widgetsnbextension
# for jupyter lab
jupyter labextension install @jupyter-widgets/jupyterlab-manager  
# make sure the following are updated
jupyter labextension install @pyviz/jupyterlab_pyviz
jupyter labextension install @jupyterlab/toc
```

## Import
```
from ipywidgets import *
```

## Slider
- Declare slider:  
  ```
  slider = FloatSlider( # also IntSlider)
      value=7.5,
      min=5.0,
      max=10.0,
      step=0.01,
      description='Input'
      )
  ```
