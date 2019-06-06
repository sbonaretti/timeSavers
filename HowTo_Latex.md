# How To: Latex

## During writing and editing
### Compute the number of words
In the *command line*: 
```
texcount completeFileName
```
texcount is one of texmaker's packages

### Highlight text  
```
\usepackage{color,soul}
...
\hl{Text to be highlighted}
```


## Change lateral margin  
```
% in the header
\usepackage{geometry}
\geometry{margin=1in}
```

## Change font 
Font catalogue: http://www.tug.dk/FontCatalogue/  
e.g. urwpalladio (Font: http://www.tug.dk/FontCatalogue/urwpalladio/):
```
\usepackage[sc]{mathpazo}
\linespread{1.05}         % Palladio needs more leading (space between lines)
\usepackage[T1]{fontenc}
```

## Figures

### Figure creation
Easy way using pptx:  
- Create figure in pptx  
- Print current page as .pdf
- To crop the figure (e.g. white margins) in Mac: 
  - Open the figure in Preview  
  - Tools -> Rectangular selection --> select the area  
  - Tools -> Crop

### Figure inclusion
```
% in the header
\usepackage{graphicx} % to include figure
\usepackage{float}    % to locate figure in text

% in the document
\begin{figure}[H]     % H = position Here in text
    \includegraphics[width=\linewidth]{figure_name.pdf}
    \caption{figure_caption}
    \label{fig:figure_label}
\end{figure}
```

### Figure reference in text
```
(Fig. \ref{fig:figure_label})
```


## Links  
- Showing link
  ```
  \url{https://doi.org/10.1016/j.media.2014.05.008}
  ```
- Not showing link  
  ```
  \href{https://www.eosc-hub.eu/}{The European Open Science Cloud}
  ```

- Icons
  ```
  % in the header
  \usepackage{fontawesome}

  % in the document
  \faGithub
  \faCode
  ```

## Tables
```
\begin{table}[h]
  \begin{tabular}{lccc} % left, centered, centered, centered # put as many as the number of columns
    \hline % create horizontal line
    row1col1  & row1col2  & row1col3  & row1col4 \\
  \end{tabular}
  \caption{table_caption}
  \label{table:table_label}
\end{table}
```

### Table reference in text
```
(Table \ref{table:table_label})

```
### Table tricks  
- Ident in cell:  
  ```
  \hspace{3mm} text
  ```
- Break text in cell:  
  ```
  % in the header 
  \usepackage{makecell}	
  
  % in the document
  \makecell{first part \\ second part}
  ```
- Merge table cells:  
  ```
  % in the header
  \usepackage{multirow}	
  
  % in the document
  \multicolumn{n}{|c|}{text} % n = number of cells to merge, |c| = left and right border and center text  
  ```  
- Fixed width table columns with text raggedright/centered/raggedleft  
  ```
  % in header
  \usepackage{array}
  \newcolumntype{L}[1]{>{\raggedright\let\newline\\\arraybackslash\hspace{0pt}}m{#1}}
  \newcolumntype{C}[1]{>{\centering\let\newline\\\arraybackslash\hspace{0pt}}m{#1}}
  \newcolumntype{R}[1]{>{\raggedleft\let\newline\\\arraybackslash\hspace{0pt}}m{#1}}
  
  % in text
  \begin{tabular}{| c | L{3cm} | C{3cm} | R{3cm} |}
  ...
  \end{tabular}
  ```
  
## References  

### Export bibliograpy from Mendeley  
- Tag the paper: For each paper, in the `Tags` field, type the paper's tag (e.g. pykneer)  
- Export biblio:   
  - In the `search` type the tag  
  - Select all the paper  
  - File -> Export(Make sure not to leave spaces in the file name)  
  
### Insert bibliography in latex file  
```
% in the header
\bibliographystyle{plain} % or any other style

% in the text
\cite{paper_keyword}

% under "References"
\bibliography{file_name.bib}

```
In texmaker, alternatively run `BibTex` once and `Quick Build` twice


