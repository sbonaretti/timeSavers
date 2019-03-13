# How to: Sherlock2
Sherlock2 is the computer cluster at Stanford

## OnDemand  
December 2018: interactive interface on the browser:
https://www.sherlock.stanford.edu/docs/user-guide/ondemand/  
To start: in browser copy/paste: https://login.sherlock.stanford.edu 

### My folders
- Data in scratch: `/scratch/users/sbonaret/data/`
- Code in home:    `/home/users/sbonaret/pykneer/pykneer/code/python/pykneer`

### Connection  
- On terminal:
  -  ssh sbonaret@login.sherlock.stanford.edu + 2 steps authentication  
- On fetch:  
  - Hostname: login.sherlock.stanford.edu  
  - Port:     22  
  - Username: SUNetID  
  - Password: SUNetID password  
  - SFTP  
  
(VPN connection not needed) 
  
### Software
- It has to be activated using the keyword `module` (equivalent to when double clicking on an icon)
- To look for a module: `module spider <module_name>`
- Module keywords here: https://www.sherlock.stanford.edu/docs/software/modules/#examples
- Reset environment: `ml reset`

