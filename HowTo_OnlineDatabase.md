# How to: Online database


## .json

### Access database using `get`
- Import `requests` (https://realpython.com/python-requests/) and declare db address: 
  ```
  import requests # to access website  
  chemidconvert = 'https://chemidconvert.cloud.douglasconnect.com/v1/' # website path

  ```

- Check that you can access database and field (output = 200): 
  ```
  smiles = requests.get(chemidconvert + 'name/to/smiles', params={'name': 'paracetamol'})
  ```
  ```
  # Output: <Response [200]>
  ```

- Extract field in .json format:   
  ```
  smiles = requests.get(chemidconvert + 'name/to/smiles', params={'name': 'paracetamol'}).json()  
  ```
  ```
  # Output: {'smiles': 'CC(=O)Nc1ccc(O)cc1'}  
  ```
  
- Extract field value:  
  ```
  smiles = requests.get(chemidconvert + 'name/to/smiles', params={'name': 'paracetamol'}).json()['smiles']
  ```
  ```
  # Output: CC(=O)Nc1ccc(O)cc1
  ```

### Filter database using `params`  
Parameters can be written in a dictionary.  
e.g. ```


