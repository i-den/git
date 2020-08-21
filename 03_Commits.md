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


