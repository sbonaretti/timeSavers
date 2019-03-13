# How To: Point visualization on Jupyter Notebook  

### See also the notebook "pointCloudVisualization" in the folder "pythonNotebooks"


To install widgets:  
- `jupyter labextension install @jupyter-widgets/jupyterlab-manager`  

To check which widgets are installed:  
-  `jupyter labextension list`  

To enable/disable widget:  
- `jupyter labextension enable jupyter-matplotlib` / `jupyter labextension disable jupyter-matplotlib`

## VTK  
- Nice visualization  
- The handling is not optimal (mouse movements not very responsive)   
- It is not embedded in the notebook
- See its HowTo for examples 

## pythreejs
- The points are rendered as square and thus the reflections look annoying  
- Cannot find a way to associate a colormap  
- See its HowTo for examples 
- To install widgets for pythreejs:  
  - `pip install nodejs`  
  - `pip install ipywidgets`  
  - `jupyter nbextension enable --py widgetsnbextension`  
  - `jupyter labextension install @jupyter-widgets/jupyterlab-manager` 

## Mayavi
- Installation has to have newest mayavi and pyqt5  
- My installation issues here: https://github.com/enthought/mayavi/issues/659#issuecomment-400821416  
- Examples: http://www.scipy-lectures.org/advanced/3d_plotting/index.html  
- Rendering is too slow and it crashes for all the points of a cartilage
- In `Jupyter notebook`, the standard example works, but it cannot be launched by function called from file. The rendering code has to be written on the notebook 
  ```
  from mayavi import mlab
  mlab.init_notebook()  
  s = mlab.test_plot3d()
  s
  ```
  
- In `Jupyter lab`, this example works but it is not embedded in the notebook:
  ```
  %gui qt
  from mayavi import mlab
  import numpy as np
  x, y, z, value = np.random.random((4, 40))
  mlab.points3d(x, y, z, value)
  ```
  
