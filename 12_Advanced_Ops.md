### reset
 - hard
 - mixed (default)
 - soft

```bash
git reset <commit_hash>
```

##### Soft
 - discard commit
 - keep changes in staging
 - keep changes in working
 
##### Mixed
 - discard commit
 - discard changes in staging
 - keep changes in working

##### Hard
 - discard commit
 - discard changes in staging
 - discard changes in working
 
### revert
Reverts specific commit
 - is not destructive
 - does not modify git history
 - takes the commit, inverse all changes, create new commit after it

### amend
Adjusts information in the last commit
 - makes new commit, last commit is gc
 
```bash
git commit --ammend -m "New msg for last commit"
```

### cherry-pick
Takes any commit and inserts it into currently checked out branch as the last commit

Makes changes in new branch
```bash
git checkout -b test-6
# changes files in playground, adds, commits - 4c53e51

git checkout master
git cherry-pick 4c53e51
```

Can skip committing on local branch
```bash
git cherry-pick --no-commit <commit_hash> 
```

### stash
Allows to save changes without committing
```bash
git stash
```

### Rebase with Squash

