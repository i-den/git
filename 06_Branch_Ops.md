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