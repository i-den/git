> pictures/PUSH_PULL_FETCH.PNG

#### Origin
 - the remote repository
```bash
git remote       # lists remote servers for the local repo
origin

git remote -v
origin  https://github.com/i-den/git.git (fetch)
origin  https://github.com/i-den/git.git (push)
```

Listing all branches
```bash
git branches -a         # All branches
* master
  test-2
  remotes/origin/master

git branch -r           # Remote branches
  origin/master
```

Tracking branch
 - a local branch that's connected to a remote branch, tracking commit diff between the two
 - when connecting to a remote repo git creates only 1 tracking branch
 - checking out a remote branch makes it tracking for the local, newly created one
 
```bash
git log --oneline
02e44ee (HEAD -> master) Added Push Pull Fetch, picture for it
04b0749 (origin/master) Added Merge Conflict info to Branch Merge

git branch -vv             # local repo
* master 02e44ee [origin/master: ahead 1] Added Push Pull Fetch, picture for it
  test-2 87cf089 Deleted file that would cause potential conflict

git branch -r -v           # remote repo
  origin/master 04b0749 Added Merge Conflict info to Branch Merge
``` 
