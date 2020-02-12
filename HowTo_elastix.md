# How to: elastix

Software for medical image registration: http://elastix.isi.uu.nl/index.php

### Add elastix path to environment in OSX

In the terminal:

- Type: ``cd``
- Type: ``ls -a`` (shows also hidden files)
- Open or create:
  - Mac: 
    ``.bash_profile`` by typing: ``nano .bash_profile``  
  - Linux: 
    ``.bashrc`` by typing: ``nano .bashrc`` 
- Type: 
  - Mac:
    ```
    export PATH=yourelastixdir:$PATH
    export DYLD_LIBRARY_PATH=yourelastixdir:$DYLD_LIBRARY_PATH
    ```
    where ``yourelastixdir`` is something similar to `/anaconda3/lib/python3.7/site-packages/pykneer/elastix/Darwin/`
  - Linux: 
    ```
    export PATH=yourelastixdir:$PATH
    export LD_LIBRARY_PATH=yourelastixdir:$LD_LIBRARY_PATH
    ```
    where ``yourelastixdir`` is something similar to `/anaconda3/lib/python3.7/site-packages/pykneer/elastix/Linux/`

- Save changes by pressing: ctrl+o; return;
- Close file by pressing: ctrl+x
- Activate changes by typing: ``source .bash_profile``
