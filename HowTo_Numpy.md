# How To: Numpy

### Create a vector 

- Known lenght and values:  
  ```
  a = np.array([value1,value2,...,valueN])
  ex.: a = np.array([1,2,3])
       a
         array([1, 2, 3])
  ```

- Known lenght and same value:  
  ```
  a = np.full((r,c), value)
  ex.: a = np.full((3,1),0)
       a 
         array([[0],
                [0],
                [0]])
  ```
- Array of unknown length and elements where 1 element is added at the time (ex. in a for loop):   
  Use a python list for the for loop and convert to numpy after the loop 
  ```
  # allocate the list
  x_list = []
  
  # for loop
  for i in range(0,len(array))
      x_list.append(value)
      
  # convert to numpy array
  x_np = np.array(x_list)
  ```
  
- Array of unknown length and elements where several elements are added at the time (ex. in a for loop):   
  Can be used also when only 1 element is added
  ```
  # create one array with size [1,1] and assign value 1
  array = np.full((1,1),1)
  array = np.extract(x==x, x)
  
  # for loop
  for i in range(0,len(array))
      array = np.hstack((array,arrayToAdd))
      
  # delete the first element
  array = np.delete(array,0,0)
  ```
    
### Extracting values from array

- Extract nested arrays:  
  ```
  a2 = np.extract(a1==a1, a1) # (condition, array where the values are extracted from)
  ex.: a1 = np.full((3,1),1)
       a1
         array([[1],
                [1],
                [1]])
       a2 = np.extract(a1==a1,a1)
       a2
         array([1, 1, 1])
  ```
- Extracting values given a condition: see the second enter of "Assigning" 

### Extracting indeces from array

- Extract indeces under condition:  
  ```
  ex: Extract where values are non-zero
      A = np.array([0,0,6,7,0]) 
      # find index
      index = np.where(A != 0)  
      index
        (array([2, 3]),)
      # extract values at index
      new_vector = A[index]    
      new_vector
        array([6, 7])
  ex: Array is 2D (it works the same way)
      x = np.arange(9.).reshape(3, 3)
      x
        array([[0., 1., 2.],
        [3., 4., 5.],
        [6., 7., 8.]])
      np.where( x > 5 )
        (array([2, 2, 2]), array([0, 1, 2]))  
  ```



### Assigning 
- When assigning an array to another use ``.copy``, otherwise the changes in the new vector will happen also in the old one:  
  ```
  ex. a = np.array([1,2,3])
      a
        array([ 1, 2, 3])
      b = a
      b
        array([ 1, 2,  3])
      b[1] = 10
      b
        array([ 1, 10,  3])
      a
        array([ 1, 10,  3])
      
      a = np.array([1,2,3])
      a
        array([ 1, 2, 3])
      b = np.copy(a)
      b
        array([ 1, 2,  3])
      b[1] = 10
      b
        array([ 1, 10,  3])
      a
        array([1, 2, 3])
      
      
  ```


- Array values of another array that respect a conditions (ex. masking an image):  
  ```
  ex.: a = np.array([[3, 1, 1, 2],
                     [3, 4, 3, 1],
                     [0, 5, 1, 0],
                     [3, 1, 2, 4],
                     [4, 4, 1, 4]]) 
       b = np.array([[0, 0, 0, 0],
                     [0, 1, 1, 0],
                     [0, 1, 1, 0],
                     [0, 1, 1, 0],
                     [0, 0, 0, 0]])
       f = np.where(b==1, a, 0) # condition, matrix from which assign values, background values
       f
         array([[0, 0, 0, 0],
                [0, 4, 3, 0],
                [0, 5, 1, 0],
                [0, 1, 2, 0],
                [0, 0, 0, 0]])
   ```
- Change array values under certain conditions:  
  ```
  ex.: y[y<0] = y[y<0] + 10
  ```
### Min, max, mean, std, abs
- ```
  np.amin(array)
  np.amax(array)
  np.mean(array)
  np.std(array)
  np.absolute(array)
  ```

### Size  
```
np.size(array)   # Number of elements  
np.size(array,0) # Number of rows 
np.size(array,1) # Number of columns
np.size(array,2) # Number of widths
```

### Add columns and rows to ndarray  
- Add columns: horizontal stack  
  ```
  a = np.array((1,2,3))
  a
    array([1, 2, 3])
  b = np.array((2,3,4))
  b
    array([2, 3, 4])
  np.hstack((a,b))
    array([1, 2, 3, 2, 3, 4])
  ```

- Add rows: vertical stack  
  ```
  a = np.array([1, 2, 3])
  a
    array([1, 2, 3])
  b = np.array([2, 3, 4])
  b
    array([2, 3, 4])
  np.vstack((a,b)) 
    array([[1, 2, 3],
           [2, 3, 4]])
  ```

### 3D Matrix to vector and back (vectorizing image to speed up computation)
```
a = np.array([[[ 1, 2, 3],[ 4, 5, 6]],[[ 7, 8, 9],[10,11,12]]])
a
  array([[[ 1,  2,  3],
          [ 4,  5,  6]],
         [[ 7,  8,  9],
          [10, 11, 12]]])
a_vector = np.reshape(a,(np.size(a),1)) # reshape to a vector
a_vector = np.extract(a_vector==a_vector,a_vector) # extract nested values
a_vector
  array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12])
a_back = np.reshape(a_vector,(np.size(a,0),np.size(a,1),np.size(a,2))) # reshape back to original nd array
a_back
  array([[[ 1,  2,  3],
          [ 4,  5,  6]],
         [[ 7,  8,  9],
          [10, 11, 12]]])
```

### Rounding
```
a = np.round(a, nOfDecimals) # rounds to the closest
```

###  Type
- Which type:
  ```
  a.dtype
  ```

- Change type:
  ```
  a = np.float32(a)
  ```
### Matrix visualization

```
pip install git+https://github.com/agoose77/numpy-html.git#egg=numpy-html
```
Example:
```
import numpy_html
import numpy as np

np.set_printoptions(threshold=5, edgeitems=2)
np.arange(49).reshape(7, 7)
```
