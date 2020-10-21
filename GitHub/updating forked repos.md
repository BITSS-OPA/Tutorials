## Updating a Forked Repo

**Remember to do this first before you start editing files on your own forked version to keep synced**

#### Resources
- [Sophia's link, user tutorial](https://gist.github.com/CristinaSolana/1885435)  
- [Github Instructions](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)  
- [Setting up a remote](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork)


#### Pre-requisites
- you have forked a repository and cloned it to your local device  
  + To clone the repo, run `git clone forked-repo-url` in a folder where you want the repository files to be

__Things that should already be installed__
- GitHub Desktop app
- [Git](https://git-scm.com/downloads)
  - [installation guides](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

### How to Update a Forked Repo  
Assuming you have already cloned your forked repo to your local device, there are two methods for updating a forked repo:  
  1) from within the repository folder, and  
  2) from the command terminal.

##### Method 1: Within the repository
1. Navigate to the folder on your computer where the repository is saved
2. Right-click and select the 'Git Bash Here' command
3. enter the command
```git
git fetch upstream
```
4. enter the command
```git
git pull upstream master
```
5. Push to origin within your local GitHub desktop app within the relevant repository or enter the following command (you may need to login to your GitHub account to do so)
```git
git push
```

##### Method 2: From the Command terminal (Recommended)
1. Locate the file path of the repository you would like to update  
  a. can be done by dragging your folder into the terminal or right-clicking and copying the file path
2. Open your device's command terminal (may also be referred to as the command prompt)
3. enter the command
```git
cd 'your file path'
```
4. enter the command
```git
git fetch upstream
```
5. enter the command
```git
git pull upstream master
```
6. Push to origin within your local GitHub desktop app within the relevant repository or enter the following command (you may need to login to your GitHub account to do so)
```git
git push
```

Note: if there are issues with step 4, insert these following steps:
1. Go to github.com and copy the url of the master repository you wish to update from
2. enter the command
```git
git remote add upstream git://github.com/.../.../
```
where you insert the url for the master repository

### Common Issues // Troubleshooting  
Here are some solutions to common issues you may have come across!  
- make sure that you have installed all of the necessary software!
  - make sure you have downloaded Git!!!
- try the other method if one of them is not working for you (though the first method is recommended as it is slightly less complicated and you have zero chance of getting the file path wrong)
- make sure you have the correct file path!
  - if you cannot figure out how to copy the file path, then try method 1 or drag the folder itself into the command terminal

##### Issues accessing the command terminal
- you can access or find the command terminal by searching the term 'command' in your start menu
- the command terminal is the same thing as the command prompt for Windows operating systems
- the command terminal is merely a way for you to 'speak directly' to your computer, as it were... it should only have your computer's  user preset as the location from which you're accessing it
- if you have issues accessing the command terminal, perhaps try using the other method!
