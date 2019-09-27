# How to: HTML, CSS, and JS

Definitions:  
- [HTML](#html) is to create a structure to a page - we say what things are   
- [CSS](#css) is for the style  
- [JavaScript](#javascript) is for interaction and adding changes to the page. Changes are due to the data or user interaction  


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

- Include link to `.css` file in `.html` `<head>`:  
  ```
  <head> 
      <link rel="stylesheet" href="style.css">
  </head>
  ```

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
  - Class selector (dot):  
    ```
    HTML
    <p class="withborder">Text</p>
    
    CSS
    .withborder { # note the dot
       color: red;
    }
    ``` 
  - ID selector (ashtag):  
    ```
    HTML
    <h1 id="page-title">Text</h1>
    
    CSS
    #page-title { # note the #
       color: red;
    }
    ```   
    
- Margin vs padding:  
  - *margin* is the distance between an HTML element and the page border  
  - *padding* is the distance between the page border and the text inside the HTML element  

## javascript    
- Variables:  
  ```
  let lastName = "Doe" # in newer js versions (var name = "John" in older js versions)  
  let result = 3+2 
  ```
- Operators:  
  ```
  let result = 3+2  
  let name = firstName + lastName
  let result = 3 >=2 # gives true
  === equal
  !== not equal
  ```
- Functions:    
  ```
  function add(v1,v2){
    return v1+v2
  }
  let result = add(5,3);
  ```  
- Conditional:  
  ```
  let color;
  
  if (v1===10){ 
      color = "blue"
  } else {
      color = "red"
  }
  ```
  can also be  
  ```
  let color = v1 ===10? "blue" : "red" 
  ```
 
**References**  
- *Information Visualization: Programming with D3.js* on Coursera  
 
