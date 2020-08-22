Two different merges
 - fast forward
 - 3 way

Receiving branch - branch that will receive the merge
 
#### Fast Forward Merge
 - Possible only when there are no further commits in the receiving branch after the commit where the feature branch was created
 - Simply moves pointer to the last commit in feature branch
 
There are no other commits in master after branching feature branch
> pictures/FAST-FORWARD-1

Moves master pointer from last commit of master to last commit of merging feature branch
> pictures/FAST-FORWARD-2

Feature branch commits are part of master branch
> pictures/FAST-FORWARD-3
