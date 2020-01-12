# Git

## Introduction
* Git is a Version Control System(VCS).
* Git has a local and remote repository.
* GitHub is the most popular remote repository for Git.
* Files are edited in the Index or staging area, then commit to the local repos, then push to the remote repos.
* Remote repos have a HTTP link or SSH for local repos to connect with.
* GitHub repos have README.md file that will be display in its homepage.
* GUI apps are available for Git, however command line is recommended for learning purpose.
* One repository can have multiply branches, the first branch created by default it called master.

## Installation
* linux(Debian)
  ```
  sudo apt-get install git
  ```
* Linux(Fedora)
  ```
  sudo yum install git
  ```
* Mac, [Click](http://git-scm.com/download/mac) to download the installation package.
* Windows, [Click](http://git-scm.com/download/win) to download the installation package.

## Git Commands
### Setup Local Repository
* ``git command --help`` View help document.
* ``git help command`` View help document.
* ``git --version`` Check current version.
* ``git init`` Initialize Local Git Repository under the current folder. a hidden folder called .git will be created.
* ``rm -rf .git`` Stop using git for the project.
* ``git config --global user.name 'name'`` setup git username(required).
* ``git config --global user.email 'email'`` setup git user's email information(required).
* ``git config --list`` Check all config values.
* ``touch .gitignore`` Add the filename or folder addresses in the .gitignore file line by line, those files will be ignored by git.

### Managing Staging Area
* ``git log`` Show changes made to the repos.
* ``git add fileName.extension`` Add the file to the staging area.
* ``git add *.extension``	Add all files with certain extension to the staging area.
* ``git add .`` Add all files to the staging area.
* ``git add -A`` Add all files to the staging area.
* ``git reset fileName`` Remove the file to the staging area.
* ``git reset``	Remove all files from the staging area.
* ``git status`` Check the current staging area.
* ``git rm - -cached filename`` Remove the file from the Index.
* ``git commit`` Open and add commit message for the commit document, save the staging area to the local repos.
* ``git commit -m 'commit message'`` Commit the files with commit message.
* ``git diff`` View the difference made to the files.

### Branches
* ``git branch`` Create new branches.
* ``git branch --merge`` Show the branch merged.
* ``git branch -d branchName`` Delete the branch locally
* ``git push origin --delete branchName`` Delete the branch in the remote repos.
* ``git checkout branchName`` Switch branch
* ``git merge branchName`` Merge certain branch to the current branch, when done input commit message.

### Working with Remote Repository
* ``git remote`` List all the current remote repos.
* ``git remote add origin URL`` Add the remote repos.
* ``git push -u origin master`` Add the current master branch to the remote repo origin
* ``git push`` Add the current master brach to its corresponding repo.
* ``git pull``	Pull the latest from the remote repos
* ``git clone URL`` Clone repos into the current directory.
* ``git clone URL folderAddress`` Clone repos into the certain directory.
