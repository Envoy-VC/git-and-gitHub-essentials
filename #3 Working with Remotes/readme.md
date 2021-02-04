![Banner](./3.png)
# 📌Section 1.1: Setting a Remote Branch

```bash
git remote add origin /link/to/git/repo
```

# 📌 Section 1.2: Deleting a Remote Branch

To delete a remote branch in Git:
```bash
git push [remote-name] --delete [branch-name]
```

# 📌Section 1.3: Changing Git Remote URL

Check existing remote
```bash
git remote -v
# origin https://github.com/username/repo.git (fetch)
# origin https://github.com/usernam/repo.git (push)
```
Changing repository URL
```bash
git remote set-url origin https://github.com/username/repo2.git
# Change the 'origin' remote's URL
```
Verify new remote URL
```bash
git remote -v
# origin https://github.com/username/repo2.git (fetch)
# origin https://github.com/username/repo2.git (push)
```

# 📌Section 1.4: List Existing Remotes

List all the existing remotes associated with this repository:
```bash
git remote
```
List all the existing remotes associated with this repository in detail including the fetch and push URLs:
```bash
git remote --verbose
```
or simply
```bash
git remote -v
```
# 📌Section 1.5: Getting Started


Syntax for pushing to a remote branch
```bash
git push <remote_name> <branch_name>
```
Example
```bash
git push origin master
```


# 📌Section 1.6: Renaming a Remote

To rename remote, use command `git remote rename`
The `git remote rename` command takes two arguments:
* An existing remote name, for example : origin
* A new name for the remote, for example : destination
Get existing remote name
```bash
git remote
# origin
```
Check existing remote with URL
```bash
git remote -v
# origin https://github.com/username/repo.git (fetch)
# origin https://github.com/usernam/repo.git (push)
```
Rename remote
```bash
git remote rename origin destination
# Change remote name from 'origin' to 'destination'
```
Verify new name
```bash
git remote -v
# destination https://github.com/username/repo.git (fetch)
# destination https://github.com/usernam/repo.git (push)
```
=== Posible Errors ===
1. Could not rename config section 'remote.[old name]' to 'remote.[new name]'
This error means that the remote you tried the old remote name (origin) doesn't exist.
2. Remote [new name] already exists.
Error message is self explanatory

# 📌Section 1.7: Show information about a Specific Remote

Output some information about a known remote: origin
```bash
git remote show origin
```
Print just the remote's URL:
```bash
git config --get remote.origin.url
```


# 📌Section 1.8: Set the URL for a Specific Remote

You can change the url of an existing remote by the command
```bash
git remote set-url remote-name url
```


# 📌Section 1.9: Get the URL for a Specific Remote

You can obtain the url for an existing remote by using the command
```bash
git remote get-url <name>
```
By default, this will be
```bash
git remote get-url origin
```


# 📌Section 1.10: Changing a Remote Repository

To change the URL of the repository you want your remote to point to, you can use the set-url option, like so:
```bash
git remote set-url <remote_name> <remote_repository_url>
```
