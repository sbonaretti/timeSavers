# How To: manubot

Instruction: https://github.com/manubot/rootstock and (better) in the README.

- Download the template-repository here: https://github.com/manubot/rootstock  
- Pip install:
  ```
  COMMIT=33e512d21218263423de5f0d127aac4f8635468f # look for commit number here: https://github.com/manubot/manubot under "Installation"
  pip install git+https://github.com/manubot/manubot@$COMMIT
  ```

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
    python build/webpage.py
    ```
  - in `.docx`:
    ```
    BUILD_DOCX=true sh build/build.sh
    python build/webpage.py
    ```
Created files are in `parentFolder/webpage/v/local`

  
## Markdown   
See here: https://github.com/manubot/rootstock/blob/master/USAGE.md

## Citations  
- References:
  ```
  [@doi:actual_doi_here]
  [@url:url_here] # for websites  
  ```  
## Tables: 
- markdown
  ```
  | col1 | col2| col3 | col4 | col5 |
  |------|-----|------|------|------|
  ```
  (To get the html, open file in editor)
  
- Label (under the table):  
  ```
  Table: Use cases.
  {#tbl:use_cases}
  ```
- Reference:  
  ```
  @tbl:use_cases
  ```

## Figures:  
```
![Figure_caption](images/figure_name.png){#fig:figure_label width="100%"} # only png and svg accepted  
```
- Reference:  
  ```
  Figure @fig:figure_label
  ```
 
     



