# How to: D3js

[Installation](#Installation)  
[Start server](#Start-server)  
[Steps for visualizations](#Steps-for-visualizations)  
[Loading data](#Loading-data)

--- 

## Installation  
- Download the file from the website and then include `d3js` in the `.html` in the `script` section:  
  ```
  <script src="d3.js">  
  </script>
  ```  
  
## Start server  
A server is needed to upload data and files when using d3js. Put data and index.html in the same folder.  
- Using python:   
  - On terminal, start a server: 
    ```
    cd to folder  
    python -m http.server 
    ```  
    and get the server address 
  - On chrome, type:  
    ```
    localhost:server_address
    ```  
    and I can see `index.html` rendered (if `index.html` not there, I see the folder content)  
- Atom: 

## Steps for visualizations  
- Transform data  (e.g. `d3.cross`, `d3.max`)
- Map data to image space (e.g. dollars to n. of pixels)  (e.g. `d3.scaleLinear`, `d3.scaleTime`)
- Compute the layout  (e.g. `d3.path`, `d3.treemap`)
- Draw the chart (e.g. `d3.select`, `d3.append`)

## Loading data  
- Data are in `.json` or `.csv` 
- Loading requires a server
- The process is asynchronous. If we want to do something with the data, we need to provide a callback:  
   ```
   d3.csv(dataUrl) #for json: d3.json(dataUrl)
     .then(callback) # once the data is ready, we can run the method (not before)
     .catch(errorHandler) # to check if there are loading errors
   ```  
 - Example:  
   ```
   <body>
       <div id="container"></div> # data will be given to container 
   </body>
   
   <script src"d3.js"></script> # import d3js 
   
   <script>
       let container = d3.select("#container") # connects to the html container  
       
       d3.csv("file_name.csv")
         .then(function (data)){ #using anonimous function, i.e. without name + providing data to the function
             for (let client of data){ # for loop thought data
                 write (client.Name)
             }
         }) 
         
         function write(text) { # this function is written below the line where it is called
             container.append("div").text(text) # provide text to the container; no need to pass container as a variable
         }
   </script> 
   
   ```

---

**References**  
- *Information Visualization: Programming with D3.js* on Coursera  
 
