# How to: D3js

[Installation](#Installation)  
[Start server](#Start_server)  
[Steps for visualizations](#Steps_for_visualizations)


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


---

**References**  
- *Information Visualization: Programming with D3.js* on Coursera  
 
