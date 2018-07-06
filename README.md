## GitTips

Common git commands.

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


