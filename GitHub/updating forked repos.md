## Updating a Forked Repo

#### Resources
- [Sophia's link, user tutorial](https://gist.github.com/CristinaSolana/1885435)  
- [Github Instructions](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)  
- [Setting up a remote](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork)


#### Pre-requisites
__Things that should already be installed__
- GitHub Desktop app
- *GitBash software (???)*

### How to Update a Forked Repo  
__A step-by-step tutorial__  
([from Sophia's tutorial/resources](https://gist.github.com/CristinaSolana/1885435), my comments given in *italics*)  

Sophia's steps are as follows:  
a. Clone your fork by putting the following command in terminal:  
- git clone git@github.com:YOUR-USERNAME/YOUR-FORKED-REPO.git
  - *is this what the correct link should look like? https://github.com/BITSS-OPA/opa-deworming.git*  
- (to get the link: click the green "clone or download" button in your online github repo)  

_my thoughts: could be useful to include more information on how to access the command terminal, also do these steps work on every operating system?_  

b. Put the commands in terminal:  
- cd into/cloned/fork-repo (you can find path by dragging your folder into terminal)
- git remote add upstream git://github.com/ORIGINAL-DEV-USERNAME/REPO-YOU-FORKED-FROM.git
- git fetch upstream
- git pull upstream master

c. Push in your local github desktop app

### Current Issues
- had trouble with accessing the command terminal (is this separate from the **command prompt**?)  
- do we need to use use GitBash and set up a remote following [these instructions](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork)?
- unclear which program should be downloaded in order to access GitBash (some posts online indicated that the program should be accessible via the GitHub desktop app)

### Common Issues // Troubleshooting  
- need to clearly state when other programs need to be installed (perhaps include a pre-requisite section)

##### Issues accessing the command terminal


#### Windows OS Specific issues

#### Mac OS Specific Issues
