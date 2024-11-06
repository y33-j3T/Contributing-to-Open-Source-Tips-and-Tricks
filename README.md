# Contributing to Open Source: Tips & Tricks 
## Contents
- [Introduction](#Introduction)
- [Content](#man_technologist-Git)
  - [Git](#man_technologist-Git)
  - [Git FAQ](#question-Git-FAQ)
  - [Writing READMEs](#page_with_curl-Writing-READMEs)
  - [Writing CONTRIBUTEs](#love_letter-Writing-CONTRIBUTEs)
  - [Choosing a License](#detective-Choosing-a-license)
  - [Documenting Issues](#bookmark_tabs-Documenting-Issues)
- [Contributing](#Contributing)
- [License](#License)


## Introduction
As I learn my way up to being a proficient contributor to open source, I have kept some of these cheatsheets/resources around to refer in times of need. This list cover mostly the basics and would suffice foundational day-to-day work. I hope you find it useful. Feel free to contribute via issues or pull requests. :heart_eyes:


## :man_technologist: Git

### Setup
<details>
<summary>Details</summary>

###### List git configurations
```git
git config --list  # see configurations from system, global, local
```
###### Set git configurations
```
git config --<level> <setting> <value>
git config --global user.name "<name>"            # set transactions' name
git config --global user.email "<email-address>"  # set transactions' email
git config --global http.proxy <proxy-address>    # set proxy to connect w/ remotes
```
###### Create a new directory, and initialize it with git-specific functions
```
git init <repository-name>
```
###### Clone a project and its entire version history
```
git clone <url>                                       # from remote
git clone <existing-project-path> <new-project-path>  # locally
```
###### Change into directory of specified repository
```
cd <repository-name>
# cd my-repo
```
###### Create files in the project directory
```
touch <filename>
# touch README.md
# touch .gitignore 
```
###### Specify files to ignore / avoid being tracked by git in .gitignore text file
```
<filename>
# app.py
# reference.txt
# *.log          # * indicates a wildcard
# *.txt
# build/
```
###### Write contents into text files
```
echo <filename-to-write>><filename>
# echo *.log > .gitignore          # rewrite the file
# echo *.log >> .gitignore         # append to the file
```
###### List all ignored files in this project
```
git ls-files --other --ignored --exclude-standard
```

</details>

### Stage
<details>
<summary>Details</summary>

###### Stage files
```
git add <filename>
# git add README.md
# git add .          # . indicates all files (except the ones specified in .gitignore)
# git add *          # * indicates a wildcard
# git add *.html
# git add *.txt 
```
###### Delete unstaged files
```
git clean -n  # see untracked files
git clean -f  # delete untracked files
```
###### Unstage changes, but preserve contents
```
git reset <filename>        # to file
git reset HEAD              # to all files
git reset                   # to HEAD by default
```
###### Delete unstaged changes
```
git checkout -- <filename>  # to file
```

</details>
  

### Commit
<details>
<summary>Details</summary>

###### Take a snapshot of the staging area
```
git commit -m "<descriptive-message>"
git commit --amend -m "<new-message>"  # ammend commit message
```
###### Show changes
```
git annotate <filename>                     # of file since first commit
git diff <commit-hash-1>..<commit-hash-2>   # of file between 2 commits
git diff HEAD~<num-1>..HEAD~<num-2>
```
###### Restore previous version
```
git checkout <commit-hash> <filename>  # of file
```
###### Undo all commits after particular commit, preserving changes locally
```
git reset <commit-hash>
```
###### Revert commit
```
git revert <commit-hash>
git checkout <current-branch>  # to fix detached head
```
###### Discard all history and changes back to the specified commit
```
git reset --hard <commit-hash>
```

</details>


### Check repository status
<details>
<summary>Details</summary>
  
###### Lists all new or modified files to be committed
```
git status
```
###### Show file differences not yet staged
```
git diff              # for all files
git diff <filename>   # for particular file
git diff --staged
```
###### Show differences between staged and the last file version
```
git diff -r HEAD             # for all files
git diff -r HEAD <filename>  # for particular file
```
###### Show changes in particular commit
```
git show <commit-hash>                    
git show HEAD~<num-commit-before-current>
```
</details>


### Branch
<details>
<summary>Details</summary>
  
###### List all local branches in the current repository
```
git branch
```
###### Create new local branch
```
git branch <local-branch-name>         
git checkout -b <local-branch-name>                                     # then go to that branch
git branch <local-branch-name> <remote-name>/<remote-branch-name>       # from remote branch
git checkout -b <local-branch-name> <remote-name>/<remote-branch-name>  # this allows you to set local-branch-name on your own
git checkout --track <remote-name>/<remote-branch-name>                 # this sets the local-branch-name as remote-branch-name
```
###### Go to branch
```
git checkout <local-branch-name>
```
###### Show difference between branches
```
git diff <branch-1>..<branch-2>
```
###### Merge particular branch 
```
git merge <branch-name>                      # to current branch
# git merge <branch-name> <another-branch>   # to particular branch
```
###### Use -a to skip staging step while commit, but untracked files must use 'git add'
```
git commit -a -m 'message'
```
###### List all remote branches
```
git branch -r
```
###### Create new remote branch / update remote branch from local branch
```
git push <remote-name> <local-branch-name>:<remote-branch-name>
```
###### Set branch upstream (ie. set the remote branch where the local branch push/pull directly)
```
git branch -u <remote-name>/<remote-branch-name>
git branch --set-upstream-to <remote-name>/<remote-branch-name>
```
###### See branch (increasing verbosity)
```
git branch      # view local branch name only
git branch -v   # shows latest commit
git branch -vv  # shows upstream branch
```
###### Delete remote branch
```
git push <remote-name> :<remote-branch-name>
git push <remote-name> --delete <remote-branch-name>
```
###### Delete local branch
```
git branch -d [local-branch-name]
```
###### Make a branch to be master 
```
git checkout better_branch
git merge --strategy=ours master    # keep the content of this branch, but record a merge
git checkout master
git merge better_branch             # fast-forward master up to the merge
```
###### Rename branch 
```
git checkout <old_name>                # go to branch to rename
git branch -m <new_name>               # rename the branch
git push origin --delete <old_name>    # delete the <old_name> remote branch
git push origin -u <new_name>          # push the <new_name> local branch & reset the upstream branch
```

</details>


### Remote
<details>
<summary>Details</summary>

###### After commit, push to remote repo aka origin, and commit to master
```
git push <remote-name> <remote-branch-name>
# git push origin master
```
###### Provide the path for the repository you created on github
```
git remote add <remote-name> <github-link>
# git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```
###### List remote files
```
git remote
```
###### Clone remote repository
```
git clone <clone-url>
```
###### Go out to any server and get any latest changes
```
git fetch <remote-name>
git fetch --all
```
###### Fetch and merge the changes from the remote branch
```
git pull <remote-name>               # into current branch
git pull <remote-name> <local-name>  # into particular branch
```
###### Add a remote
```
git remote add <remote-name> <github-link>
# git remote add myRepo http://github.com/somerepo.git
```
###### Remove a remote
```
git remote rm <remote-name>
```
###### Set up a branch to track a remote branch
```
git chekcout <branch-name>
git branch -u <remote-name>/<branch-name>
```
###### Show remote URLs
```
git remote -v
```
###### Set remote URLs
```
git remote set-url <remote-name> <url>
```
###### Clear local pointers to non-existing remote branches
```
git remote prune <remote-name>
```
###### Add & push to multiple remotes
```
git remote add <remote-name> <primary-repo-url>
git remote set-url --add --push <remote-name> <primary-repo-url>          # Re-register remote as a push URL
git remote set-url --add --push <remote-name> <secondary-repo-url>        # Add another push URL to this remote
```
###### Fetch from multiple remotes (not git pull, since you cannot merge many remotes into one)
```
git fetch --all                                       # fetch from multiple remotes
git checkout <branch-name>                            # checkout to the branch you want to work with
git reset --hard <remote-name>/<branch-name>          # switch remotes to access the work done on each one & further work
```

</details>


### Stash changes
<details>
<summary>Details</summary>
  
###### Stash unstaged stuff somewhere and come back later
```
git stash
```
###### List all stashed changesets
```
git stash list
```
###### Apply stashed items
```
git stash apply 
```
###### Restore the most recently stashed files
```
git stash pop
```
###### Discard the most recently stashed changeset
```
git stash drop
```

</details>


### Refactor file tracking
<details>
<summary>Details</summary>
  
###### Delete file from working directory and stage deletion
```
git rm <filename>
```
###### Stop tracking a file that is currently tracked
```
git rm --cached <filename>
git rm -r --cached <folder>    # if you want to remove a whole folder, you need to remove all files in it recursively
```
###### Change the file name and prepare it for commit
```
git mv <filename-original> <file-renamed>
```

</details>


### Review history
Browse and inspect the evolution of project files
<details>
<summary>Details</summary>
  
###### List version history for the current branch
```
git log
git log --oneline                 # simplified output
git log -<num-output> <filename>  # limit number of output
```
###### List version history for a file, including renames
```
git log --follow <file>
```
###### Show content differences between two branches
```
git diff <first-branch>...<second-branch>
```
###### Output metadata and content changes of the specified commit
```
git show <commit-hash>
```
###### Test / work with previous commit 
```
git checkout <commit-hash>
```

</details>


## :question: Git FAQ
- How to make Git “forget” about a file that was tracked but is now in .gitignore? [Stop tracking a file that is currently tracked](#stop-tracking-a-file-that-is-currently-tracked)
- Git LFS: Encountered X file(s) that should have been pointers, but weren't. ([reference](https://www.reddit.com/r/Unity3D/comments/o4jh6d/git_lfs_encountered_x_files_that_should_have_been/))


## :page_with_curl: Writing READMEs
- List of well written READMEs [[see]](https://github.com/matiassingers/awesome-readme)
- GitHub Emojis [[see]](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md)
- Template to make a good README [[see]](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2)
- Badges [[see]](https://shields.io/)
- Octodex [[see]](https://octodex.github.com/)
- LaTeX mathematical symbol embedding [[see]](https://www.codecogs.com/latex/eqneditor.php)


## :love_letter: Writing CONTRIBUTEs
-


## :detective: Choosing a License
- Explain a license in plain english [[see]](https://tldrlegal.com/)
- Full guide to choosing a license [[see]](https://choosealicense.com/)
- Further license references for open source [[see]](https://opensource.org/licenses)
- Questions to ask yourself:
  1. What licenses are already in my software?
  2. What are the terms of service where my software is hosted?
  3. Do I want derivatives, additions and distributions to use the same licenses?
  4. Can others use my software in their own proprietary software?


## :bookmark_tabs: Documenting Issues
- Initiator (who logged the call)
- Initiator Extension or Phone 
- Date/Time Opened
- Summary Description
- Impact/Importance
- Type (of fault)
- Owner (of system)
- Current Status (open, in process, closed)
- Next Step
- Next Step Date
- Completion Date
- Resolution, development request # or link to vendor support request


## Contributing
- Please refer to [CONTRIBUTE.md](./CONTRIBUTE.md) for details. :heart_eyes:


## License 
Contributing to Open Source: Tips & Tricks is released under the [MIT license](./LICENSE).
