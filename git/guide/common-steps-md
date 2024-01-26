# Common steps

There are a set of steps that is almost always used in Git. Let's explore them. I will assume that Git is already setup with a SSH key or similar and it is ready to be used.

After having read this, the [cheat sheet]() will make sense.

## Table of Contents
0. [Cloning a Git repository (repo)](#0-cloning-a-git-repository-repo)

1. [Orienting ourselves](#1-orienting-ourselves)

2. [Branch management](#2-branch-management)

3. [Modifying files and committing](#3-modifying-files-and-committing)

4. [Cleaning up branch list](#4-cleaning-up-branch-list)

5. [Switch branch after already having done changes](#5-switch-branch-after-already-having-done-changes)

6. [When others have made changes you don't have on your machine](#6-when-others-have-made-changes-you-dont-have-on-your-machine)


## 0. Cloning a Git repository (repo)

Assuming we already have created a Git repository (repo) in some Git platform such as GitHub, we then want to clone it into some directory on our system. Cloning means to download the Git repository to one's local machine and be able to sync it with the online version. Let's say we want to clone it into a directory `some-dir` and that we have already navigated to the directory in our terminal and our terminal prompt looks like this:

```
some-dir % 
```

We then get the SSH link (*e.g.,* `git@github.com:KTH-DD2480-Fundsoft/learning.git`) or similar from our platform and write:

```
some-dir % git clone git@github.com:KTH-DD2480-Fundsoft/learning.git
```

After this, we may have to enter our password and a directory containing the repo should then be created in the directory we are in, `some-dir` in our case:

```
.
└── learning
```

The directory will conatain a hidden directory `.git` which is what keeps all the git functionality stuff. We leave this directory alone. To start using git on our new repository, we navigate into it in our terminal:

```
some-dir % cd learning
learning %
```

Now we are in our git repo but locally. From now on, the prompt part `learning %` will be omitted, but do note that all the commands are made within this directory.

## 1. Orienting ourselves

Creating a branch from the `main` branch is usually one of the first meaningful steps when using Git on a repo. But before doing that, let's orient ourselves.

### 1.1. Listing branches

We can always use the command `git branch` to see all the branches we have and in which branch we are currently in:

```
learning % git branch
* main
```

However, this is not the full picture. By only writing `git branch`, you only list the local branches, which are the branches you have locally on your machine. There might be branches in the repo which you haven't brought in into your machine yet and to see those, you can write `git branch -r`:

```
learning % git branch -r
  origin/HEAD -> origin/main
  origin/main
```

Or to see both the local branches and remote branches, you write `git branch -a`:

```
learning % git branch -a
* main
  remotes/origin/HEAD -> origin/main
  remotes/origin/main
```

### 1.2. Current status

We can always use the the command `git status` to see the current status of our repo:

```
learning % git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

If there are changes that need to be commited, the message can look like this instead:

```
learning % git status
On branch <some-branch>
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   <some-file>
        modified:   <another-file>

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        <an-untracked-file>
        <another-untracked-file>

no changes added to commit (use "git add" and/or "git commit -a")
```

## 2. Branch management

To create a branch from the current branch we are on, there are different commands due to historical reasons. Previously, the commands `branch` and `checkout` were used for creating branches and moving into them. However, the new command `switch` have made it much more intuitive to do this.

### 2.1. Creating a branch

The following command can be made to create a branch from the current branch:

```
git switch -c <branch-name>
```

### 2.2. Switching to a branch

The following command can be made to switch to an existing branch

```
git switch <branch-name>
```

## 3. Modifying files and committing 

When having made modifications, you want ultimately do what is called "push" the changes to the online version of the repo so that you can do a Pull Request, if you're on GitHub (more about Pull Request in a seperate file). But in order to push the changes, there are a series of steps to do first.

Firstly, if you add a new file, then the branch needs to register this. Similarly, if you delete a file, then the branch needs to register this. Secondly, if you have made changes to an existing file which the branch knows exist, then the branch needs to register this. After having registered all the changes, then one has to *commit* to the changes by making what is called a *commit*. After commiting, the changes can be pushed. In the next sections, we will go over these steps.

### Note: The term "staged"
 One thing to keep in mind while reading the following sections is that any file that has been "added" with the command `git add` is called a *staged file*.

### 3.1. Adding/Staging new files

Files that the branch doesn't know about are called *untracked files*. To make the branch know about these files the following command can be made:

```
git add <name-of-untracked-file>
```

This is called to *add* or *stage* a an untracked file. You can also add multiple files at once:

```
git add <file-1> <file-2>
```


### 3.2 Add/Stage changes/modifications

To add or stage the changes made in an existent file then the same command can be made and Git will know that modifications are being added/staged and not an entirely new file:

```
git add <name-of-modified-existent-file>
```

The logic behind Git using the same command for adding changes and adding new files is to simplify the experience. Adding a new file could indeed be seen as a modification in of itself. 

You can also add multiple modifications/new files at once:

```
git add <modified-file-1> <new-file-1>
```

Or you could even add all the modifications at once, but keep in mind that this will also add the modifications of the other sections below:

```
git add .
```

**This command adds all modifications**. Generally, this approach is not recommended as this won't produe any meaningful commit messages. More about this later.

### 3.3. Delete a file

If a file is deleted, then this is simply seen as a modification by the branch. Thus, the same command `git add` can be used to add this modification/change. To regesiter the file deletion, the same command can be made:

```
git add <name-of-deleted-file>
```

### 3.4. Restore a file / Discard changes

If you want to discard the changes made to an existent file, then you can make the following command:

```
git restore <name-of-modified-existent-file>
```

### 3.5 See current changes to file

If you want to see in the terminal what changes have been made to a file, you can run:

```
git diff <file-name>
```

### 3.6. Unstage a file

If you have added a file, you can see this by writing `git status`:

```
learning % git status
On branch <branch-name>
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   <modified-file>
        new file:   <new-file>
```

To unstage this, you can simply write:

```
git restore --staged <file-name>
```

as indicated by the message.

### 3.7. Commiting

Once ready to commit the staged modifications, then you commit the modifications by making a commit message. A simple way is to use the following command.

```
git commit -m "<Commit message>" 
```

However, this is not the best way to create commit messages. There is a better way... Introducing [Conventional Commits](conventional-commits.md).

After reading that, then it should be apparent that an easy way of writing a commit message that doesn't need further elaboration but that still follows the specification is something like the following:

```
git commit -m "feat: add new back button to home page" 
```

If you want to write an elaborate commit message, then just simply skip the `-m` flag and run:

```
git commit
```

This is going to open your editor, probably Vim. When you are finished, if the editor is Vim, then press `ESC`, type `:wq` (*which stands for write and quit*) and then press `Enter`.

### 3.8. Pushing commits

Once you have made commits, then these commits can be pushed to the remote version of the repo. To do this, simply run:

```
git push
```

The first time you will get the following message:

```
learning % git push
fatal: The current branch <branch-name> has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin <branch-name>
```

Just copy the written command and run it again:

```
git push --set-upstream origin <branch-name>
```

Then it should be pushed succesfully.


## 4. Cleaning up branch list

After a branch has been deleted after it has been merged to main, you can switch back to main and create a new branch. You can then safely delete your branch locally:

```
git branch -d <branch-name>
```

However, if you now run `git branch -a`, you will still see the branch on the remote version even though it has already been deleted there. To update the list, run:

```
git fetch -p
```

which is the same as 

```
git fetch --prune
```

## 5. Switch branch after already having done changes

Sometimes, you make changes to a branch where you did not intend to do the changes. This is very annoying because Git will prevent you from branching until you have handled the changes. Fear not, because the command `git stash` comes to the rescue.

This is a command which takes your changes and puts them aside momentarily in a stack-like structure. Think like a tower of blocks. You put blocks on top of each other, and the "first" block in the tower can be seen as the one on top. The blocks will have an index each, where the top block begins with index "0".

Anyhow, when you have changes you want to put aside, you run:

```
git stash 
```

Now you can list your stash by running:

```
git stash list
```

If you would make some more changes and stash them, they would lay on top the first stashed changes.

When you have stashed away your changes, you can freely switch to whatever branch you want. Yeahhh. And once you have switched to the desired branch, you can get back your changes by *popping* them out from your stash by running:

```
git stash pop <index>
```

where `<index>` is the index of the stashed changes you want to recover, as specified by the `git stash list`. If you have only stashed away one set of changes, the index will of course be `0`. So you can run:

```
git stash pop 0
```

## 6. When others have made changes you don't have on your machine

As the project advances, team members will have made changes which you won't have on your machine, so **it is crucial** that you make the following step a habit:

Once you open the repo on your machine again, make the habit to always run:

```
git pull
```

This will pull all the changes on the remote to your machine so that you are up to date. After having done this, then you can create branches and make changes.