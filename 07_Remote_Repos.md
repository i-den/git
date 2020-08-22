Remote Repos are optimized
 - keeps Objects packed in .git/objects/pack
 
#### Unpacking Remote Repo Objects
```bash
cd .git/objects/pack

cat pack-{hash} | git unpack-objects
```

#### git diff

```bash
git diff

diff --git a/01_Objects.md b/01_Objects.md                                                    # a/ previous version    b/ current version
index 8efa0f9..c80d50b 100644                                                                 # sha1 hashes for the above files
--- a/01_Objects.md
+++ b/01_Objects.md
@@ -46,3 +46,5 @@ Object Types:                                                               # old file lines 46, 46+3. new file line 46, 46+5
   - snapshot of the hierarchy (tree) and the contents of the files (blobs)
 - Annotated Tag
   - a text pointer to a specific commit
+  ^M
+Hashed in sha1 hash. Directory is hexadecimal, thus 16*16 folders max in .git/objects/^M
diff --git a/07_Remote_Repos.md b/07_Remote_Repos.md
index 4c5d3f0..57f890b 100644
--- a/07_Remote_Repos.md
+++ b/07_Remote_Repos.md
@@ -1,43 +1,15 @@
-#### List All Branches
-```bash
-git branch
-* master
-```
-
-#### Create Branch
-```bash
-git branch name
-git checkout -b {branch-name}     # creates and checkouts in the new branch
-```
-
-```bash
-git checkout temp
```