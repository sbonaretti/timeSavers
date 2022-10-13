# How to create documentation


## 1. For API: pdoc3

- Installation `pip install pdoc3`
- Documentation for a **module** (i.e. single file)
  - First time creation: `pdoc module_name --html`
  - For subsequent updates: `pdoc module_name --html --force` 
- Documentation for a **package** (i.e. several files). 
  - Give the folder the name of the package 
  - First time creation: `cd` to the parent folder of the package, then `pdoc package_name --html` 
  - For subsequent updates: `pdoc package_name --html --force`
- Notes about Numpy docstring syntax: 
  - Compatible with markdown
  - Use the plural for `Parameters` and `Returns`   
