<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/PUSH_PULL_FETCH.PNG">

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
cbf306d (HEAD -> master) Adjusted Push Pull Fetch
02e44ee Added Push Pull Fetch, picture for it
04b0749 (origin/master) Added Merge Conflict info to Branch Merge

git branch -vv             # local repo
* master cbf306d [origin/master: ahead 2] Adjusted Push Pull Fetch
  test-2 87cf089 [origin/test-2] Deleted file that would cause potential conflict

git branch -r -v           # remote repo
  origin/master 04b0749 Added Merge Conflict info to Branch Merge
```
#### git remote show origin
 - shows all info for local and remote branches
```bash
git remote show origin
* remote origin
  Fetch URL: https://github.com/i-den/git.git
  Push  URL: https://github.com/i-den/git.git
  HEAD branch: master
  Remote branches:
    master tracked
    test-2 tracked
  Local branches configured for 'git pull':
    master merges with remote master
    test-2 merges with remote test-2
  Local refs configured for 'git push':
    master pushes to master (fast-forwardable)
    test-2 pushes to test-2 (up to date)
``` 

### Fetch
Creating repo in Github named git-added-branch
```bash
git branch -r
  origin/master
  origin/test-2
```
The newly created branch in remote repo is not listed.

Fetching remote changes
```bash
git fetch                                   # fetch changes
From https://github.com/i-den/git
 * [new branch]      git-added-branch -> origin/git-added-branch


git branch -vv                              # still not listed
* master cbf306d [origin/master: ahead 2] Adjusted Push Pull Fetch
  test-2 87cf089 [origin/test-2] Deleted file that would cause potential conflict


git branch -r                               # listed in remote branches
  origin/git-added-branch
  origin/master
  origin/test-2

git checkout git-added-branch
Branch 'git-added-branch' set up to track remote branch 'git-added-branch' from 'origin'.
Switched to a new branch 'git-added-branch'

* git-added-branch 04b0749 [origin/git-added-branch] Added Merge Conflict info to Branch Merge
  master           a951613 [origin/master: ahead 3] Added info to Push Pull Fetch
  test-2           87cf089 [origin/test-2] Deleted file that would cause potential conflict
```

Branch gid-added-branch deleted at Github

ow to know that remote branch is deleted
```bash
git remote show origin
* remote origin
  Fetch URL: https://github.com/i-den/git.git
  Push  URL: https://github.com/i-den/git.git
  HEAD branch: master
  Remote branches:
    master                               tracked
    refs/remotes/origin/git-added-branch stale (use 'git remote prune' to remove)     # shown as prune
    test-2                               tracked
  Local branches configured for 'git pull':
    git-added-branch merges with remote git-added-branch
    master           merges with remote master
    test-2           merges with remote test-2
  Local refs configured for 'git push':
    master pushes to master (fast-forwardable)
    test-2 pushes to test-2 (up to date)


git remote prune origin
Pruning origin
URL: https://github.com/i-den/git.git
 * [pruned] origin/git-added-branch

  git-added-branch 04b0749 [origin/git-added-branch: gone] Added Merge Conflict info to Branch Merge      # gone
* master           a951613 [origin/master: ahead 3] Added info to Push Pull Fetch
  test-2           87cf089 [origin/test-2] Deleted file that would cause potential conflict
```

### Pull
Pull merges remote branch into current branch
 - first fetches
 - then merges FETCH_HEAD

<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/PULL-1.PNG">

Process
 - checkout local branch to be pulled
 - check tracking branch with git branch -vv
 - git pull
 - will fetch all changes from remote repo / git fetch used
 - will update FETCH_HEAD that has hashes of last commits in remote repo
 - will merge remote branch into current branch / git merge FETCH_HEAD

<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/PULL-2.PNG">


Create file in test-2 branch via Github, then pulling
```bash
git pull -v
From https://github.com/i-den/git
 = [up to date]      test-2     -> origin/test-2
 = [up to date]      master     -> origin/master
Updating 87cf089..24c33fc
Fast-forward
 playground/test-file-added-via-github | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 playground/test-file-added-via-github
```

#### show ref
```bash
git show-ref

95477e93e3a05f2554dadf03edaeb3917157ac2b refs/heads/master
24c33fc5981fa7d6c7ed3dd2b4958de7a11f210c refs/heads/test-2
9bfcc52b57579d3514637528472dc2c22bbc5860 refs/heads/test-3
04b0749808ab7c7685ec42d08e4e1189c059a88c refs/remotes/origin/master
24c33fc5981fa7d6c7ed3dd2b4958de7a11f210c refs/remotes/origin/test-2
9bfcc52b57579d3514637528472dc2c22bbc5860 refs/remotes/origin/test-3

.git/refs/heads
.git/refs/remotes/origin
```