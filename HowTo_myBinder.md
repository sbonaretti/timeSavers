# How to: mybinder

## ENVIRONMENT FILE

In the github repository create the environment file. If using: 
- python: create `requirements.txt`. Example:
  ```
  numpy==1.15.1
  pandas==0.23.4
  ```
- R: create `runtime.txt` containing the version of R used. To see the version, in terminal `R --version`. This command calls a version of R in MCRAN (which contains an image of all R versions). Example:
  ```
  r-2017-03-06
  ```
  Create also `install.R`, containing all the packages to install. Example: 
  ```
  install.packages("ggplot2")
  install.packages("ggrepel")
  ```
- python and R: create one file called `enviroment.yml` for conda installation. Example: 
  ```
  name: pykneer
  channels:
    - conda-forge
  dependencies:
    - python=3.7.1
    - numpy=1.15.1
    - pandas=0.23.4
    - scipy=1.1.0
    - simplegeneric # for rpy2
    - watermark # for dependences
    # R packages
    - rpy2
    - r-base=3.4.1
    - r-ggplot2
    - r-ggrepel
    - r-maps
    - r-ggmap
  ```
Add this file to the repository (master branch, no subfolders)

Copy the URL and the badges before launching (or after launching, just go back to the previous page)

## CREATING THE ENVIRONMENT
Go to [mybinder.com](https://mybinder.org/) and fill out like this: 
- Github repository name or URL: put the master repository. Example: 
  ```
  https://github.com/sbonaretti/pyKNEEr (GitHub on the right)
  ```
- Git branch, tag, or commit: ```master```  
- Path to a notebook file (optional): Put the relative (to the directory) path to the file. Example:  
  ```
  publication/data/cart_segm_literature.ipynb (File on the right)
  ```
- Press launch. It creates a docker file, containing a linux machine, where it install python and R with the libraries required in the environment file -> It takes time (~15-20 minutes). The following times it takes less because the docker image is already created

## ADDING A NEW NOTEBOOK
- Go to the mybinder page where you created the previous mybinder, and just substitute the name of the notebook file
  
  


