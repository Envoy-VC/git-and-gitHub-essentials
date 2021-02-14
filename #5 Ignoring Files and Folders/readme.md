<img src="./5.png"/>

# 📌Section 1.1: Ignoring files and directories with a .gitignore file

You can make Git ignore certain files and directories — that is, exclude them from being tracked by Git — by
creating one or more **.gitignore** files in your repository.
In software projects, .gitignore typically contains a listing of files and/or directories that are generated during the
build process or at runtime. Entries in the .gitignore file may include names or paths pointing to:
* 1. temporary resources e.g. caches, log files, compiled code, etc.
* 2. local configuration files that should not be shared with other developers
* 3. files containing secret information, such as login passwords, keys and credentials
When created in the top level directory, the rules will apply recursively to all files and sub-directories throughout
the entire repository. When created in a sub-directory, the rules will apply to that specific directory and its subdirectories.
When a file or directory is ignored, it will not be:
* 1. tracked by Git
* 2. reported by commands such as git status or git diff
* 3. staged with commands such as git add -A
eg-
```bash
# Ignore files called 'file.abc'
file.abc

# Ignoring files with full path.
dir/otherdir/file.abc

# Ignoring directories
bin/

# Ignoring files by extension
*.abc

# To ignore files only at the top level directory, but not in its
# subdirectories, prefix the rule with a `/`
/*.apk
/*.abc
```

# 📌Section 1.2: Checking if a file is ignored

The `git check-ignore` command reports on files ignored by Git.
You can pass filenames on the command line, and git check-ignore will list the filenames that are ignored. For
example:
```bash
$ git check-ignore ignoredFile.io Readme.md
ignoredFile.io
```

# 📌Section 1.3: Exceptions in a .gitignore file

If you ignore files by using a pattern but have exceptions, prefix an exclamation mark(!) to the exception. For
example:
```bash
*.txt
!important.txt
```
The above example instructs Git to ignore all files with the .txt extension except for files named important.txt.
If the file is in an ignored folder, you can NOT re-include it so easily:
```bash
folder/
!folder/*.txt
```
In this example all .txt files in the folder would remain ignored.

The right way is re-include the folder itself on a separate line, then ignore all files in folder by *, finally re-include
the *.txt in folder, as the following:
```bash
!folder/
folder/*
!folder/*.txt
```

**Note**: For file names beginning with an exclamation mark, add two exclamation marks or escape with the \
character:
```bash
!!includethis
\!excludethis
```
# 📌Section 1.4: A global .gitignore file

To have Git ignore certain files across all repositories you can create a global **.gitignore** with the following command
in your terminal or command prompt:
```bash
$ git config --global core.excludesfile <Path_To_Global_gitignore_file>
```

Git will now use this in addition to each repository's own .gitignore file. Rules for this are:
* If the local .gitignore file explicitly includes a file while the global .gitignore ignores it, the local
.gitignore takes priority (the file will be included)
* If the repository is cloned on multiple machines, then the global .gigignore must be loaded on all machines
or at least include it, as the ignored files will be pushed up to the repo while the PC with the global
.gitignore wouldn't update it. This is why a repo specific .gitignore is a better idea than a global one if the
project is worked on by a team


# 📌Section 1.5: Ignore files that have already been committed to a Git repository


If you have already added a file to your Git repository and now want to stop tracking it (so that it won't be present
in future commits), you can remove it from the index:
```bash
git rm --cached <file>
```

This will remove the file from the repository and prevent further changes from being tracked by Git. The **--cached**
option will make sure that the file is not physically deleted.

Note that previously added contents of the file will still be visible via the Git history.

Keep in mind that if anyone else pulls from the repository after you removed the file from the index, their copy
will be physically deleted.


# 📌Section 1.6: Ignore files locally without committing ignore rules

If you want to ignore certain files in a repository locally and not make the file part of any repository, edit
.git/info/exclude inside your repository.
For example:
```bash
# these files are only ignored on this repo
# these rules are not shared with anyone
# as they are personal
gtk_tests.py
gui/gtk/tests/*
localhost
```

# 📌Section 1.7: Ignoring subsequent changes to a file (without removing it)

Sometimes you want to have a file held in Git but ignore subsequent changes.
Tell Git to ignore changes to a file or directory using update-index:
```bash
git update-index --assume-unchanged my-file.txt
```

The above command instructs Git to assume my-file.txt hasn't been changed, and not to check or report
changes. The file is still present in the repository


# 📌Section 1.8: Ignoring a file in any directory

To ignore a file foo.txt in any directory you should just write its name:
```bash
foo.txt # matches all files 'foo.txt' in any directory
```
If you want to ignore the file only in part of the tree, you can specify the subdirectories of a specific directory with
** pattern:

```bash
bar/**/foo.txt # matches all files 'foo.txt' in 'bar' and all subdirectories
```
Or you can create a .gitignore file in the bar/ directory. Equivalent to the previous example would be creating file
bar/.gitignore with these contents:
```bash
foo.txt # matches all files 'foo.txt' in any directory under bar/
```
# 📌Section 1.9: Ignoring files in subfolders (Multiple gitignore files)

Suppose you have a repository structure like this:
```bash
examples/
 output.log
src/
 <files not shown>
 output.log
README.md
```
output.log in the examples directory is valid and required for the project to gather an understanding while the one
beneath src/ is created while debugging and should not be in the history or part of the repository.

There are two ways to ignore this file. You can place an absolute path into the .gitignore file at the root of the
working directory:
```bash
# /.gitignore
src/output.log
```
Alternatively, you can create a .gitignore file in the src/ directory and ignore the file that is relative to this
.gitignore:
```bash
# /src/.gitignore
output.log
```

# 📌Section 1.10: Finding files ignored by .gitignore

You can list all files ignored by git in current directory with command:
```bash
git status --ignored
```

So if we have repository structure like this:
```
.git
.gitignore
./example_1
./dir/example_2
./example_2
```
...and .gitignore file containing:
```
example_2
```

...than result of the command will be:
```bash
$ git status --ignored
On branch master
Initial commit
Untracked files:
 (use "git add <file>..." to include in what will be committed)
.gitignore
.example_1
Ignored files:
 (use "git add -f <file>..." to include in what will be committed)
dir/
example_2
```

If you want to list recursively ignored files in directories, you have to use additional parameter - --untrackedfiles=all
```bash
$ git status --ignored --untracked-files=all
```
