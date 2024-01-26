# Comment

Basically, these are all the commands you need to know about.


# Before anything else

Pull changes from the remote on the current branch
(retrieves all branches on the remote):

```
git pull
```


# Branch listing

List all local branches (also shows the active branch):
```
git branch
```

List all remote branches (e.g. on GitHub):

```
git branch -r
```

List all local and remote branches:

```
git branch -a
```

# Branch creating and switching


Create a new branch based on the current branch:

```
git switch -c <branch-name>
```

Switch to a branch:

```
git switch <branch-name>
```

# Statusing


Get status of the repo (current branch and what changes have been made):

```
git status
```




See changes to a specifc file:

```
git diff <file-name>
```




# Standard steps to push changes to current branch

## Step 1: Adding/Staging

Add/Stage specific modification to file (multiple files can be listed):

```
git add <file-name>
```

or (**but not appropriate in serious projects**)\
add/Stage all changes in order to then make the commit:

```
git add . 
```
## Step 2: Committing

Commit the changes with a message:

```
git commit -m "<Commit message>" 
```

or even better create an elaborate commit message:

```
git commit
```

## Step 3: Push to branch

Push commit to branch, if the branch exists on the remote
```
git push
```

Push commit to branch, if the branch does not exist on the remote.\
This will create the branch on the remote.\
(this command will be included in the message after running the `push` command, so just copy it):

```
git push --set-upstream origin <branch-name>
```


# Clean up

Clean remote branches that are deleted (e.g. via GitHub or by others)

```
git fetch -p
```

or

```
git fetch --prune
```

Delete a local branch

```
git branch -d <branch-name>
```

# Stashing

Stash changes

```
git stash
```

List stashes

```
git stash list
```

Restore stash where <index> is a index as specified by `git stash list`

```
git stash pop <index>
```