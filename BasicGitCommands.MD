[<< BACK](README.md)

- [Clone repository](#clone-repository)
- [List local and remote branches](#list-local-and-remote-branches)
- [Create a branch from a remote branch](#create-a-branch-from-a-remote-branch)
- [Fetch and merge the latest modifications](#fetch-and-merge-the-latests-modifications)
- [List all the branches and where the local branches points](#list-all-the-branches-and-where-the-local-branches-points)
- [Delete a local branch](#delete-a-branch)
- [Optimizing your local repository](#optimizing-your-local-repository)
- [Switch to another local branch](#switch-to-another-local-branch)
- [Save your work and update from a remote branch](#save-the-current-state-of-the-working-directory-and-update-from-a-remote-branch)
- [Update your branch losing your local changes](#force-a-branch-update-by-losing-your-local-changes)
- [Roll back the changes (stage)](#roll-back-the-changes-youve-made-stage---unstage)
- [Roll back the changes (commit)](#turn-back-the-changes-after-the-last-commit-you-have-made)
- [Clean tracked remote branches](#clean-tracked-remote-branches)
- [Create a branch from a remote commit](#create-a-local-branche-from-a-remote-commit)
- [Update your local branch with another remote branch](#update-your-local-branch-with-another-remote-branche)



### Clone repository

The first step is always to clone the repository where you are going to work:

```
git clone https://github.com/juanon777/GitTips.git
```

The output screen will be similar to:

```
Cloning into 'GitTips'...
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (4/4), done.
```

A **GitTips** folder will be created.

### List local and remote branches

```
git branch -a
```

Something similar to

```
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
```
  
will be show. 
The * indicates that the current branch is master.


### Create a branch from a remote branch

How to create a local branch (development) from a remote branch (origin/master)

```
git checkout -b development origin/master
```
Something similar to

```
Switched to a new branch 'development'
Branch 'development' set up to track remote branch 'master' from 'origin'.
```

will be show. 

### Fetch and merge the latests modifications

Fetch the latest changes from the remote branch to your current branch.

```
git pull
```

Something similar to

```
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/juanon777/GitTips
   d3e09b3..c7ab3b6  master     -> origin/master
Updating d3e09b3..c7ab3b6
Fast-forward
 README.md | 21 +++++++++++++++++++--
 1 file changed, 19 insertions(+), 2 deletions(-)
```

will be show. 
This output indicates that there was a change in the **readme.md** file.
git pull performs two actions: **git fetch** + **git merge**.

### List all the branches and where the local branches points

```
git branch -vv
```
Something similar to

```
* feature0102 20f23a1 [origin/development] new feature
development   52fddb1 [origin/development] fix comments
master        0fa8b46 [origin/master] new file
```

will be show.

e.g **feature0102** branch points to **origin/development** but you can push to another branch with:

```
git push -u origin feature0102
```

If you execute:

```
git branch -vv
```

Something similar to

```
* feature0102 f3fa2b4 [origin/feature0102] new feature
development   52fddb1 [origin/development] fix comments
master        0fa8b46 [origin/master] new file
```
will be show. 

### Delete a branch

Delete a local branch. If this branch isn't merge will ask you for confirmation

```
git branch -d feature0102
```

Force to delete a local branch

```
git branch -D feature0102
```


### Optimizing your local repository

Optimize your git repositories with:

```
git gc
```

### Switch to another local branch

E.g you are in the local branch feature0102 and you want to work in the development branch.

```
git checkout development
```

### Save the current state of the working directory and update from a remote branch

You have not finished your development yet but you want to upgrade from a remote branch. With the stash command you can update from a branch in a clean way and reintegrate your work later.
  If there are conflicts when updating. First fix the conflict and then reintegrate your work in the branch.

```
git stash
git pull
optional (fix de conflicts: git add, git commit ??)
git stash pop
```

### Force a branch update by losing your local changes

Lost all your uncommitted changes and update the latest changes from a remote repository.

```
git fetch --all
git reset --hard origin/development (throws away all your uncommitted changes)
```

### Roll back the changes you've made stage -> unstage

```
git reset HEAD
```

### Roll back the changes after the last commit you have made

```
git reset --hard HEAD~1
```

You lost your commit!!


### Clean tracked remote branches

```
git pull --prune
```

### Create a local branche from a remote commit

You need to find a commit id.

```
git checkout -b development ab28e731101c154f70d394c978ca7d40b198433a
```

### Update your local branch with another remote branche

You work on a local branch (**featureLocal**) that points to a remote branch (**featureRemote**).
You can update your local branch from another remote branch (**development**).
Recommended step to send a pull-request to development. This step minimizes conflicts.

```
git pull origin development
```




[<< BACK](README.md)
