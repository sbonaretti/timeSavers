# How to: Create a Python Package

This is the way I did/am doing for *pyKNEEr* - Learning in progress

[Upgrade package](#upgrade-package)  

[Create package from scratch](#create-new-package-from-scratch)   


--- 


## UPGRADE PACKAGE

**From version 0.0.4: Working with GitHub branches**  

&nbsp; [1. Set up](#1-Set-up)    
&nbsp; [2. Modifying code](#2-Modifying-code)  
&nbsp; [3. Testing code](#3-Testing-code)  
&nbsp; [4. Create new package](#4-Create-new-package)  
&nbsp; [5. Release new package](#5-Release-new-package)  

### 1. Set up
- In GitHub desktop, current branch tab (top center) :  
  - Create a new branck: -> New branch -> Name (e.g. v004)   
  - Select the created new branch  
  
- Activate the python virtual environment:  
  ```
  source pyKNEEr/bin/activate
  ```  
  
- Manually update version number in `setup.py`  


### 2. Modifying code 
- **Spyder** 
  - Make sure you are in virtual environment:  
    ```
    source pyKNEEr/bin/activate
    ```  
  - Open spyder from terminal: 
    ```
    spyder
    ```   
    (If not installed yet: `pip install spyder`   
    Thread: https://stackoverflow.com/questions/30170468/how-to-run-spyder-in-virtual-environment) 

  - Fix bugs / Implement and test new code in spyder - leave the Jupyter notebooks to the very end (they are the user interface!) 
  
  
- **Jupyter notebooks** (user interface)  

  - 2 ways: 
    1. pyKNEEr not installed (quick and dirty way):

        - Make sure you are in virtual environment:  
          ```
          # cd to folder /pyKNEEr/ (where the folder bin is)
          source bin/activate
          ```  
        - Uninstall current version:  
          ```
          pip uninstall pykneer
          ```  
        - Copy/paste file withfunction to modify to the notebook folder
        - Open Jupyter lab and go to the `pyKNEEr` kernel (top-right button)  
        - Add the autoreload to the top of the notebook:
          ```
          # Make sure there are no empty spaces at the end of the lines 
          %load_ext autoreload 
          %autoreload 2
          ```
          and add the module to import, not the package:  
          ```
          import pykneer_io
          ```
          and not `from pykneer import pykneer_io as io`
        - Cut/paste the new function back to the folder containing source code
        
    2. With installation of pyKNEEr release I am working on: 

        - Make sure you are in virtual environment:  
          ```
          # cd to folder /pyKNEEr/ (where the folder bin is)
          source bin/activate
          ```  
        - Uninstall current version:  
          ```
          pip uninstall pykneer
          ```  
          (For ITK: installed packages are in `lib/python3.7/site-packages`)

        - Install work-in-progress version:   
          ```
          # cd to folder /pyKNEEr/pykneer (where the file setup.py is)
          python setup.py develop
          ```
          Note: package is installed in the directory as `setup.py`, not in the parent directory  

        - Launch JupyterLab from terminal:
          ```
          jupyter lab
          ```  
          To close: `crtl + c`  
          Note: make sure to re-import pyKNEEr (top of notebook)

        - Use pyKNEEr's kernel if already existing. If not, create a [new kernel](https://anbasile.github.io/programming/2017/06/25/jupyter-venv/):  
          ```
          pip install ipykernel
          ipython kernel install --user --name=projectname
          ```
          Select the new kernel from the notebook (top-right)

- **PyCharm**
  - Used for the editing of the code documentation because it does grammar check   
  - Not used for coding because it does not have the iphython module (need to run the whole function to debug, like VisualStudio)


### 3. Testing code  
- Make sure you are in virtual environment:  
    ```
    source pyKNEEr/bin/activate
    [to finish]
    ```
        
### 4. Create new package

#### Create the package
- Update version number in `setup.py`  
- Add new files (if any) to `__init__.py`
- Create the package
  ```
  #cd to setup.py folder, not in virtual environment
  python3 setup.py sdist bdist_wheel
  ```
  It creates ``dist/*.whl``, which is the executable


#### Test the package  
- Create a new virtual environment and activate it
  ```
  virtualenv test_release
  source test_release/bin/activate
  ```  
- Copy paste the new package (`*.whl`) from the directory `pip/pykneer/dist` to the directory `test_release`  
- Install `itk 4.3` if still needed:  
  ```
  cd test_release
  pip install itk-core==4.13.1.post1 itk-numerics==4.13.1.post1 itk-filtering==4.13.1.post1 itk-io==4.13.1.post1 itk-segmentation==4.13.1.post1 itk-registration==4.13.1.post1 --force-reinstall --no-cache-dir
  pip install itk==4.13.1.post1
  ```
- Install package from local executable
  ```
  pip install pykneer-0.0.3-py3-none-any.whl # use autofill to install the new version
  ```
- Install notebook in virtual environment (it might already be installed):
  ```
  pip install ipykernel
  ```
- Create kernel in virtual environment (it might already be present):
  ``` 
  python -m ipykernel install --user --name=test_release
  ```
- In `test_release` copy the `demo/input` folder, open the notebooks and  
  - Click the button in the top right of the notebook and select the kernel in test_release  
  - Run all the notebooks of the demo

### 5. Release new package 
- Upload to pypi:  
  ```
  #cd to pyKNEEr/pykneer
  python3 -m twine upload dist/*
  ```

- Commit the new version to GitHub

- Add release to Zenodo for DOI
  
  FIRST TIME (see https://github.com/QMSKI/TransparentQMSKI/wiki/How-To:-Upload-to-Zenodo#github_code)
  Note: Do not create release on GitHub  
  - Go to menu next to email on top-right and click `GitHub`
  - Select the repository name   
    - 1. Flip the switch  (press the button)
    - 2. Create the release (press the button). In GitHub:
      - Fill out: Tag version (e.g. v0.0.4), Release Title  (e.g. pyKNEEr 0.0.4)
      - `Publish release`
  - Go back to Zenodo (https://zenodo.org/account/settings/github/) and click on your repository:
    - Get your DOI badge for your website, documents, etc.
    - Click the DOI link
    - Once in your new data page, click Edit to fill out your metadata. Make sure to:
      - Add the QMKSI community
      - Add the license
      - Save and Publish



- Install new version locally: 
  ```
  pip install pykneer --upgrade
  pip show pykneer
  ```



------------------------------------------------------------------------------------------------

## CREATE NEW PACKAGE FROM SCRATCH

&nbsp; [Create a virtual environment](#create-a-virtual-environment)  
&nbsp; [Folder and file structure](#folder-and-file-structure)  
&nbsp; &nbsp; [setup.py](#setup.py)  
&nbsp; &nbsp; [Additions to code](#additions-to-code)  
&nbsp; &nbsp; &nbsp; [Python packages](#python-packages)   
&nbsp; &nbsp; &nbsp; [Modules](#modules)   
&nbsp; &nbsp; &nbsp; [Text files](#text-files)   
&nbsp; &nbsp; &nbsp; [Binaries](#binaries)  
&nbsp; &nbsp; &nbsp; [Binaries](#binaries)  
&nbsp; &nbsp; &nbsp; [Tests](#tests)   
&nbsp; &nbsp; [License](#license)  
&nbsp; &nbsp; [README.md](#readme.md)  
&nbsp; [Commands](#commands)   
&nbsp; &nbsp; [Create a package](#create-a-package)  
&nbsp; &nbsp; [Install a package](#install-a-package)  
&nbsp; &nbsp;  &nbsp; [Install package from local executable](#install-package-from-local-executable)  
&nbsp; &nbsp;  &nbsp; [Install package from test.pypi.org](#install-package-from-test.pypi.org)  
&nbsp; [Conventions](#conventions)    
&nbsp; [Test with Jupyter notebook](#test-with-Jupyter-notebook)   
&nbsp; [Upload to pypi.org](#upload-to-pypi.org)  
&nbsp; [Usefull websites](#usefull-websites)  
&nbsp; [Tricks](#tricks)  

### Create a virtual environment
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

### Folder and file structure
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

#### setup.py
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

Important: For following versions, update the line `version="0.0.1"` to the new version


#### Additions to code 

##### Python packages
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

##### Modules
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

##### Text files (<folder_with_parameters>)

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

##### Binaries (<folder_with_executables>)
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


##### Tests 

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

#### LICENSE
- Choose a license: https://choosealicense.com
- Copy the text in the file LICENSE
- Add the license to setup.py (Sintax: https://autopilot-docs.readthedocs.io/en/latest/license_list.html)


#### README.md
Brief description of package

### Commands

#### Create a package
```
python3 setup.py sdist bdist_wheel
```
It creates ``dist/*.whl``, which is the executable

#### Install a package

##### Install package from local executable (easy and recommended)
Example:
```
pip install dist/my_package-0.0.1-py3-none-any.whl
```

##### From test.pypi.org (more complicated, not necessary)
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

### Conventions  
- General conventions: https://www.python.org/dev/peps/pep-0008/  
- Naming conventions:  https://www.python.org/dev/peps/pep-0008/#naming-conventions  
  - _Modules_ should have short, all-lowercase names. Underscores can be used in the module name if it improves readability.  
  - _Packages_ should also have short, all-lowercase names, although the use of underscores is discouraged.  
  - _Class_ names should normally use the CapWords convention.  
  - _Function_ names should be lowercase, with words separated by underscores as necessary to improve readability. _Variable_ names follow the same convention as function names. mixedCase is allowed only in contexts where that's already the prevailing style (e.g. threading.py), to retain backwards compatibility.  
- _Docstrings_: They are the comments in modules. Check out here: https://www.python.org/dev/peps/pep-0257/   

### Test with Jupyter notebook
Install notebook in virtual environment:
```
pip install ipykernel
python -m ipykernel install --user --name=<env_name>
```
Click the button in the top right of the notebook and select the kernel in <env_name>  
Note: autoreload not working  - look for how to install it

### Upload to pypi.org
- Register here: https://pypi.org/account/register/
- `cd` to the folder 
- Upload the package
  ```
  python3 -m twine upload dist/*
  ```

### Usefull websites

https://ewencp.org/blog/a-brief-introduction-to-packaging-python/  
https://inventwithpython.com/blog/2018/10/22/a-curriculum-for-python-packaging/ (summary of videos)  
https://packaging.python.org/ (official page)  

### Tricks
Matplotlib has issues with virtual environments on mac. To make it work, create ``matplotlibrc``:
```
cd ~/.matplotlib
nano matplotlibrc
```
and add:
```
backend: TkAgg
```

