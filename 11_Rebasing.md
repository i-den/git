Rebase vs Merge
<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/REBASE-VS-MERGE.PNG">

Rebasing
<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/REBASE-1.PNG">

Create a test file in a feature branch, commit it
```bash
git checkout -b test-5
echo "Added in test-5" > playground/test-5.txt

git add playground/test-5.txt
git commit -m "Added test-5 file"
```

Create a new commit in master
```bash
git checkout master
echo "Added in master" > playground/test-5-added-in-master.txt

git add playground/test-5-added-in-master.txt
git commit -m "Added test-5 file in master"
```

<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/REBASE-2.PNG">


Rebasing
```bash
git rebase master
First, rewinding head to replay your work on top of it...
Applying: Added test-5 file
```

<img src="https://raw.githubusercontent.com/i-den/git/master/pictures/REBASE-3.PNG">


