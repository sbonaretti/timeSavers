# How to: Create a Python Package

## Create a virtual environment
```
# Go to folder
cd <folder>
# Create virtual environment
virtualenv <env_name>
# Activate virtual environment
source <env_name>/bin/activate

# Deactivate
deactivate
```

## Folder and file structure
Instructions from https://packaging.python.org/  
Folder structure in <env_name>:
```
<package>
    |
    |  (mandatory)
    |_ setup.py
    |_ requirements.txt
    |_ LICENSE
    |_ README.md
    |
    |  (optional)
    |_ setup.cfg 
    |_ MANIFEST.in
    |
    |  (code)
    |_ my_package
         |
         |  (mandatory)
         |_ __init__.py
         |_ *.py
         |
         |_ (optional)
         |_ <folder_with_parameters>
         |_ <folder_with_executables>
         |_ tests
              |_ test_*.py
    
```

### setup.py
It contains all the info to create the package  
Example:
```
import setuptools
from pathlib import Path

with open("README.md", "r") as fh:
    long_description = fh.read()

setuptools.setup(

    name="my_package",                              
    version="0.0.1",                               
    author="Example Author",
    author_email="author@example.com",
    description="A small example package",
    long_description=long_description,
    long_description_content_type="text/markdown",
    url="https://github.com/pypa/sampleproject",
    
    # including requirements (dependencies)     
    install_requires=[
        l.strip() for l in
        Path('requirements.txt').read_text('utf-8').splitlines()
    ],
    
    # including parameterFolder and Elastix package
    packages=setuptools.find_packages(),
    package_data={'': ['*.txt'],
                  '': ['Darwin/*']
    },
    include_package_data=True,
    
    # including tests
    setup_requires=["pytest-runner"],
    tests_require=["pytest"],
    
    # more stuff
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: GNU General Public License v3 (GPLv3)",
        "Operating System :: OS Independent",
    ],
)
```



### Additions to code 

#### python packages
In ``requirements.txt`` list packages and version  
Example: 
```
numpy>=1.15.1
pandas>=0.23.4
```

In ``setup.py`` add:
```
# top of file
from pathlib import Path

# In the function 'setuptools.setup':
install_requires=[
        l.strip() for l in
        Path('requirements.txt').read_text('utf-8').splitlines()
    ],
```

#### modules
Add modules to ``my_package/__init__.py``.
Example:
```
from . import pykneer_io as io  # this is a file
from . import cylinder_fitting  # This is a folder, containing another package (it has its own __init__.py)
```

In the code, when calling a dependent module, add ``from .``  
Example:
```
from . import pykneer_io as io

```

#### text files (<folder_with_parameters>)

In``MANIFEST.in``:
```
include my_package/parameterFiles/*.txt
```

In ``setup.py`` add:
```
# In the function 'setuptools.setup':
packages=setuptools.find_packages(),
package_data={'': '*.txt'},
include_package_data=True,
```

In the code, to add path to <folder_with_parameters>:
```
import pkg_resources 
```
For a file:
```
DATA_PATH = pkg_resources.resource_filename('example_pkg','parameterFiles/MR_param_rigid.txt')
# assign DATA_PATH where needed
```
For a folder: 
```
DATA_PATH = pkg_resources.resource_filename('example_pkg','parameterFiles/')
# assign DATA_PATH where needed
```

#### Binaries (<folder_with_executables>)
In``MANIFEST.in``:
```
include example_pkg/Darwin/*    # Contains binaries for OS
```

Setup ``setup.py`` becomes (adding to right above):
```
# In the function 'setuptools.setup':
packages=setuptools.find_packages(),
    package_data={'': ['*.txt'],
                  '': ['Darwin/*']
    },
```
In the code, same as right above


#### Tests 

In ``setup.cfg``:
```
[aliases]
test=pytest
[tool:pytest]
addopts = --verbose
python_files = tests/test_*.py  # As a convention, test file are named test_*.py
```

In ``setup.py``:
```
# In the function 'setuptools.setup':
setup_requires=["pytest-runner"],
tests_require=["pytest"],
```

Run all test (after installation):
```
python setup.py test
```

### LICENSE
- Choose a license: https://choosealicense.com
- Copy the text in the file LICENSE
- Add the license to setup.py (Sintax: https://autopilot-docs.readthedocs.io/en/latest/license_list.html)


### README.md
Brief description of package

## Commands

### Create a package
```
python3 setup.py sdist bdist_wheel
```
It creates ``dist/*.whl``, which is the executable

### Install a package

#### Install package from local executable (easy and recommended)
Example:
```
pip install dist/my_package-0.0.1-py3-none-any.whl
```

#### From test.pypi.org (more complicated, not necessary)
- Create an account
- Make sure to increase the version every time in``setup.py``:
  ```
  version="0.0.x"
  ```
- Upload the package
  ```
  python3 -m twine upload --repository-url https://test.pypi.org/legacy/ dist/*
  ```
- Download the package:
  ```
  pip install -i https://test.pypi.org/simple/ my_package               # the first time
  pip install -i https://test.pypi.org/simple/ my_package --upgrade     # the following times
  ```

## Conventions  
- General conventions: https://www.python.org/dev/peps/pep-0008/  
- Naming conventions:  https://www.python.org/dev/peps/pep-0008/#naming-conventions  
  - _Modules_ should have short, all-lowercase names. Underscores can be used in the module name if it improves readability.  
  - _Packages_ should also have short, all-lowercase names, although the use of underscores is discouraged.  
  - _Class_ names should normally use the CapWords convention.  
  - _Function_ names should be lowercase, with words separated by underscores as necessary to improve readability. _Variable_ names follow the same convention as function names. mixedCase is allowed only in contexts where that's already the prevailing style (e.g. threading.py), to retain backwards compatibility.  
- _Docstrings_: They are the comments in modules. Check out here: https://www.python.org/dev/peps/pep-0257/   

## Test with Jupyter notebook
Install notebook in virtual environment:
```
pip install ipykernel
python -m ipykernel install --user --name=<env_name>
```
Click the button in the top right of the notebook and select the kernel in <env_name>  
Note: autoreload not working  - look for how to install it

## Upload to pypi.org
- Register here: https://pypi.org/account/register/
- `cd` to the folder 
- Upload the package
  ```
  python3 -m twine upload dist/*


## Usefull websites

https://ewencp.org/blog/a-brief-introduction-to-packaging-python/  
https://inventwithpython.com/blog/2018/10/22/a-curriculum-for-python-packaging/ (summary of videos)  
https://packaging.python.org/ (official page)  

## Tricks
Matplotlib has issues with virtual environments on mac. To make it work, create ``matplotlibrc``:
```
cd ~/.matplotlib
nano matplotlibrc
```
and add:
```
backend: TkAgg
```