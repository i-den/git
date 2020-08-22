### Create a Repository
```bash
# creates .git directory
git init
```
#### The .git directory
```bash
+--- branches
+--- config
+--- description
+--- HEAD
+--- hooks
|   +--- applypatch-msg.sample
|   +--- commit-msg.sample
|   +--- fsmonitor-watchman.sample
|   +--- post-update.sample
|   +--- pre-applypatch.sample
|   +--- pre-commit.sample
|   +--- pre-push.sample
|   +--- pre-rebase.sample
|   +--- pre-receive.sample
|   +--- prepare-commit-msg.sample
|   +--- update.sample
+--- info
|   +--- exclude
+--- objects
|   +--- info
|   +--- pack
+--- refs
|   +--- heads
|   +--- tags
```

#### Objects
The git filesystem stores objects in
```bash
.git/objects
```

Object Types:
- Blob (binary large object)
  - files of any type
- Tree
  - the repo's directories
- Commit
  - snapshot of the hierarchy (tree) and the contents of the files (blobs)
- Annotated Tag
  - a text pointer to a specific commit
