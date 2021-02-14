# 📌Section 1.1: Staging All Changes to Files

```bash
git add -A
(or)
git add .
```

# 📌Section 1.2: Unstage a file that contains changes

```bash
git reset <filePath>
```
# 📌Section 1.3: Add changes by hunk
You can see what "hunks" of work would be staged for commit using the patch flag:
git add -p
or
git add --patch
This opens an interactive prompt that allows you to look at the diffs and let you decide whether you want to include
them or not.
Stage this hunk [y,n,q,a,d,/,s,e,?]?
* 'y'  stage this hunk for the next commit
* 'n'  do not stage this hunk for the next commit
* 'q'  quit; do not stage this hunk or any of the remaining hunks
* 'a'  stage this hunk and all later hunks in the file
* 'd'  do not stage this hunk or any of the later hunks in the file
* 'g'  select a hunk to go to
* '/'  search for a hunk matching the given regex
* 'j'  leave this hunk undecided, see next undecided hunk
* 'J'  leave this hunk undecided, see next hunk
* 'k'  leave this hunk undecided, see previous undecided hunk
* 'K'  leave this hunk undecided, see previous hunk
* 's'  split the current hunk into smaller hunks
* 'e'  manually edit the current hunk
* '?'  print hunk help

# 📌Section 1.4: Interactive add

`git add -i` (or --interactive) will give you an interactive interface where you can edit the index, to prepare what
you want to have in the next commit. You can add and remove changes to whole files, add untracked files and
remove files from being tracked, but also select subsection of changes to put in the index, by selecting chunks of
changes to be added, splitting those chunks, or even editing the diff. Many graphical commit tools for Git (like e.g.
git gui) include such feature; this might be easier to use than the command line version.
It is very useful (1) if you have entangled changes in the working directory that you want to put in separate commits,
and not all in one single commit (2) if you are in the middle of an interactive rebase and want to split too large
commit.

# 📌Section 1.5: Show Staged Changes

To display the hunks that are staged for commit:
```bash
git diff --cached
```
# 📌Section 1.6: Staging A Single File

To stage a file for committing, run
```bash
git add <filename>
```

# 📌Section 1.7: Stage deleted files
```bash
git rm filename
```
To delete the file from git without removing it from disk, use the --cached flag
```bash
git rm --cached filename
```