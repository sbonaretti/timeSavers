# How to: pythreejs

### Documentation and examples
- Installation not too painful (but I had to reinstall), but very few examples and the python community for this is not vert large  
- Examples:   
  - https://github.com/jupyter-widgets/pythreejs/tree/master/examples  
  - http://pythreejs.readthedocs.io/en/latest/examples/index.html  
- Available classes:  
  - http://pythreejs.readthedocs.io/en/latest/api/index.html  
  
  
### Issues  
- For issues with rendering of points with colormaps, here are the threads I have opened: 
  - https://github.com/jupyter-widgets/pythreejs/issues/194
  - https://discourse.threejs.org/t/point-cloud-in-pythreejs/3238


### Sintax for classes and their functions  
  
```
variableName = className(function1 = x,  
                         function2 = y)
``` 

Example:  
```
ptsMaterial = PointsMaterial(
              color='red', 
              size=1)
```

They can also be nested. Example: 
``` 
pointCloud = Points(
             geometry=geometry, 
             material=PointsMaterial(color='red', size=1),
             )
```

### Point representation

- Points represented as square (defaults of WebGL) and no colormap associated:  
  ```
  from pythreejs import *

  # --points----------------------
  ptsCoord = np.array([[-1.0, -1.0,  0.0],
                       [ 1.0, -1.0,  0.0],
                      [ 1.0,  1.0,  0.0],
                     ], dtype=np.float32)
  pts = BufferAttribute(
        array=ptsCoord,
        )

  size = np.array([[1],[5],[1],], dtype=np.float32)
  sizes = BufferAttribute(
          array=size,
          )


  geometry = BufferGeometry(
             attributes={'position': pts,
                         'size': sizes,
                        })

  material = PointsMaterial(color='red', 
                            size=1)
  pointCloud = Points(
               geometry = geometry, 
               material = material,
               )

  # --rendering----------------------
  c = PerspectiveCamera(
      position=[0, 5, 5], 
      up=[0, 1, 0],
      children=[DirectionalLight(color='white', position=[3, 5, 1], intensity=0.5)])

  scene = Scene(
          children=[pointCloud, c, AmbientLight(color='#777777')])

  renderer = Renderer(camera=c, 
                      scene=scene, 
                      controls=[OrbitControls(controlling=c)])
  display(renderer)
  ```

- Loop of spheres at minute 11 of this video: https://www.youtube.com/watch?v=i40d8-Hu4vM
  ```
  # https://www.youtube.com/watch?v=i40d8-Hu4vM - minute: 11:00
  from pythreejs import *
  from IPython.display import display

  x = [1,5,3] 
  y = [1,5,3]
  z = [1,5,3]
  colors = ['red', 'blue', 'green']
  #colors = [(1,0,0),(0,1,0), (0,0,1)]
  sensors = [Mesh(geometry=SphereGeometry(radius=1),  
                  material=MeshLambertMaterial(color=colors[i]),
                  position=[x[i], y[i], z[i]])
               for i in range(len(x))]

  scene = Scene(children=sensors + [AmbientLight(color='white')])

  c = PerspectiveCamera(position=[0,1,1], up=[0,0,2])

  renderer = Renderer(camera = c,
                      scene = scene,
                      controls=[OrbitControls(controlling=c)])
  display (renderer)
  ```
  
### Lights and cameras  

https://www.youtube.com/watch?v=vB5lSSJRJR0

