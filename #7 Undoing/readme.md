<img src="./7.png"/>

# 📌Section 1.1: Return to a previous commit

To jump back to a previous commit, first find the commit's hash using git log.


To temporarily jump back to that commit, detach your head with:
```bash
git checkout 789abcd
```
This places you at commit 789abcd. You can now make new commits on top of this old commit without affecting the
branch your head is on. Any changes can be made into a proper branch using either branch or checkout -b.


To roll back to a previous commit while keeping the changes:
```bash
git reset --soft 789abcd
```

To roll back the last commit:
```bash
git reset --soft HEAD~
```

To permanently discard any changes made after a specific commit, use:
```bash
git reset --hard 789abcd
```
To permanently discard any changes made after the last commit:
```bash
git reset --hard HEAD~
```


# 📌Section 1.2: Undoing changes

Undo changes to a file or directory in the working copy.
```bash
git checkout -- file.txt
```

To only undo parts of the changes use --patch. You will be asked, for each change, if it should be undone or not.
```bash
git checkout --patch -- dir
```
To undo changes added to the index.
```bash
git reset --hard
```

Without the --hard flag this will do a soft reset


# 📌Section 1.3: Using reflog
# 📌
# 📌
# 📌
# 📌
# 📌