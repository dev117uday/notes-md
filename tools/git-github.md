---
description: Git it
---

# Git version Control

## Basic and Git Configuration

* version : `git --version`
* git directory \[ Linux \] : `which git` 

### Setting your user name and email :

* You need to set who you are _before_ creating any commit. That will allow commits to have the right author name and email associated to them.
```s
$ git config --global user.name "Your Name"
$ git config --global user.email mail@example.com
```

* Remove a global identity :
```s
$ git config --global --remove-section user.name
$ git config --global --remove-section user.email
```

### Basic Commands

* Create an empty Git repository: `git init`
  * This creates a hidden folder, .git , which contains the plumbing needed for Git to work.
* Check status : `git status`
* Adding files to staging area : 
  * `git add <directory/filename>` \[for single file\]
  * `git add .`  or `git add --all` \[for all changed files\]
* Commit all files : 
  * `git commit` \[this opens your Git's default code editor\]
* To commit files with short message : 
  * `git commit -m "commit msg"`
* To add the remote location of git : 
  * `git remote add origin https://<your-git-service-address>/owner/repository.git`
* Cloning a Repo : 
  * `git clone https://github.com/username/projectname.git`
* To specify a different name of the directory, example `MyFolder` :
  * `git clone https://github.com/username/projectname.git MyFolder`
* To clone in current directory : 
  * `git clone https://github.com/username/projectname.git .`
* To push your code to upstream :
  * `git push --set-upstream origin main` or `git push origin`
* Check the remote names: 
  * `git remote -v`
* To get help about any command : 
  * `git <command> --help`

### Logging

* To view log  :
  * `git log`
  * `git log --stat`  \[ for detailed view \]
* To view log more beautifully :
  * `git log --decorate --oneline --graph`
* Create alias commands : 
  * `git config --global alias.mylog "log --decorate --oneline --graph"`
  * To run  :  `git mylog`
* To view logs in oneline :
  * `git log --oneline`
* To see commit using commit id : `git show <commit id>`

### Working with Remote Repositories

* List remote location :
  * `git remote -v`
* If a remote branch has been deleted, your local repository has to be told to prune the reference to it
  * `git fetch [remote-name] --prune`
* Updating from Upstream Repository
```s
git fetch remote-name
git merge remote-name/branch-name
```
  * The pull command combines a fetch and a merge : `git pull`
  * `git pull --rebase remote-name branch-name`
* Syntax for pushing to a remote branch :
  * `git push <remote_name> <branch_name>`
* Rename remote :
  * `git remote rename origin destination`

## Diff & Patch

![Git cheat sheet](../.gitbook/assets/git-cheat-sheet.png)

### Differences

- To see new changes made
  - `git diff`

- To see difference between two files :
  - `diff code1.js code2.js`

- Or use **-u** to show more detailed view of diff
  - `diff -u code1.js code2.js`

- To generate differences between two file in another file
  - `diff code1.js code2.js > change.diff`

- To see staged changes
  - `git diff --staged`

### Patch

- In order to patch the changes
  - `patch code1.js < change.diff`

### Logging details about commits

- To commit all files without going through git add
  - `git commit -a -m "commit message"`

- To get more details about the project 
  - `git log -p`

- to see patch file to another commit, we use commit id
  - `git show b09ddf8a0000055f50386f1aa938f4b8a7b43b0c`

- to get stats about your commits
  - `git log --stat`

- to see details while adding
  - `git add -p`

- to see details on last n commit \(example of 2\)
  - `git log -p -2`

### File Management

- to rename file that is being tracked by git
  - `git mv old_file_name new_file_name`

- to delete a file use : 
  - `git rm file_to_be_delete`

- to revert change of a file, use : 
  - `git checkout file_name`

- to remove a file from being tracked by git, use : 
  - `git reset HEAD file_name`

- to change the commit msg/ or to overwrite last commit:
  - `git commit --amend`

- to revert HEAD :
  - `git revert HEAD`

- to see details on last n commit \(example of 2\)
  - `git log -p -2`

- To see the last two commit, becoz revert doesnt delete the faulty commit, it roles back head while keeping the fault.

To create a new branch :
  - `git branch name_of_new_branch`

