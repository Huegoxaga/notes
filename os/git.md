# Version Control Systems

## Git CLI

### Introduction

- Git is a Version Control System(VCS).
- Git has a local and remote repository.
- GitHub is the most popular remote repository for Git.
- Files are edited in the Index or staging area, then commit to the local repos, then push to the remote repos.
- Remote repos have a HTTP link or SSH for local repos to connect with.
- GitHub repos have README.md file that will be display in its homepage.
- GUI apps are available for Git, however command line is recommended for learning purposes.
- One repository can have multiple branches, the first branch created by default it called master.
- The master branch is usually shared by the team, regular commits are suggested to make on a separate branch.
- There is a HEAD in each repo, by default it is the master branch. It can be set in the repo setting.
- When a branch is ahead of the `HEAD`, it can be merged to the HEAD to update the `HEAD`.
- When a branch is behind the `HEAD`, it can `pull` the head and update from the `HEAD`.
- A fast-forward is when, instead of constructing a merge commit, git just moves your branch pointer to point at the incoming commit. It happens if it detects that the current `HEAD` is an ancestor of the commit you're trying to merge.

### Installation

- linux(Debian)
  ```
  sudo apt-get install git
  ```
- Linux(Fedora)
  ```
  sudo yum install git
  ```
- Mac, run `brew install git`.
- Windows, [Click](http://git-scm.com/download/win) to download the installation package.

### Git Commands

- [Click](https://git-scm.com/docs) to list a full list of commands.

#### Setup Local Repository

- `git command --help` View help document.
- `git help command` View help document.
- `git --version` Check current version.
- `git init` Initialize Local Git Repository under the current folder. a hidden folder called .git will be created.
- `rm -rf .git` Stop using git for the project.
- `git config --global user.name 'name'` setup git username(required).
- `git config --global user.email 'email'` setup git user's email information(required).
- `git config --list` Check all config values.
- `git gc` cleanup unnecessary files and optimize the local repository in the `.git` folder
- `git clean -f` Remove untracked files from the working tree
- `touch .gitignore` Add the filename or folder addresses in the .gitignore file line by line, those files will be ignored by git.

#### Managing Staging Area

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

#### Branches

- `git branch` lists local branches and shows the current working branch.
- `git branch -a` lists all local and its corresponding remote tracking branches.
- `git branch <branchname>` create a new local branch.
- `git branch --merge` Show the branch merged.
- `git branch -m <oldbranch> <newbranch>` rename a local branch.
  - If the current working branch is the `<oldbrach>`, run `git branch -m <newbranch>` to rename.
  - To sync remote branch names, delete the remote `<oldbranch>`, and push the `<newbranch>`.
- `git branch -M <newbranch>` create new branch then checkout to the new branch
- `git branch -d branchName` Delete the branch locally.
- `git push -d origin <BranchName>` Delete remote branch
- `git branch --set-upstream-to <remoteBranchName>` or `git branch -u <remoteBranchName>` set the remote tracking branch for the local branch.
- `git push origin --delete branchName` Delete the branch in the remote repos.
- `git checkout branchName` Switch branch.
- `git checkout -b branchName` create a new branch and switch to that branch.
- `git fetch origin && git checkout -b remoteBranchName origin/remoteBranchName` add a new remote branch to local
- `git merge` Combines remote tracking branch into current local branch.
- `git merge branchName` Merge certain branch to the current branch, when done input commit message.
- `git merge origin/remoteBranch --no-commit --no-ff` Merge certain remote branch to the current branch, when done input commit message.
  - When making pull request that will not be able to auto-merged, merge code locally then push it, then auto merge for the pull request will be enabled.
    - When merge a branch into master, checkout the this branch run `git merge master`, then checkout to master run `git merge --no-ff --no-commit <BranchName>` then commit and push
  - The `--no-ff` flag prevents git merge from executing a `fast-forward`
    - `fast-forward` will replace the header pointer without creating new commit if no changes are made
  - `--ff-only` means fast-forward only.
- `git rebase` similar to merge but keep all the commit records of the merging branch into the master branch after it is merged, example usage:
  1. `git checkout branch`
  2. `git rebase master`
  3. `git checkout master`
  4. `git merge branch`

#### Working with Remote Repository

- `git log` see records and past commit id
- `git revert <commitID>` revert back a certain commit and commit the changes.
- `git reset <commitID>` reset the files to the state after a certain commit.
  - use `git push --force` will delete all the newer commits in the remote repo.
- `git remote` List all the current remote repos.
- `git remote add origin <URL>` Add the remote repos.
  - For Github repos, the URL is usually like, `https://github.com/AccountName/ReposName.git`
- `git remote show origin` check the tracking config
- `git remote set-url origin <URL>` update remote URL(happens when repo name changed)
- `git config --get remote.origin.url` check the current tracking remote URL
  - or `git remote -v`
- `git push -u origin <remoteBranch>` push to certain remote branch and set the remote branch as the remote tracking branch.
  - create new remote branch if not exists
- `git push` update the remote repo with its corresponding local branch.
- `git push origin <branchName>` push to a certain remote branch.
- `git fetch origin` git fetch is similar to pull but doesn't merge. It fetches remote updates but the local stays the same.
- `git pull <URLorRemoteBranchName>` pull from a certain remote branch.
  - `git pull origin master --no-commit` this is recommanded to merge new codes from master before sending pull request from working branches.
- `git pull` Pull the latest from the remote repos
- `git clone URL` Clone repos into the current directory.
- `git clone URL folderAddress` Clone repos into the certain directory.

## Git Large File Storage(LFS)

- Use Git LFS when a file has size larger than 100MB

### Setup

- run `brew install git-lfs`
- run `git lfs install` to signin
- run `git lfs track "<large_file>"` to let `lfs` handle large file
  - a record in `.gitattributes` file will be created
- During future `git push` large files will be automatically managed by `lfs`
  - Rollback is required when large file has already been committed to the local repo

## GitHub CLI

- It enables the full access to the GitHub Website using CLI
- [Click Here](https://cli.github.com/manual/) to view the official manual
- Installation, run `brew install gh` to install
- add `eval "$(gh completion --shell <bash|zsh|fish|powershell>)"` in the dot file in order to setup command auto completion with tab
- `gh` command has two level and has a `gh <FirstLevel><SecondLevel>` structure, it has the following first level command:
- `auth` is used to manage user login, it has the following second level command
  - `login` login to the GitHub account
  - `logout` logout
  - `refresh` same as logout then login
  - `status` View authentication status
- `repo` is used to manage repositories, it has the following second level command
  - `create` create a repository under your account using the current directory name
    - `create <ProjectName>` create a repository with a specific name
    - `create <Organization/Username>/<ProjectName>` create a repository in an organization
      - `--private` Make the new repository private
  - `clone <URL>` clone a repo
  - `clone <Organization/Username>/<ProjectName>` clone a repo
- `pr` is used to manage pull requests, it has the following second level command
  - By default the command will access the pull request that belongs to the current branch, all second level command can acess a specific request by appending argument including `<RequestNumber>`, `<RequestUrl>`, `<RequestBranch>`
  - `list` List and filter pull requests in this repository
    - `-s open` list open request only
  - `view` View the pull request that belongs to the current branch
  - `status` Check the status of the pull request in the current branch
  - `create` Create a pull request interactively
    - `create --title "Pull request title" --body "Pull request body"`
    - `create --web` Quickly navigate to the pull request creation page
  - `merge` Merge a pull request
    - `--delete-branch=false'` or `-d=false` retain the remote and local head branch after merge
    - `-m` or `--merge` Merge the commits with the base branch
    - `-r` or `--rebase` Rebase the commits onto the base branch
    - `-s` or `--squash` Squash the commits into one commit and merge it into the base branch
  - `diff` View changes in a pull request
