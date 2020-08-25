> pictures/REBASE-VS-MERGE.png
>
> pictures/REBASE-1.png

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

> pictures/REBASE-2.png

Rebasing
```bash
git rebase master
First, rewinding head to replay your work on top of it...
Applying: Added test-5 file
```


