# How To: manubot

Instruction: https://github.com/manubot/rootstock and (better) in the README.

- Download the template-repository here: https://github.com/manubot/rootstock  
- Install and activate the environment:  
  ```
  cd [path]/manubot/build`  
  conda env remove --name manubot
  conda env create --file environment.yml
  conda activate manubot # to deactivate: conda deactivate
  ```
- Go back to the parent directory:  
  ```
  cd ..
  ```
- Build the manuscript: 
  - in `.html` and `.pdf`:  
    ```
    sh build.sh
    ```
  - in `.docx`:
    ```
    BUILD_DOCX=true sh build/build.sh
    ```
Created files are in `parentFolder/output`
  
  
## Citations  

```
[@doi:actual_doi_here]
```  
- Change citation style:  

