#### Commit Object
Contains the following information
 - sha1 hash
 - Author Name and Email
 - Description
 - Parent (optional)
 - Hash Pointer to a Tree object
 
#### Creating a Commit 
```bash
git commit -m "Initialized repo. Added Objects, Low Level Commands and Commits README file"
[master (root-commit) 86bfae0] Initialized repo. Added Objects, Low Level Commands and Commits README file
 4 files changed, 168 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 01_Objects.md
 create mode 100644 02_Low_Level_Commands.md
 create mode 100644 03_Commits.md
---

# Feedback
master branch
root-commit as this is the root commit and does not have parent commits

# Read the Object
git cat-file -p 86bfae0
tree 09f932a5106b5b9da2c506e6a83363ef98f1597c
author i-den <email@gmail.com> 1598029752 +0300
committer i-den <email@gmail.com> 1598029752 +0300

Initialized repo. Added Objects, Low Level Commands and Commits README file
---
git cat-file -t 86bfae0
commit
```

#### git status
Shows
 - branch
 - changes to be committed
```bash
git status
```

Tracking statuses
 - Untracked    (new files)
 - Modified
 - Staged       (added with git add)
 - Unmodified   
 
Lifecycle
```bash
Untracked                  Modified                  Staged                            Unmodified
     | >>- Stage (start tracking) git add ------------> |                               |
     |                           |                      | >>- Commit file git commit -> |
     |                           | <--- Change file in Working Dir ------------------<< |
     |                           | >>- Stage git add -> |                               |
     | <----------------------------- Untrack ---------------------------------------<< |
```

#### git add
Adds files from the Working Directory to the Staging Area (Index)
```bash
git add file1.txt file2.txt
git add .
```

#### git rm
If a file has never been committed - returns to untracked
```bash
git rm --cache filename
```

#### git log
Shows history of the commits
```bash
git log

commit 2b1d3391bfd56ddce14ad5c93db2811ac5a572b6 (HEAD -> master)
Author: i-den <email@gmail.com>
Date:   Fri Aug 21 20:20:35 2020 +0300

    Adjusted the Commits README

commit 86bfae058699e4db7a594b879aa5b2387651b5a2
Author: i-den <email@gmail.com>
Date:   Fri Aug 21 20:09:12 2020 +0300

    Initialized repo. Added Objects, Low Level Commands and Commits README file


git log --oneline
2b1d339 (HEAD -> master) Adjusted the Commits README
86bfae0 Initialized repo. Added Objects, Low Level Commands and Commits README file
```

#### git checkout
Overwrites the Working Directory to a specific branch
```bash
git checkout <commit_hash>
```

