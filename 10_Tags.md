Tags
 - text pointers to specific commits

Types
 - lightweight
   - ```git tag v1.0.0```
   - .git/refs/tags
 - annotated
   - ```git tag -a v1.0.0 -m "New Tag"```
   - .git/refs/tags
   - .git/objects
   - stores tag message
   - stores tag author and date (as with every commit)
   
#### Lightweight Tags
Creating a lightweight tag
```bash
git tag v0.0.1

git tag # listing all tags
v0.0.1
```

Showing the tag
```bash
git show v0.0.1
# same as
git show <commit_hash of the tag>
```

Tag in filesystem
```bash
ls .git/refs/tags/
v0.0.1

cat .git/refs/tags/v0.0.1
329dbb7820dad89d81159ea1a8aa6666291a089d
```

Lightweight does not contain information
```bash
git tag -v v0.0.1
error: v0.0.1: cannot verify a non-tag object of type commit.
```

#### Annotated Tag
Creating an Annotated Tag
```bash
git tag -a v0.0.3 -m "First Tag"
```
```bash
git tag -v v0.0.3
object e38ccbab214e2442e44498bcf3b8ca06b4a46e46
type commit
tag v0.0.3
tagger i-den <24753710+i-den@users.noreply.github.com> 1598295585 +0300

First Tag
error: no signature found
```

Tag in filesystem
```bash
ls .git/refs/tags/
v0.0.3

cat .git/refs/tags/v0.0.3                  # hash of the new annotated tag Git object
ff0b301716d47c2fcc07ec36687de19f74c19f91   # different from the object in the previous command
```

Showing the tag object
```bash
git cat-file -t ff0b301716d47c2fcc07ec36687de19f74c19f91
tag

git cat-file -p ff0b301716d47c2fcc07ec36687de19f74c19f91      # same output as git tag -v v0.0.3 read directly from the Git object
object e38ccbab214e2442e44498bcf3b8ca06b4a46e46
type commit
tag v0.0.3
tagger i-den <24753710+i-den@users.noreply.github.com> 1598295585 +0300

First Tag
```

#### Pushing tags
Push all tags
```bash
git push -v --tags
Pushing to https://github.com/i-den/git.git
Counting objects: 1, done.
Writing objects: 100% (1/1), 174 bytes | 174.00 KiB/s, done.
Total 1 (delta 0), reused 0 (delta 0)
POST git-receive-pack (428 bytes)
To https://github.com/i-den/git.git
 * [new tag]         v0.0.1 -> v0.0.1
 * [new tag]         v0.0.3 -> v0.0.3
```

Push specific tag
 - pushes only the tag, not commits after it
```bash
git push origin <tag_name>
```

#### Deleting tags
Local
```bash
git tag
v0.0.1
v0.0.3
v0.0.4

git tag -d v0.0.1
Deleted tag 'v0.0.1' (was 329dbb7)
```

Remote
```bash
git push -d origin v0.0.1
To https://github.com/i-den/git.git
 - [deleted]         v0.0.1
```