# How to: pandoc


For conversion from markdown (.md) to .pdf

## Build the .pdf
`pandoc file_name.md -o file_name.pdf`

## Style 
([manual](https://pandoc.org/MANUAL.pdf), from page 41)

There are several options:
- YAML file (to understand)
- in command line while calling pandoc:
  - `pandoc input.md -V linkcolor:blue -o output.pdf`  
- Using `.css` 
  - install: https://wkhtmltopdf.org/downloads.html
  - build: `pandoc -t html --css style.css input.md -o output.pdf`
- Using latex commands:
  - Create file with style: e.g. `mystyle.pandoc`
  - call it when building: `pandoc input.md -H mystylefile.pandoc -o output.pdf`


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
