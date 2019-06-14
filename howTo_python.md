# How to: python  

### Lists
- Add array to one single cell  
  ```
  list.append(array)
  ```
- Add each element of an array to a separate cell of a list  
  ```
  list.extend(array)
  ```
- Check if element is empty:  
  ```
  for i in range (0, len(list)):
    if not list[i]:
        print (i)
  ```
- Delete element given index:  
  ```
  array = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
  del array[1]
  -> 1
  ```
- Check if element is already in list:   
  ```
  if element in list:
  ```
- Convert list of lists to one single list  
  ```
  from itertools import chain
  long_list = list(chain.from_iterable(list_of_lists))
  ```
  
  

### Strings  
- Find substring in string:  
  - In general (returns the index for the first letter):
    ```
    main_string = "ciao"
    sub_string = "ao"
    main_string.find(sub_string)
    ```
  - In `if` (returns -1 if string not found): 
    ```
    if main_string.find(sub_string) != -1:
        print ("found")
    ```
    or
    ```
    if sub_string in main_string:
        print ("found")
    ```
- Find string in list of strings:  
  - In `if`:
    ```
    if string in list_of_string:
        print ("found")
    ```  
  - Get index:  
    ```
    index = list_of_string.index(string)
    ```
- Find overlap between two list of strings (returns a list with overlapping terms):  
  ```
  overlap = list(set(list_of_strings_1) & set(list_of_strings_2))
  ```
- Substitute sub_string in string:  
  ```
  main_string = main_string.replace('old_sub_string', 'new_sub_string')
  ```

### Packages  

- To install a package: `pip install <packageName>`  
- To update a package: `pip install <packageName> --upgrade`  
- To remove a package: `pip uninstall <packageName>`
- To list packages: `pip freeze`  

### Python version 
- To know python version: `python --version`

### Kill all python processes
- In terminal: `pkill -f python`


