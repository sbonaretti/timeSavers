# How to: D3js

[Installation](#Installation)
--- 
D3js provides two different kinds of method:  
- To transform data  
- To draw on webpage  

## Installation  
- Download the file from the website and then include `d3js` in the `.html` in the `script` section:  
  ```
  <script src="d3.js">  
  </script>
  ```
  
## Start server using python   
- On terminal, start a server: 
  ```
  cd to folder  
  python -m http.server 
  ```  
  and get the server number 
- On chrome, type:  
  ```
  localhost:server_number
  ```

## Steps for visualizations:  
- Transform data  (e.g. `d3.cross`, `d3.max`)
- Map data to image space (e.g. dollars to n. of pixels)  (e.g. `d3.scaleLinear`, `d3.scaleTime`)
- Compute the layout  (e.g. `d3.path`, `d3.treemap`)
- Draw the chart (e.g. `d3.select`, `d3.append`)


**References**  
- *Information Visualization: Programming with D3.js* on Coursera  
 
