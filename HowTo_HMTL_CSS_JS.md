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
- Conditional (if):  
  ```
  let color;
  
  if (v1===10){ 
      color = "blue"
  } else {
      color = "red"
  }
  ```
  can also be:
  ```
  let color = v1 ===10? "blue" : "red" 
  ```  
- Loops:    
  - For: 
    ```
    for (let i=1; i<21; i+=1){
        console.log(i)
    }
    ```  
  - While:  
    ```
    let i=1  
    while (i<21){
        console.log(i) 
        i+=1
    }
    ```  
  - Break:  
    ```
    let i=1  
    while (true){
        console.log(i) 
        i+=1 
        if (i>21)  
            break;
    }
    ```
 - Add the `.js` file at the end of the `.html` file:  
   ```
   ...
   </body>  
   <script src="script.js">
   </script>  
   </html>
   ```  
 - Example 1: Writing in HTML:  
   ```
   <script>  
       let Name = "John";
       let Weight = 196;  
       let Height = 90;
       
       # write to page
       document.write (Name) # document refers to the actual HTML page. This function writes John in the rendered html page   
       # calculate bmi
       const KG_PER_KILO = 0.45
       const INCH_TO_METER = 0.0254  
       let WeightInKg = Weight * KG_PER_KILO
       let HeightInM  = Height * INCH_TO_METER  
       let BMI = WeightInKg/ HeightInM / HeightInM
       document.write (Name + ": " + BMI)
   </script>  
   ```    
- Example 2: Using a function:    
  ```
   <script>  
   
       # use data struct
       let client = { 
       Name:  "John", # let is deleted, = becomes :, and ; becomes ,
       Weight: 196,  
       Height: 90,
       }
       
       # calculate bmi with function
       const KG_PER_KILO = 0.45
       const INCH_TO_METER = 0.0254  
       function getBMI(client){
           let WeightInKg = Weight * KG_PER_KILO    # client.Weight -> client.Weight
           let HeightInM  = Height * INCH_TO_METER  # client.Height -> client.Height
           let BMI = WeightInKg/ HeightInM / HeightInM  
           return BMI
        }
       document.write (client.Name + ": " + getBMI(client))
   </script>  
   ```    
   
   
**References**  
- *Information Visualization: Programming with D3.js* on Coursera  
 
