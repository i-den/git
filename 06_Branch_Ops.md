#### List All Branches
```bash
git branch
* master
```

#### Create Branch
```bash
git branch name
git checkout -b {branch-name}     # creates and checkouts in the new branch
```

```bash
git checkout temp

cat .git/refs/heads/master
2659a9e98d796883a79904a96c35f6f4ad2cc5b0
cat .git/refs/heads/temp
2659a9e98d796883a79904a96c35f6f4ad2cc5b0

cat .git/HEAD
ref: refs/heads/master
git checkout temp
cat .git/HEAD
ref: refs/heads/temp
```

#### Checkout Branch
Moves HEAD to the branch
```bash
git checkout {branch-name}
```

#### Delete Branch
```bash
git branch -d {branch-name}          # deletes only merged branches
git branch -D {branch-name}          # deletes non-merged branches
```

Rename Branch
```bash
git branch -m {old-name} {new-name}
```

#### Create Remote Branch based on Local Branch
Create local branch
```bash
git checkout -b test-3
```
No remote tracking branch
```bash
git branch -vv
  master e5cf520 [origin/master: ahead 6] Added info to Push Pull Fetch
  test-2 24c33fc [origin/test-2] Create test-file-added-via-github
* test-3 e5cf520 Added info to Push Pull Fetch
```

Created test file in test-3 branch, added and committed

Remote branch still misses as it's not added in remote repo
```bash
git log --oneline
9bfcc52 (HEAD -> test-3) Added test-3 txt file

git branch -a
  master
  test-2
* test-3
  remotes/origin/master
  remotes/origin/test-2
```

Error on pushing this way
```bash
git push
fatal: The current branch test-3 has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin test-3
```

Creating remote branch
```bash
git push --set-upstream origin test-3
```
or
```bash
git push -u -v origin test-3
Pushing to https://github.com/i-den/git.git
Counting objects: 28, done.
Delta compression using up to 16 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (28/28), 589.35 KiB | 23.57 MiB/s, done.
Total 28 (delta 15), reused 0 (delta 0)
POST git-receive-pack (603647 bytes)
remote: Resolving deltas: 100% (15/15), completed with 2 local objects.
remote:
remote: Create a pull request for 'test-3' on GitHub by visiting:
remote:      https://github.com/i-den/git/pull/new/test-3
remote:
To https://github.com/i-den/git.git
 * [new branch]      test-3 -> test-3
Branch 'test-3' set up to track remote branch 'test-3' from 'origin'.
updating local tracking ref 'refs/remotes/origin/test-3'
```