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

### Fecth the latests modifications

Fecth the latest changes from the remote branch to your current branch.

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
git pull performs two actions: git fetch + git merge.

### Workflow to modify and upload a change to a remote branch that doesn't exist

##### Step 1/6 Verify if you are in the good branch (development) #####

```
git branch -a
```

Something similar to

```
* development
  master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
```
will be show. 
You are in the good branch. If not: **git checkout development** 

##### Step 2/6 Modify something and then check the status of the branch #####
  
```
git status
```
Something similar to
  
 ```
On branch development
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```
will be show. 
These messages indicate that the branch is updated but you have a file in unstage status. You have to pass the file README.md to the stage status.
  
##### Step 3/6 Stage the files #####
  
```
git add README.md
```
  
If you want to add more files at once, use **git add * **.
  
##### Step 4/6 Status before commit #####
  
```
git status
```
  
Something similar to

```
On branch development
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   README.md
```
will be show. 

##### Step 5/6 Commit changes #####

```
git commit -m "fix comments"
```  
  
##### 6/6 Push the changes in a new remote branch #####

A development remote branch will be created.

```
git push -u origin development
```  

Something similar to

``` 
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 322 bytes | 322.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/juanon777/GitTips.git
 * [new branch]      development -> development
Branch 'development' set up to track remote branch 'development' from 'origin'.
``` 

will be show.



