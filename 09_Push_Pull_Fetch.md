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
 
 