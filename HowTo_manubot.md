# How To: manubot

Instruction: https://github.com/manubot/rootstock

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
  conda activate manubot          # to deactivate: conda deactivate
  ```
- Go back to the parent directory:  
  ```
  cd ..
  ```
  
- Build the manuscript: 
  - make sure the virtual environment is acrive: `conda activate manubot `
  - in `.html` and `.pdf`:  
    ```
    sh build/build.sh             # Created files are in `output` and figures are not rendered in `.html`
    python build/webpage.py       # Created files are in `parentFolder/webpage/v/local` and figures are rendered
    ```
  - in `.docx`:
    ```
    BUILD_DOCX=true sh build/build.sh
    python build/webpage.py
    ```

  
## Markdown   
See here: https://github.com/manubot/rootstock/blob/master/USAGE.md

## Citations  
- References:
  ```
  [@doi:actual_doi_here]
  [@url:url_here] # for websites  
  ```  
- For recurrent citations:  
  - In `content/citation-tags.tsv` add a label (tag) and a citation (doi):  
    ```
    tag	citation
    deep-review	doi:10.1098/rsif.2017.0387
    ref_weber	doi:10.1109/eScience.2018.00027
    ```  
    Make sure that there is a tab between tag and citation. If not, copy/paste the space from the template `deep-review	doi:10.1098/rsif.2017.0387`
  - In the text, cite as:  
    ```
    @tag:ref_weber
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
- Change font size (see [GitHub issue](https://github.com/manubot/rootstock/issues/239)):    
  - Go to the `.css` file: `build/themes/default.html` (saved as `.html` but it is a `.css`)  
  - For `html` rendering, go around line 216 and add:    
    ```
    table {
        border-collapse: collapse;
        border-spacing: 0;
        width: 100%;
        margin-left: auto;
        margin-right: auto;  
        font-size: 12px;   /* ADDED - set size in terms of pixels (character height) */ 
        font-size: 10pt;   /* ADDED -set size in terms of points */
        font-size: 0.75em; /* ADDED -set size relative to main document font-size */
    }
    ```
  - For `.pdf` add the same lines around line 533   
    ```
    figure, table {
            font-size: 0.85em;
            font-size: 12px;   /* ADDED - set size in terms of pixels (character height) */ 
            font-size: 10pt;   /* ADDED -set size in terms of points */
            font-size: 0.75em; /* ADDED -set size relative to main document font-size */
        }
    ```

- Customizing tables:  
  - Write the table in HTML (if already written in markdown, open the HTML in editor, and copy/paste to markdown file)   
  
 

table td {
    word-wrap: break-word;         /* All browsers since IE 5.5+ */
    overflow-wrap: break-word;     /* Renamed property in CSS3 draft spec */
}


## Figures:  
```
![Figure_caption](images/figure_name.png){#fig:figure_label width="100%"} # only png and svg accepted  
```
- Reference:  
  ```
  Figure @fig:figure_label
  ```
 
     



