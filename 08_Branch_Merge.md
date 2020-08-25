Two different merges
 - fast forward
 - 3 way

Receiving branch - branch that will receive the merge
 
### Fast Forward Merge
 - Possible only when there are no further commits in the receiving branch after the commit where the feature branch was created
 - Simply moves pointer to the last commit in feature branch
 
There are no other commits in master after branching feature branch
<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/FAST-FORWARD-1.PNG">

Moves master pointer from last commit of master to last commit of merging feature branch
<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/FAST-FORWARD-2.PNG">

Feature branch commits are part of master branch
<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/FAST-FORWARD-3.PNG">

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

<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/3-WAY-1.PNG">
New commit is made
<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/3-WAY-2.PNG">

#### 3 Way in action
Create new branch

<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/3-WAY-3.PNG">

Create file in it
```bash
git checkout -b test-2                              # creates test-2 branch
touch playground/test-6-added-in-test-2-branch.txt

git add .
git commit -m "Added test file in test-2 branch"
```

Create file in master after creating one in test-2
```bash
git checkout master
touch touch playground/test-7-added-in-master-branch-after-adding-a-new-file-in-test-2-branch.txt      # eee Macarena

git add .
git commit -m "Added a test file in master after adding a test file in test-2"
```

Merging the two branches
```bash
git checkout master
git merge test-2

Merge made by the 'recursive' strategy.
 playground/test-6-added-in-test-2-branch.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 playground/test-6-added-in-test-2-branch.txt
```

cat the merge commit, 2 parents
```bash
cat .git/refs/heads/master
eff09fe984c128eb649d4ecddd61e23b7909e490

git cat-file -p eff09fe
tree 72d193692ef35a4575f13fef2e1fc831c51e5644
parent 586ab6dc5a9834bd916eea76793b615c62723940
parent 87cf089adbfc55b40faef9077314f89fb4cf1b7e
author i-den <24753710+i-den@users.noreply.github.com> 1598208273 +0300
committer i-den <24753710+i-den@users.noreply.github.com> 1598208273 +0300
```

the parents can be observed with git log
```bash
git log --oneline

eff09fe Merge branch 'test-2'
586ab6d Deleted file that will cause potential conflict as well
87cf089 (test-2) Deleted file that would cause potential conflict
...
```

### Merge Conflict
Creating a conflict with a test-3 branch

```bash
echo "Line added in master branch" > playground/conflicting-file.txt

git add .
git commit -m "Added line in conflicting file while in master branch"

git checkout -b test-3
echo "Line added in test-3 branch" > playground/conflicting-file.txt

git add .
git commit -m "Added line in conflicting file while in test-3 branch"
```

Merge Conflict
```bash
git merge test-3
Auto-merging playground/conflicting-file.txt
CONFLICT (content): Merge conflict in playground/conflicting-file.txt
Automatic merge failed; fix conflicts and then commit the result.
```

Conflicting file
```bash
git status
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   playground/conflicting-file.txt


cat playground/conflicting-file.txt
<<<<<<< HEAD
Line added in master branch
=======
Line added in test-3 branch.
>>>>>>> test-3
```

Staging Area files
```bash
git ls-files
...
100644 d2fee18dc4e677f5bec9f1c5baf76fe7300882f6 1       playground/conflicting-file.txt
100644 978af8379d8ece09018559b8218593762f75826c 2       playground/conflicting-file.txt
100644 85c08549366705690d9a7de4a3eac5965a125af6 3       playground/conflicting-file.txt

# first - common to both branches, file during branching
# second - changed in master branch
# third - changed in test-3 branch
```

#### Resolving conflict
Changing file
```bash
# OLD:
<<<<<<< HEAD
Line added in master branch
=======
Line added in test-3 branch.
>>>>>>> test-3

# NEW:
Line added in master branch
```

```bash
git status

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   playground/conflicting-file.txt
```

Committing resolved conflict
```bash
git add playground/conflicting-file.txt
git commit -m "Resolved conflict"


git ls-files               # file has only 1 version now
100644 978af8379d8ece09018559b8218593762f75826c 0       playground/conflicting-file.txt



git commit -m "Resolved conflict"
[master 89b9caa] Resolved conflict
```