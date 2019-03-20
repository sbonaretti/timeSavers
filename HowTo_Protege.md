# How to: Protege
(https://protege.stanford.edu)

Tool to manually create ontologies and save them in .owl or .turtle

Instructions from the YouTube series: https://www.youtube.com/watch?v=R9ERlUgvgwM&index=1&list=PLea0WJq13cnAfCC0azrCyquCN_tPelJN1

## Create new ontology  
- Launch protege  

### Specify IRI
- In the tab `Active ontology`, in `Ontology IRI`, change ontology name (e.g. leave the name, conclude with `myOntology.owl`)  
### Add classes and subclasses (slow way)  

**Add classes**
- In the tab `Entities`, select the tab `Classes`  
- Click on `Add subclass` button (2 dots and a +) for a new class (`owl:Thing` is going to stay there)  

**Add subclasses** 
- Same as "Add classes", just click on the parent class name before clicking on the `Add subclass` button  `D`

**Make classes disjoint** 
- Go to `Description` (bottom-right panel), click on the `+` next to `Disjoint with` and select the classes   
- Disjointing classes avoids overlap  

### Add classes and subclasses  (fast way)  
- Right click on class name -> `Add subclassES...`  
- Identation creates the hierarchy (see [here](http://protegeproject.github.io/protege/views/class-hierarchy/) under "Add SubClasses Popup Menu Item")  
*Note* Classes are automatically disjointed  
 
