# How to: python  

- [Lists](#Lists)  
- [Strings](#Strings)  
- [Tuples](#Tuples)  
- [Packages](#Packages)  
- [Python version](#Python-version)  
- [Kill all python processes](#Kill-all-python-processes)  
- [Get time of process](#Get-time-of-process))

---

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
- Get unique elements (using sets)  
  ```
  my_list_set = set(my_list)  
  unique_elements = list(my_list_set) # note that "list"  here is a function   
  ```
  
--- 

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
- Split string: 
  - In two parts, before and after character: 
    ```
    part1, part2 = url.rsplit('/', 1)
    ```
  - Get only first or second part:  
    ```
    part1 = url.rsplit('/', 1)[0]
    part2 = url.rsplit('/', 1)[1]
    ```

---

### Tuples  
- Find element in tuples and get index:  
  ```
  if element in tuple:
        index = tuple.index(element)
  ```  
- Check if tuple is empty:  
  ```
  if len(tuple) == 0: 
     ...
  ```

---

### Packages  

- To install a package: `pip install <packageName>`  
- To update a package: `pip install <packageName> --upgrade`  
- To remove a package: `pip uninstall <packageName>`
- To list packages: `pip freeze`  

---

### Python version 
- To know python version: `python --version`

---

### Kill all python processes
- In terminal: `pkill -f python`

---

### Get time of process 
- To print out the time of a process:
  ```
  import time
  start_time = time.time()
  # [code here]
  print ("-> The total time was %.2f seconds (about %d min)" % ((time.time() - start_time), (time.time() - start_time)/60))
  ```


