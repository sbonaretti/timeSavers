# How to: GitHub

## Start a new repository on the website
- Go to github.com and to the personal page  
- Repository -> New  
- Enter repository name + click on "Private" + click on "Initialize the repository with a README" --> create a Repository  

## Sync repository locally
- Clone or download --> Open in desktop --> Clone to the desidered parent folder

## Ignore files to syncronize

- right click on one file to discard --> ignore  
- it creates automatically a new file: .gitignore that can be edited (right click -> Open with default program)  
    - add all the files with an extension (ex: *.hdr)   
    - add a whole folder (ex: parentFolderPath/folder)
- save  
- to refresh the file list, click on history and then click back on changes

## Synchronize a project after local changes
Two steps:
- commit: you write your locale .log file (sort of), so that if you work offline, you have the history
- pull/push (before it was sync) to synchronize with the server

## Branches in GitHub desktop  
(https://www.youtube.com/watch?v=6cLlX0ZqO5Q)  
- Open GitHub desktop and go to the repository you want to branch  
- Top Menu -> Branch -> New Branch (ex.: dev)  
- Menu under the top menu:  
  - Set Current Branch to dev  
  - Publish branch (check out it is there in the webapp)
- Setting the Current Branch in the top determines where the commit will go (to master or dev)  
- To merge changes in dev to the master branch, pull request:  
  - Current Branch -> Pull request (look if there is a better way - the video uses previous version of GitHub Desktop)
  - The master adds the dev branch  
  - Update the master locally  
 
## Create a token  
https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/
