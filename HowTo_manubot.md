# How To: manubot

Instruction: https://github.com/manubot/rootstock

- Download the template-repository here: https://github.com/manubot/rootstock  
- Install and activate the environment:  
  ```
  cd [path]/manubot/build`  
  conda env remove --name manubot
  conda env create --file environment.yml
  conda activate manubot # to deactivate: conda deactivate
  ```
- Build the manuscript:  
  ```
  sh build.sh
  ```
