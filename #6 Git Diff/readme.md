<img src="./6.png"/>

# 📌Section 1.1: Show dierences in working branch

```git diff```
This will show the unstaged changes on the current branch from the commit before it. It will only show changes
relative to the index, meaning it shows what you could add to the next commit, but haven't. To add (stage) these
changes, you can use git add.
If a file is staged, but was modified after it was staged, git diff will show the differences between the current file
and the staged version.

# 📌Section 1.2: Show changes between two commits

```bash
git diff 1234abc..6789def # old new
```
E.g.: Show the changes made in the last 3 commits:
```bash
git diff @~3..@ # HEAD -3 HEAD
```
Note: the two dots (..) is optional, but adds clarity.
This will show the textual difference between the commits, regardless of where they are in the tree

# 📌Section 1.3: Show dierences for staged files
```bash
git diff --staged
```
This will show the changes between the previous commit and the currently staged files.
NOTE: You can also use the following commands to accomplish the same thing:
```bash
git diff --cached
```
Which is just a synonym for **--staged** or
```bash
git status -v
```
Which will trigger the verbose settings of the status command.

# 📌Section 1.4: Comparing branches

Show the changes between the tip of new and the tip of original:
```bash
git diff original new # equivalent to original..new
```
Show all changes on new since it branched from original:
```bash
git diff original...new # equivalent to $(git merge-base original new)...new
```
# 📌Section 1.5: Show both staged and unstaged changes

To show all staged and unstaged changes, use:
```bash
git diff HEAD
```
**NOTE**: You can also use the following command:
```bash
git status -vv
```

# 📌Section 1.6: Show differences for a specific file or directory
```bash
git diff myfile.txt
```
Shows the changes between the previous commit of the specified file (myfile.txt) and the locally-modified version
that has not yet been staged.

This also works for directories:
```bash
git diff documentation
```

The above shows the changes between the previous commit of all files in the specified directory (documentation/)
and the locally-modified versions of these files, that have not yet been staged.


To show the difference between some version of a file in a given commit and the local HEAD version you can specify
the commit you want to compare against:
```bash
git diff 27fa75e myfile.txt
```

Or if you want to see the version between two separate commits:
```bash
git diff 27fa75e ada9b57 myfile.txt
```

# 📌Section 1.7: Using meld to see all modifications in the working directory

```bash
git difftool -t meld --dir-diff
```
will show the working directory changes. Alternatively,
```bash
git difftool -t meld --dir-diff [COMMIT_A] [COMMIT_B]
```

will show the differences between 2 specific commits
