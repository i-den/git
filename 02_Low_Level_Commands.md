#### Low level git commands
```bash
git hash-object                   # creates git object
git cat-file                      # reads git object
git mktree                        # creates a tree object
```

#### git hash object
```bash
echo "Hello, git" | git hash-object --stdin -w
22f46444d223ec55b7677c6dd212b155fe2a7661

# folder name + file name = hash
.git/objects/22                                         # where 22 is the beginning of the hash above
.git/objects/22/f46444d223ec55b7677c6dd212b155fe2a7661  # the name of the file, substr 2
```

```bash
cat test.txt
Some text

# no new files will be created in the .git/objects
git hash-object test.txt
01b51e6ac5e39d1eb2fec3143437c6f117a58f03

# a new object file will be created
git hash-object -w test.txt
01b51e6ac5e39d1eb2fec3143437c6f117a58f03
.git/objects/01/b51e6ac5e39d1eb2fec3143437c6f117a58f03

git cat-file -p 01b51e6ac5e39d1eb2fec3143437c6f117a58f03
Some text
```

#### git cat-file
```bash
git cat-file -p <hash>   # contents of the obj
git cat-file -p 22f46444d223ec55b7677c6dd212b155fe2a7661
Hello, git

git cat-file -s <hash>   # size of the obj
git cat-file -s 22f46444d223ec55b7677c6dd212b155fe2a7661
11

git cat-file -t <hash>   # type of the obj
git cat-file -t 22f46444d223ec55b7677c6dd212b155fe2a7661
blob
```

#### Git Object
Object Type + Object Length +Content = Hash
> "Hello, git" + blob + delimiter + 11
>
> echo "blob 30\0Some text" | shasum
>
> 01b51e6ac5e39d1eb2fec3143437c6f117a58f03

#### git tree
```bash
# Two files to be used as pointers in the tree
git cat-file -p 01b51e6ac5e39d1eb2fec3143437c6f117a58f03
Some text

git cat-file -p 22f46444d223ec55b7677c6dd212b155fe2a7661
Hello, git

# The tree input
cat temp-tree.txt
100644 blob 01b51e6ac5e39d1eb2fec3143437c6f117a58f03    file1.txt
100644 blob 22f46444d223ec55b7677c6dd212b155fe2a7661    file2.txt

# Create the tree object
cat temp-tree.txt | git mktree
4db5f300da47bb5a325bcb10b691ac98167be733
.git/objects/4d/b5f300da47bb5a325bcb10b691ac98167be733         # created file

# Verify the tree object
git cat-file -p 4db5f300da47bb5a325bcb10b691ac98167be733       # can also use git cat-file -p 4db5
100644 blob 01b51e6ac5e39d1eb2fec3143437c6f117a58f03    file1.txt
100644 blob 22f46444d223ec55b7677c6dd212b155fe2a7661    file2.txt

git cat-file -t 4db5f300da47bb5a325bcb10b691ac98167be733
tree
```

#### git read-tree
Working Directory
Staging Area (Index)
Repository

```bash
git ls-files
> empty

git read-tree 4db5   # puts the two files from the Git Repository to the Staging Area (Index)

git ls-files
file1.txt
file2.txt

git ls-files -s
Permissions Hash Differs from Repo Name
100644 01b51e6ac5e39d1eb2fec3143437c6f117a58f03 0       file1.txt
100644 22f46444d223ec55b7677c6dd212b155fe2a7661 0       file2.txt
```

#### git checkout-index
Working Directory
Staging Area (Index) - files
Repository - files

To put in Working Directory
```bash
git checkout-index -a

ls
file1.txt fil2.txt
```

