The Branch is a text reference to the commit
 - Branches are located in .git/refs/heads
 - Current branch tracks new commits
 - branch pointer moves automatically after every new commit
 - .git/refs/heads/master - last commit on the master branch
```bash
git log --oneline
aac42f5 (HEAD -> master) Added info to Commits
2b1d339 Adjusted the Commits README
86bfae0 Initialized repo. Added Objects, Low Level Commands and Commits README file

cat .git/refs/heads/master
aac42f51eb385cfe03a5fca7a34d6f7ec47f80d6
```
```bash
                                                                                                                HEAD
                                                                                                                 |
                                                                                                                 |
                                                                                                               master
                                                                                                                 |
                                                                                                                 |
     Commit                                             Commit                                                 Commit
Initialized Repo    <--- Parent 86bfae0 -<<   Adjusted the Commits README  <------- Parent 2b1d339 --<<  Added info to Commits
    86bfae0                                             2b1d339                                                aac42f5
       |                                                   |                                                      |
       |                                                   |                                                      |
     Tree                                                Tree                                                   Tree
   86bfae0                                              0624ee                                                 d4a62f
 01_Objects.md                                       01_Objects.md
 02_Low_Level_Commands.md                            02_Low_Level_Commands.md
 03_Commits.md                                       03_Commits.md
```

HEAD
- reference to the currently checked-out branch or commit
- Pointer is located in .git/HEAD file
- locally significant
- Change ref to specific branch
  - git checkout {branch name}
- Change ref to specific commit
  - git checkout {commit hash}

```bash
cat .git/HEAD
ref: refs/heads/master
```

HEAD to master branch
> pictures/HEAD-1

HEAD to commit
> pictures/HEAD-2


