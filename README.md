# Contributing to Open Source: Tips & Tricks (work in progress)

## License
1. What licenses are already in my software?
2. What are the terms of service where my software is hosted?
3. Do I want derivatives, additions and distributions to use the same licenses?
4. Can others use my software in their own proprietary software?

## Git
// create a new directory, and initialize it with git-specific functions
```
git init <repository-name>
git init my-repo
```
  
// change into the `my-repo` directory
```
cd my-repo
```

// create files in the project directory
```
touch README.md
touch .gitignore 
```

// type file types to ignore in gitignore file eg
```
*.log
*.txt
```

// stage files
```
git add README.md
git add *
git add *.html
git add *.txt 
```

// take a snapshot of the staging area
```
git commit -m 'message'
```

// provide the path for the repository you created on github
```
git remote add <remote-name> <github-link>
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```

// after commit, push to remote repo aka origin, and commit to master
```
git push <remote-name> <remote-branch-name>
git push origin master
```

### branching 

// create new local branch
```
git branch <local-branch-name>
```

// create new local branch from remote branch
```
git branch <local-branch-name> <remote-name>/<remote-branch-name>
git checkout -b <local-branch-name> <remote-name>/<remote-branch-name> (this allows you to set local-branch-name on your own)
git checkout --track <remote-name>/<remote-branch-name> (this sets the local-branch-name as remote-branch-name)
```

// go to branch (if main branch, local-branch-name=master)
```
git checkout <local-branch-name>
```

// merge branches to source branch (must be on source branch)
```
git merge <branch-name>
```

// use -a to skip staging step while commit, but untracked files must use 'git add'
```
git commit -a -m 'message'
```

// stash unstaged stuff somewhere and come back later
```
git stash
```

// apply stashed items
```
git stash apply 
```

// list all remote branches
```
git branch -r
```

// create new remote branch / update remote branch from local branch
```
git push <remote-name> <local-branch-name>:<remote-branch-name>
```

// set branch upstream (ie. set the remote branch where the local branch push/pull directly)
```
git branch -u <remote-name>/<remote-branch-name>
git branch --set-upstream-to <remote-name>/<remote-branch-name>
```

// see branch (increasing verbosity)
```
git branch (view local branch name only)
git branch -v (shows latest commit)
git branch -vv (shows upstream branch)
```

// delete remote branch
```
git push <remote-name> :<remote-branch-name>
git push <remote-name> --delete <remote-branch-name>
```

// make a branch to be master 
```
git checkout better_branch
git merge --strategy=ours master    # keep the content of this branch, but record a merge
git checkout master
git merge better_branch             # fast-forward master up to the merge
```

### remote 

// list remote files
```
git remote
```

// clone remote repository
```
git clone <clone-url>
```

// go out to any server and get any latest changes
```
git fetch <remote-name>
git fetch --all
```

// fetch and merge the changes from the remote branch into current branch
```
git pull <remote-name>
```

// add remote repository
```
git remote add <remote-name> <github-link>
git remote add myRepo http://github.com/somerepo.git
```

// show remote links
```
git remote -v
```

// stop tracking a file that is currently tracked
```
git rm --cached <filename>
git rm -r --cached <folder> (If you want to remove a whole folder, you need to remove all files in it recursively.)
# How to make Git “forget” about a file that was tracked but is now in .gitignore?
```

// clear local pointers to non-existing remote branches
```
git remote prune <remote-name>
```

## Issue 
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








