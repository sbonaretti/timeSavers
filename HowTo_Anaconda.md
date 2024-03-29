# How to: Anaconda

## Update to latest version

Documentation [here](https://docs.anaconda.com/anaconda/install/update-version/)
```
conda update anaconda
```

## Update spyder 
If not updated with `conda update anaconda`:
```
conda update spyder
```
or install spyder specifying the version, e.g.:
```
conda install spyder=4.0.1
```
and relaunch Anaconda

## Update JupyterLab
If not updated with `conda update anaconda`:
```
conda install -c conda-forge jupyterlab
```
and relaunch Anaconda

## JupyterLab extensions
- Update:
  ```
  jupyter labextension update --all
  ```
- List:
  ```
  jupyter labextension list
  ```

## Conda cheat sheet
Here: https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf
