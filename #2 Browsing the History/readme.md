![Banner](./2.png)

# Section 1.1: "Regular" Git Log

```bash
git log
```
will display all your commits with the author and hash. This will be shown over multiple lines per commit.If you
wish to show a single line per commit, add --oneline


If you wish to limit your command to last n commits log you can simply pass a parameter. For example, if you wish
to list last 3 commits logs
```bash
git log -3
```
# Section 1.2: Prettier log

To see the log in a prettier graph-like structure use:
```bash
git log --decorate --oneline --graph
```

Since it's a pretty big command, you can assign an alias:

```bash
git config --global alias.p-log "log --decorate --oneline --graph"

```

To use the alias version:
```
# history of current branch :
git p-log

# combined history of active branch (HEAD), develop and origin/master branches :
git p-log HEAD develop origin/master

# combined history of everything in your repo :
git p-log --all
```

# Section 1.3: Log search
```bash
git log -S"Hello World"
```
Searches for addition or removal of specific string or the string matching provided REGEXP. In this case we're
looking for addition/removal of the string Hello World
```bash
git log -G"Hello World"
```
Searches for changes in lines containing specific string or the string matching provided REGEXP.

# Section 1.3: List all contributions grouped by author name

**git shortlog** summarizes **git log** and groups by author

```bash
git shortlog

Committer 1 (<number_of_commits>):
 Commit Message 1
 Commit Message 2

 ...
Committer 2 (<number_of_commits>):
 Commit Message 1
 Commit Message 2
 ...

```
If no parameters are given, a list of all commits made per committer will be shown in chronological order.

To simply see the number of commits and suppress the commit description, pass in the summary option:
```bash
-s
--summary
```

```bash
git shortlog -s

<number_of_commits> Committer 1
<number_of_commits> Committer 2
```

To sort the output by number of commits instead of alphabetically by committer name, pass in the numbered
option:
```
-n
--numbered
```


To add the email of a committer, add the email option:
```
-e
--email
```

# Section 1.4: Searching commit string in git log


Searching git log using some string in log:
```
git log [options] --grep "search_string"
```
Example:
```
git log --all --grep "removed file"
```
Will search for removed file string in all logs in all branches.


Also,
```
git log --grep "add file" --invert-grep
```
Will show all commits that do not contain add file.

# Section 1.5: Filter logs
```
git log --after '3 days ago'
```
Specific dates work too:
```
git log --after 2016-05-01
```
 You can als use --before

You can also filter logs by author. e.g.
```
git log --author=author
```

# Section 1.6: Log showing commited files

```
git log --stat
```
This Will show all the modifications,insertions ,changed files ,etc.

# Section 1.7: Show the contents of a single commit

Using **git show** we can view a single commit

```bash
git show 48c83b3

git show 48c83b3690dfc7b0e622fd220f8f37c26a77c934
```
