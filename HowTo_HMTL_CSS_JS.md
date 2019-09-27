# How to: HTML, CSS, and JS

Definitions:  
- [HTML](#html) is to create a structure to a page - we say what things are   
- [CSS](#css) is for the style  
- JavaScript is for interaction and adding changes to the page  


## HTML   
- Core code:   

  ```
  <!DOCTYPE html>
  <html>
  
  <head>
     <title>Page title</title>
  </head>
  
  <body>
      <h1>First heading</h1>
      <p>First paragraph</p1>
  </body>
  
  </html>
  ```

## CSS  

- Different kinds of HTML selectors are called in different ways in CSS:  
  - Tag selector:   
    ```
    HTML
    <p>Text</p>
    
    CSS
    p {
       color: red;
    }
    ```  
  - Class selector:  
    ```
    HTML
    <p class="withborder">Text</p>
    
    CSS
    .withborder { # note the dot
       color: red;
    }
    ``` 
  - ID selector:  
    ```
    HTML
    <h1 id="page-title">Text</h1>
    
    CSS
    #page-title { # note the #
       color: red;
    }
    ``` 


**References**  
- *Information Visualization: Programming with D3.js* on Coursera  
 
