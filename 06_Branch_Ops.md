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