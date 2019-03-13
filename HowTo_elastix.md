# How to: elastix

In the terminal:

- Type: ``cd``
- Type: ``ls -a`` (shows also hidden files)
- Open or create ``.bash_profile`` by typing: ``nano .bash_profile``
- Type:

 - On mac: ``export DYLD_LIBRARY_PATH=yourelastixdir/lib:$DYLD_LIBRARY_PATH``
 - On linux ``export LD_LIBRARY_PATH=yourelastixdir/lib:$LD_LIBRARY_PATH``

 where ``yourelastixdir`` is ``/Users/YourUserName/kneeanalysis/pykneer/``, with ``YourUserName`` being your actual user name

- Save changes by pressing: ctrl+o; return;
- Close file by pressing: ctrl+x
- Activate changes by typing: ``source .bash_profile``
