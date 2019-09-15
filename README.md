# Contributing to Open Source: Tips & Tricks 

## Contents
- [Introduction](#Introduction)
- [Git](#Git)
- [Git FAQ](#Git-FAQ)
- [Writing READMEs](#Writing-READMEs)
- [Writing CONTRIBUTEs](#Writing-CONTRIBUTEs)
- [Choosing a License](#Choosing-a-license)
- [Contributing](#Contributing)
- [License](#License)

## Introduction
As I learn my way up to being a proficient contributor to open source, I have kept some of these cheatsheets/resources around to refer in times of need. This list cover mostly the basics and would suffice foundational day-to-day work. I hope you find it useful. Feel free to contribute via issues or pull requests. :heart_eyes:

## Git
### Setup
```
git config --global user.name "<name>"
```

```
git config --global user.email "<email address>"
```

### Init
###### Create a new directory, and initialize it with git-specific functions
```
git init <repository-name>
# git init my-repo
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
```

###### Stage files
```
git add <filename>
# git add README.md
# git add .          # . indicates all files (except the ones specified in .gitignore)
# git add *          # * indicates a wildcard
# git add *.html
# git add *.txt 
```

###### Take a snapshot of the staging area
```
git commit -m <message>
# git commit -m "added a button"
```

###### Provide the path for the repository you created on github
```
git remote add <remote-name> <github-link>
# git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```

###### After commit, push to remote repo aka origin, and commit to master
```
git push <remote-name> <remote-branch-name>
# git push origin master
```

### Branch

###### Create new local branch
```
git branch <local-branch-name>          # create a local branch
git checkout -b <local-branch-name>     # create a local branch and checkout to that branch
```

###### Create new local branch from remote branch
```
git branch <local-branch-name> <remote-name>/<remote-branch-name>
git checkout -b <local-branch-name> <remote-name>/<remote-branch-name>    # this allows you to set local-branch-name on your own
git checkout --track <remote-name>/<remote-branch-name>                   # this sets the local-branch-name as remote-branch-name
```

###### Go to branch
```
git checkout <local-branch-name>
# git checkout master          # go to master branch
```

###### Merge branches to source branch (must be on source branch)
```
git merge <branch-name>
```

###### Use -a to skip staging step while commit, but untracked files must use 'git add'
```
git commit -a -m 'message'
```

###### Stash unstaged stuff somewhere and come back later
```
git stash
```

###### Apply stashed items
```
git stash apply 
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
git branch (view local branch name only)
git branch -v (shows latest commit)
git branch -vv (shows upstream branch)
```

###### Delete remote branch
```
git push [remote-name] :[remote-branch-name]
git push [remote-name] --delete [remote-branch-name]
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

### Remote

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

###### Fetch and merge the changes from the remote branch into current branch
```
git pull <remote-name>
```

###### Add remote repository
```
git remote add <remote-name> <github-link>
git remote add myRepo http://github.com/somerepo.git
```

###### Show remote links
```
git remote -v
```

###### Stop tracking a file that is currently tracked
[1]:#Stop-tracking-a-file-that-is-currently-tracked
```
git rm --cached <filename>
git rm -r --cached <folder>    # if you want to remove a whole folder, you need to remove all files in it recursively
```

###### Clear local pointers to non-existing remote branches
```
git remote prune <remote-name>
```

## Git FAQ
- [How to make Git “forget” about a file that was tracked but is now in .gitignore?][1]

## Writing READMEs
- List of well written READMEs [[see]](https://github.com/matiassingers/awesome-readme)
- GitHub Emojis [[see]](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md)
- Template to make a good README [[see]](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2)
- Badges [[see]](https://shields.io/)
- Octodex [[see]](https://octodex.github.com/)
- LaTeX mathematical symbol embedding [[see]](https://www.codecogs.com/latex/eqneditor.php)

## Writing CONTRIBUTEs

## Choosing a License
- Explain a license in plain english [[see]](https://tldrlegal.com/)
- Full guide to choosing a license [[see]](https://choosealicense.com/)
- Further license references for open source [[see]](https://opensource.org/licenses)
- Questions to ask yourself:
  1. What licenses are already in my software?
  2. What are the terms of service where my software is hosted?
  3. Do I want derivatives, additions and distributions to use the same licenses?
  4. Can others use my software in their own proprietary software?

## Documenting Issues
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






