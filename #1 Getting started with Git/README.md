<img src="./img/1.png"/>

# Section 1.1: Create your first repository, then add and commit files

 * Install Git from [here](https://git-scm.com/)

Once Git is installed, navigate to the directory you want to place under version control and create an empty Git
repository:
```bash
 git init 
```
This creates a hidden folder, .git, which contains the plumbing needed for Git to work.
Next, check what files Git will add to your new repository; this step is worth special care:
```
git status
```
Adding files
```
git add <filename1> <filename2>
git add *.<file-extention>            # adds all files with that extention
git add .                             # adds all files
```
Commit all the files that have been added, along with a commit message:

```
git commit -m "Initial commit"

```
This creates a new commit with the given message. A commit is like a save or snapshot of your entire project. You
can now push, or upload, it to a remote repository, and later you can jump back to it if necessary.
If you omit the -m parameter, your default editor will open and you can edit and save the commit message there

**Adding a remote**
To add a new remote, use the git remote add command on the terminal, in the directory your repository is stored
at.

The git remote add command takes two arguments:
* 1. A remote name, for example, origin
* 2. A remote URL, for example,    ```https://<your-git-service-address>/user/repo.git```

```
 git remote add origin https://<your-git-service-address>/owner/repository.git
```


# Section 1.2: Clone a repository

The git clone command is used to copy an existing Git repository from a server to the local machine.


For example, to clone a GitHub project:
```
cd <path where you would like the clone to create a directory>
git clone https://github.com/username/projectname.git
```

Note:
1. When cloning to a specified directory, the directory must be empty or non-existent.
2. You can also use the ssh version of the command:
```
git clone git@github.com:username/projectname.git
```

# Section 1.3: Sharing code

To share your code you create a repository on a remote server to which you will copy your local repository

On the remote server:
```
git init --bare /path/to/repo.git
```
On the local machine:
```
git remote add origin ssh://username@server:/path/to/repo.git
```
(Note that ssh: is just one possible way of accessing the remote repository.)

Now copy your local repository to the remote:
```
git push --set-upstream origin master
```
Adding --set-upstream (or -u) created an upstream (tracking) reference which is used by argument-less Git
commands, e.g. git pull

# Section 1.4: Setting your user name and email

You need to set who you are *before* creating any commit. That will allow commits to have the
right author name and email associated to them.

To declare that identity for all repositories, use git config --global


```
git config --global user.name "Your Name"
git config --global user.email mail@example.com
```


To declare an identity for a single repository, use git config inside a repo.
```
cd /path/to/my/repo
git config user.name "Your Login At Work"
git config user.email mail_at_work@example.com
```

* Remove a global identity
```
git config --global --remove-section user.name
git config --global --remove-section user.email

```
# Section 1.5: Setting up the upstream remote

To get more information about any git command – i.e. details about what the command does, available options and
other documentation – use the --help option or the help command.



For example, to get all available information about the git pull command, use:
```
git pull --help
git help pull
```

If you only want a quick help showing you the meaning of the most used command line flags, use -h:

```
git pull -h
```
