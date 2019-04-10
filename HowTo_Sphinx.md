# How to: Sphinx

Sphinx is the package to create websites in pyton.   

Steps done in `terminal`.

## Install Sphinx
It should be already installed with Anaconda. If not:  
`
pip install Sphinx    
`

## Set up the site  
- Go to the project folder:   
  `cd <projectFolder>`  
- Launch sphinx:  
  `sphinx-quickstart`  
- Fill out the requirements. Useful entries:  
    - `Select root path: .` Enter (already `cd`ed to the folder) 
    - `Separate source and build directories (y/n) [n]:` `y`
    - `imgmath: include math, rendered as PNG or SVG images (y/n) [n]:` `y`  
    - `mathjax: include math, rendered in the browser by MathJax (y/n) [n]:` `y`  
    - `githubpages: create .nojekyll file to publish the document on GitHub pages (y/n) [n]:` `y`  
    - `Create Makefile? (y/n) [y]:` `y` 

## Language: Markdown (.md files)
If site pages are written in markdown, install markdown parser.  
Documentation here: http://www.sphinx-doc.org/en/master/usage/markdown.html  
- `pip install recommonmark`  
- Open `source/conf.py`and:
    - Uncomment line 51 and comment line 52 (search if they are not there). It has to look like this:  
      ```
      source_suffix = ['.rst', '.md']  
      #source_suffix = '.rst'
      ```
    - Add these lines anywhere (below the previous lines is fine):  
      ```
      source_parsers = {
          '.md': 'recommonmark.parser.CommonMarkParser',
      } 
      ```
## Language: ReStructuredTest (.rst files)  
Basic documentation here: http://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html  
Documentation of python addictions here: http://www.sphinx-doc.org/en/stable/markup/index.html  
Basics: http://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html#paragraphs  
It has more functions than markdown (e.g. good for template "guzzle").  

## Make the site  
- `make html`
- to open it, double click on `build/html/index.html`

## Change theme  
 - List of themes:  
   - http://www.sphinx-doc.org/en/master/theming.html   
   - https://sphinx-themes.org/  
 - If theme chosen in https://sphinx-themes.org/, click on `pypi`:  
   - Installation: as indicated  
   - Use: as indicated  
   - `make html`   
   - refresh page    
 - Change theme in `conf.py` in `html_theme = ` . 
 - To see where the theme is installed: `pip show theme_name` (e.g. `pip show guzzle_sphinx_theme`)
   
(The theme for pyKNEEr is guzzle: https://pypi.org/project/guzzle_sphinx_theme/  
 The theme for my personal website is sphinx-bootstrap: https://pypi.org/project/sphinx-bootstrap-theme/)
## Edit home page  
- The home page is `source\index.rst`

## Add pages  
- Add a new `.md` file to the folder `source`  
- Add the file to `index.rst`, under `toctree` (`toc` = table of content). Example: Adding the page "introduction":  
  ```
  .. toctree::
     :maxdepth: 2
     :hidden:

     introduction
   ``` 
- `make html`  
- refresh page

## Sidebar  
- Some changes for sidebar are allowed in `conf.py`. Example:   
  ```
  html_sidebars = {   
    '**':       [   
                  'logo-text.html',   
                ]   
  ```              
- Options for changes in `conf.py` here: http://www.sphinx-doc.org/en/master/usage/configuration.html#confval-html_sidebars  
- To customize changes, for example in `global toc`:   
  - Create the file `globaltoc.html` and put it in the folder `_templates`. It overwrites the original one. (Easier to copy the original one (use search to find it) into `_templates`)   
  - Modify `_templates\globaltoc.html`  

## Change css 
- Create `custom.css` in `source/_static/css` (if folder `css` does not exist, create it)  
- In `conf.py` add:  
  ``` 
  def setup(app):   
    app.add_stylesheet('css/custom.css')   
  ```  
- Add the changes (they will overwrite the original css).  
- Trick 1: Changes in css do not always update quickly. Write some text somewhere -> `make html` -> refresh the html page. Also the style will be updated   
- Trick 2: To know the name of the classes to change, look at the content of the html file and find the class name there (in Chrome: right-click on the .html file -> `View page source`; or open with an editor - e.g. Atom )



## Useful link on how to set up the site:  
1. https://www.youtube.com/watch?v=uPTSTQRoluw

## Images and figures  

Example for image usage:  
.. image:: picture.jpg  
   :width: 200px  
   :height: 100px  
   :scale: 50 %  
   :alt: alternate text  
   :align: right  

Example for figure usage:  
.. figure:: picture.png  
   :scale: 50 %  
   :alt: map to buried treasure  

   This is the caption of the figure (a simple paragraph).  

## Add site to GitHub

- Personal webpage  
  - Create the repository `yourUserName.github.io` (it has to be this name)  
  - Commit all the content of the `build` folder directly into the repository  
  - Make sure that the repository contains the file `.nojekyll`.   
    `.nojekyll` tells GitHub not to use Jekyll (its default) to build the website. `.nojekyll` is created when running the command `sphinx-quickstart` to make the website (command: `githubpages: create .nojekyll file to publish the document on GitHub pages (y/n) [n]:` `y`). `.nojekyll` can also be created manually with a text editor as an empty file with that name  - (To see/hide the hidden files in mac: https://ianlunn.co.uk/articles/quickly-showhide-hidden-files-mac-os-x-mavericks/) 
  - Go to `settings` -> `GitHub Pages` -> `Source` -> `Master branch` -> `Save`
  - The link to the website appears above `Source`. It takes a few minutes to have the website up 
  
- Project webpage  
  - In the repository of your project create a folder called `docs` (it has to be this name)  
  - Commit all the content of the `build` folder directly into the folder `docs`  
  - Make sure that the repository contains the file `.nojekyll`.   
    `.nojekyll` tells GitHub not to use Jekyll (its default) to build the website. `.nojekyll` is created when running the command `sphinx-quickstart` to make the website (command: `githubpages: create .nojekyll file to publish the document on GitHub pages (y/n) [n]:` `y`). `.nojekyll` can also be created manually with a text editor as an empty file with that name  
  - Go to `settings` -> `GitHub Pages` -> `Source` -> `Master branch/docs folder` -> `Save`
  - The link to the website appears above `Source`. It takes a few minutes to have the website up  
  - Note: double-check if `.nojekyll` is needed also in the main folder of the repository
  
## Adding Google Analytics (GA) tracking number to website  

### 1. Getting the tracking number from GA
(to be added)  

### 2. Adding tracking number to website 
If the website template already includes support for GA tracking number, enter it as indicated in the template instructions (usually in `confy.py`).  

If the website templete does not include support for GA tracking number (from: https://www.ericholscher.com/blog/2009/apr/5/adding-google-analytics-sphinx-docs/):   
- In the `source` folder, create a fodler `_templates` 
- In `_templates`, create the file `layout.html` and copy/paste these lines:  
  ```
  {% extends "!layout.html" %}
  {% block footer %}
  {{ super() }}
  <script type="text/javascript">
  var gaJsHost = (("https:" == document.location.protocol) ? "https://ssl." : "http://www.");
  document.write(unescape("%3Cscript src='" + gaJsHost + "google-analytics.com/ga.js'   type='text/javascript'%3E%3C/script%3E"));
  </script>
  <script type="text/javascript">
  try {
  var pageTracker = _gat._getTracker("GAtrackingNumberHere");
  pageTracker._trackPageview();
  } catch(err) {}</script>
  {% endblock %}
  ```
  Substitute `GAtrackingNumberHere` with your actual number (do not delete the quotes)  
- Run `make html`

### 3. Checking tracking number was added  
Open your `index.html` file in a text editor (e.g. Atom) and search for your GA code, or open `index.html` in Chrome, and then right-click -> `View page source`, and search for your GA code   

  
  
