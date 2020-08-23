Two different merges
 - fast forward
 - 3 way

Receiving branch - branch that will receive the merge
 
### Fast Forward Merge
 - Possible only when there are no further commits in the receiving branch after the commit where the feature branch was created
 - Simply moves pointer to the last commit in feature branch
 
There are no other commits in master after branching feature branch
> pictures/FAST-FORWARD-1

Moves master pointer from last commit of master to last commit of merging feature branch
> pictures/FAST-FORWARD-2

Feature branch commits are part of master branch
> pictures/FAST-FORWARD-3

#### Fast Forward in action
Master Branch
```bash
tree                            # master branch
└── playground
    ├── test-1.txt
    ├── test-2.txt
    └── test-5.txt                   # missing

2 directories, 17 files
```

Feature Branch
```
tree                            # feature branch
└── playground
    ├── test-1.txt
    ├── test-2.txt
    ├── test-3.txt                   # present
    ├── test-4.txt                   # present
    └── test-5.txt

2 directories, 19 files
```
merge
```bash
git checkout master
git merge test-1

Updating c9a6fde..41b2d38                    # before merge master points to c9a6fde, after merge to 41b2d38
Fast-forward
 playground/test-3.txt | 1 +
 playground/test-4.txt | 1 +
 2 files changed, 2 insertions(+)
 create mode 100644 playground/test-3.txt
 create mode 100644 playground/test-4.txt
```

Can delete feature branch afterward
```bash
git branch -d test-1
Deleted branch test-1 (was 41b2d38).
```

### 3 Way Merge
 1. Creates new commit based on 3 other commits
    - Ancestor
    - last commit in receiving branch
    - last commit in feature branch
 2. The new commit has two parents
 3. Those commits are unchanged as they're referred to

> pictures/3-WAY-1.PNG
>
> pictures/3-WAY-2.PNG

#### 3 Way in action
Creating a new branch, adding a new commit to it
```bash
git checkout -b test-2                              # creates test-2 branch
touch playground/test-6-added-in-test-2-branch.txt

git add .
git commit -m "Added test file in test-2 branch"
```

Adding a new commit to master
```bash
git checkout master
touch touch playground/test-7-added-in-master-branch-after-adding-a-new-file-in-test-2-branch.txt      # eee Macarena

```