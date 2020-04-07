# Git

## Introduction

- Git is a Version Control System(VCS).
- Git has a local and remote repository.
- GitHub is the most popular remote repository for Git.
- Files are edited in the Index or staging area, then commit to the local repos, then push to the remote repos.
- Remote repos have a HTTP link or SSH for local repos to connect with.
- GitHub repos have README.md file that will be display in its homepage.
- GUI apps are available for Git, however command line is recommended for learning purposes.
- One repository can have multiple branches, the first branch created by default it called master.
- The master branch is usually shared by the team, regular commits are suggested to make on a separate branch.

## Installation

- linux(Debian)
  ```
  sudo apt-get install git
  ```
- Linux(Fedora)
  ```
  sudo yum install git
  ```
- Mac, [Click](http://git-scm.com/download/mac) to download the installation package.
- Windows, [Click](http://git-scm.com/download/win) to download the installation package.

## Git Commands

- [Click](https://git-scm.com/docs) to list a full list of commands.

### Setup Local Repository

- `git command --help` View help document.
- `git help command` View help document.
- `git --version` Check current version.
- `git init` Initialize Local Git Repository under the current folder. a hidden folder called .git will be created.
- `rm -rf .git` Stop using git for the project.
- `git config --global user.name 'name'` setup git username(required).
- `git config --global user.email 'email'` setup git user's email information(required).
- `git config --list` Check all config values.
- `touch .gitignore` Add the filename or folder addresses in the .gitignore file line by line, those files will be ignored by git.

### Managing Staging Area

- `git log` Show changes made to the repos.
- `git add fileName.extension` Add the file to the staging area.
- `git add *.extension` Add all files with certain extension to the staging area.
- `git add .` Add all files to the staging area.
- `git add -A` Add all files to the staging area.
- `git reset fileName` Remove the file to the staging area.
- `git reset` Remove all files from the staging area.
- `git status` Check the current staging area.
- `git rm - -cached filename` Remove the file from the Index.
- `git commit` Open and add commit message for the commit document, save the staging area to the local repos.
- `git commit -m 'commit message'` Commit the files with commit message.
- `git diff <branch1> <branch2>` View difference between branches.

### Branches

- `git branch` lists local branches and shows the current working branch.
- `git branch -a` lists all local and its corresponding remote tracking branches.
- `git branch <branchname>` create a new local branch.
- `git branch --merge` Show the branch merged.
- `git branch -m <oldbranch> <newbranch>` rename a local branch.
  - If the current working branch is the `<oldbrach>`, run `git branch -m <newbranch>` to rename.
  - To sync remote branch names, delete the remote `<oldbranch>`, and push the `<newbranch>`.
- `git branch -d branchName` Delete the branch locally.
- `git branch --set-upstream-to <remoteBranchName>` or `git branch -u <remoteBranchName>` set the remote tracking branch for the local branch.
- `git push origin --delete branchName` Delete the branch in the remote repos.
- `git checkout branchName` Switch branch.
- `git merge` Combines remote tracking branch into current local branch.
- `git merge branchName` Merge certain branch to the current branch, when done input commit message.

### Working with Remote Repository

- `git remote` List all the current remote repos.
- `git remote add origin <URL>` Add the remote repos.
  - For Github repos, the URL is usually like, `https://github.com/AccountName/ReposName.git`
- `git push -u origin <remoteBranch>` Add the current branch to certain remote branch and set the remote branch as the remote tracking branch.
- `git push` update the remote repo with its corresponding local branch.
- `git pull <URLorRemoteBranchName>` pull from a certain remote branch.
- `git pull` Pull the latest from the remote repos
- `git clone URL` Clone repos into the current directory.
- `git clone URL folderAddress` Clone repos into the certain directory.
