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

