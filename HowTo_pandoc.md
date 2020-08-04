# How to: pandoc


For conversion from markdown (.md) to .pdf

## Build the .pdf
`pandoc file_name.md -o file_name.pdf`

## Style 
([manual](https://pandoc.org/MANUAL.pdf), from page 41)

There are several options:
- YAML file
- command line

- https://wkhtmltopdf.org/downloads.html


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
