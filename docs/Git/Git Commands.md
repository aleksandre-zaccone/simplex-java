
# git init

The `git init` command creates a new Git repository. It can be used to convert an existing, unversioned project to a Git repository or initialize a new, empty repository.

Executing `git init` creates a .git subdirectory in the current working directory, which contains all of the necessary Git metadata for the new repository. This metadata includes subdirectories for objects, refs, and template files. A HEAD file is also created which points to the currently checked out commit.
# git config

Get and set repository or global options. 
By default, `git config` will write to a local level if no configuration option is passed. Local configuration values are stored in a file that can be found in the repo's .git directory: `.git/config

Global level configuration is user-specific, meaning it is applied to an operating system user. Global configuration values are stored in a file that is located in a user's home directory. ~ `/.gitconfig` on unix systems and `C:\Users\\.gitconfig` on windows
`
To read configuration:
```git
git config user.name
git config user.email
git config --list
```

To write values:
```git
git config --global user.name "Aleksandre Ablotia"
git config --global user.email "your_email@example.com"
git config --global core.editor kate
git config --global merge.tool kdiff3
git config --global color.ui true
```


# git branch

The `git branch` command lets you create, list, rename, and delete branches. Git does not creates a master branch until first commit
```git
git branch // List all local branches. 
git branch <branch> // creates a branch with given name, but dont checkout new branch
git branch -d <branch> // deletes branche by given name (safe mode)
git branch -D <branch> // deletes branche by given name (force mode)
git branch -m <branch> // Rename the current branch to "branch"
git branch -a // List all remote branches. 

```

# git checkout

The `git checkout` let us switch between branches.
```git
git checkout <branch> // switch to another branch
git checkout -b ＜new-branch＞ // create and switch to new branch
```



# git add
The `git add` command adds a change in the working directory to the staging area. It tells Git that you want to include updates to a particular file in the next commit. However, `git add` doesn't really affect the repository in any significant way—changes are not actually recorded until you run `git commit`.
```git
git add <file> // add file
git add <directory> // add directory
```

# git commit
The `git commit` command captures a snapshot of the project's currently staged changes. 
```git
git commit // commit one by one
git commit -a // commit all
git commit -m "commit message" // commit and add message
git commit -am "commit message" // commit all and add message
git commit --amend // add changes to last commit

```


# git status
The `git status` command displays the state of the working directory and the staging area. It lets you see which changes have been staged, which haven’t, and which files aren’t being tracked by Git

# git merge


# git push
`git push` is most commonly used to publish an upload local changes to a central repository. After a local repository has been modified a push is executed to share the modifications with remote team members.
```git
git push
git push --all // Push all branches
```

# git clone

`git clone` command clones (download) a repository that already exists on GitHub, including all of the files, branches, and commits.
```git
git clone [url] // clone/copy remote repository with all data
git clone [url] --branch [branch] --single-branch // clone only one branch
```

# git remote

The `git remote` command is essentially an interface for managing a list of remote entries that are stored in the repository's `./.git/config` file.
```git
git remote // List the remote connections we have to other repositories.
git remote -v // Same as the above command, but include the URL of each connection.
```
# git fetch
The `git fetch` command downloads commits, files, and refs from a remote repository into your local repo, but not update your local repo's working state, leaving your current work intact.
```git
git fetch <remote> // fetch all
git fetch <remote> <branch> // fetch only one branch
```

# git pull
The `git pull` command is used to fetch and download content from a remote repository and immediately update the local repository to match that content. Merging remote upstream changes into your local repository is a common task in Git-based collaboration work flows. The `git pull` command is actually a combination of two other commands, `git fetch` followed by `git merge`. In the first stage of operation git pull will execute a `git fetch` scoped to the local branch that HEAD is pointed at. Once the content is downloaded, `git pull` will enter a merge workflow. A new merge commit will be-created and HEAD updated to point at the new commit.
```git
git pull <remote> // fetch + merge + create merge commit
git pull --no-commit <remote> // fetch + merge

```

# git clean

# git reset

# git revert

# git log

# git rebase

# git rebase -i




