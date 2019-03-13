# How to: rst


Titles
- h1 level title (= title of the page)  
  ```==============```
- h2 level title (= it goes in side bar):   
  ```--------------``` 
- lower level title:  
  ```+++++++++++++++++```
- =, for sections   
- -, for subsections  
- ^, for subsubsections  
- ", for paragraphs  
  
Font size
- superscript:   
  ```:sup:`subscript text` ```  
- subscript:   
  ```:sub:`subscript text` ```   
  If not space in between letters (e.g. T2):  
  ```T\ :sub:`2`\  ``` (leave two spaces after second back-slash) 
  
Font appearance:  
- bold:  
  ```**bold**```  
- italics:  
  ```*italics*``` 
- underlined: it does not exist in .rst. Use HTML (include all paragraph in the command):   
  ```
  .. raw:: html
     # skip a line
     beginning of sentence <u>underlinedText</u> end of sentence
  ```   

White space between paragraphs:      
  ```
  |
  ```

Lists
- bulleted list: 
  ```
  * item x (or -; leave a space before the list)
  * item y
    * with z under y
  ``` 
- numbered list: 
  ``` 
  1. item 1
  2. item 2
  ```

Links
- link to external webpages opened in the same tab:  
  ``` 
  `text <https://www.anaconda.com/download/>`_ 
  ```
- link to external webpages opened in a different tab: It does not exist in .rst. Use HTML:    
  ```
  .. raw:: html
     # skip a line
     beginning of sentence <a href="address" target="_blank">text</a>  end of sentence
  ``` 
- to internal parts of the website:  
  - in the destination of the link:  
    ```
    .. _label:
       # skip a line
       Text 
    ```
  - in the origin of the link:  
    ```
    :ref:`Click here <label>`
    ```
  Note: in the destination `_label` has underscore; in the origin `label` has no underscore     
    
   
Code  
- bash:  
  ``` 
  .. code-block:: bash 
  ```  
- inline code:  
  ```
  `` code `` 
  ```
  
Figure
  ```
  .. figure:: _figures/figureName.png
            :align: center
            :scale: 30%
  ```

Note
- ``` 
  .. note::

  ```

Labelled paragraph  
- Indent two spaces  
  ```
  This is a non-indented paragraph  
    This is an indented (and labelled) paragraph  
  ```
