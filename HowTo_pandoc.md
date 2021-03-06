# How to: pandoc


For conversion from markdown (.md) to .pdf

## Good blogs:
- https://learnbyexample.github.io/tutorial/ebook-generation/customizing-pandoc/

## Build the .pdf
`pandoc file_name.md -o file_name.pdf`

## Style 
([manual](https://pandoc.org/MANUAL.pdf), from page 41)

There are two ways of going to a `.pdf`: via `latex` or via `html`. Based on this, one can create styles in different ways:
- Using pandoc `-V options` 
  - While building: `pandoc input.md -V linkcolor:blue -o output.pdf`  
- Using `.css` (via HTML) 
  - Install: https://wkhtmltopdf.org/downloads.html
  - Build: `pandoc -t html --css style.css input.md -o output.pdf`
  - Note: does not recognize latex formulas
- Using latex commands (via LATEX):
  - Create file with style: e.g. `mystylefile.pandoc`
  - Call it when building: `pandoc input.md -H mystylefile.pandoc -o output.pdf`


## Fonts: 
([manual](https://pandoc.org/MANUAL.pdf), page 42)
- Existing fonts:
  - To be specified after to the keyword `fontfamily`
  - Some examples:
    - bookman
    - utopia
    - fouriernc 
    - times
    - mathpazo 
    - libertine
    - arev
    - lmodern
