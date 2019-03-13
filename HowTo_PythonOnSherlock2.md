# How to: Python on Sherlock2
Sherlock2 is the computer cluster at Stanford

### My folders
- Data in: /scratch/users/sbonaret
- Code in: /home/users/sbonaret

## OnDemand  
December 2018: interactive interface on the browser:
https://www.sherlock.stanford.edu/docs/user-guide/ondemand/


## One time configuration
- Create a new directory and go to it:  
    - `mkdir pykneer`
    - `cd pykneer`
- Load python:  
    - `module load python/3.6.1` (To check which python version is available: `module avail`)  
- Create virtual environment and activate it (https://github.com/bnaras/sherlock_cluster/blob/master/VirtualEnvForPython.Rmd)
    - `virtualenv pykneer_env`  
    - `source pykneer_env/bin/activate`  
- Check python version:  
    - `python --version`     
- Install needed modules, for example:  
    - `pip install numpy` (if not in a virtual environment: `pip install --user numpy`)  
    - `pip install matplotlib`  
    - `pip install simpleITK`  
    - `pip install itk`  
- Install Jupyter  
    - `pip install jupyter`  
- Get the code from github
    - `git clone https://github.com/sbonaretti/pykneer.git` (`pykneer` is the name of the repository on github, nothing to do with the local folder names. The project is cloned in the current directory)


## Daily work
- Connect to sherlock and cd to the parent folder (see HowTo_Sherlock2)
- Load python and activate virtual environment from the parent folder
    - `module load python/3.6.1`
    - `source $HOME/pykneer/pykneer_env/bin/activate` (needs the whole path)   
- Cd to the code folder and download updated code from github (if code changed locally):
    - `git pull`  
- Launch jobs with one of these options:
    1. Debug with python
        - `python`   
       	- Ex. copy paste one-by-one the commands in the notebook cells to see if they work  
       	- To exit python: `exit()`
    2. Directly launch notebook and save it as HTML (this is gonna be killed by sherlock)  
        - `jupyter nbconvert --to=html --execute --allow-errors --ExecutePreprocessor.timeout=18000 preprocessing.ipynb`  
        - `jupyter nbconvert --to=html --execute --allow-errors --ExecutePreprocessor.timeout=28800 preprocessing.ipynb`        
           `mv preprocessing.html $(date +"%m_%d_%Y-%H_%M")_preprocessing.html`    
	   (add date and time to file name of saved hmtl file) 
        - `jupyter nbconvert --execute --allow-errors --ExecutePreprocessor.timeout=30000 --to notebook preprocessing_in_house_CQ.ipynb` .  
          `mv preprocessing_in_house_CQ.nbconvert.ipynb $(date +"%m_%d_%Y-%H_%M")_preprocessing_in_house_CQ.ipynb`  
	   (add date and time to file name of saved .ipynb file - saving as .ipynb allows re-edit text cells after running calculations)   
	 Note: timeout is important to avoid that calculations are killed before being completed. 86400 = 24h
    3. Launch job:  
        - `cd /home/users/sbonaret/pykneer/pykneer/code/python/`  
        - `sbatch preprocessing.sbatch`   (example of sbatch file below)
- Check queue:
    -  `squeue -u sbonaret`
- Cancel job (to try):
    - `scancel jobid`
    - `scancel -u sbonaret` (to cancel all jobs)
- Check log of a crashed job:
    - `more slurm-<jobid>`

## Sbatch files
Sbatch files are files to launch jobs  

Example: 
```
#!/bin/bash

#SBATCH --job-name=preprocessing
#SBATCH --nodes=1            ### This is the number of computers: put 1 as python is not parallelized across machines
#SBATCH --ntasks-per-node=10 ### This is the number of cores - use the same as the number of cores used in the notebook
#SBATCH --mem-per-cpu=8GB    ### mem per task (10 tasks x 8GB is a good combination)
#SBATCH --time=24:00:00
#SBATCH --partition=normal
##SBATCH --mail-type=ALL # notifications for job done & fail
##SBATCH --mail-user=serena.bonaretti@stanford.edu

## load python module
module load python/3.6.1
## activate the virtual environment
source $HOME/pykneer/pykneer_env/bin/activate

## launch jobs
jupyter nbconvert --execute --allow-errors --ExecutePreprocessor.timeout=30000 --to notebook preprocessing.ipynb 
  # nb convert is a command to run jupyter notebooks
  # --execute: runs the notebook
  # --allow-errors: does not stop the execution in case of errors
  # --ExecutePreprocessor.timeout: sets the max time for execution (before the machine can pass to the next command)
  # --to notebook: saves as a notebook. This is convenient if one wants to run the results without being done with the text in the text cells. To save as .html directly, use: --to=html
mv preprocessing.ipynb $(date +"%m_%d_%Y-%H_%M")_preprocessing.ipynb
  # change the output name by adding date and time to avoid to overwrite the original notebook and to differenciate notebooks in case of several executions of the same notebook

# see point 2 of "Launch jobs" above for alternatives on command lines
```
