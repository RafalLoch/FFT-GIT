
# How to work with GIT
## Autohotkey
Download link: 
> https://www.autohotkey.com

Settings:
<br>GitHotkey.ahk
```
; **git-specific

::gs::git status
::glo::git log --oneline
::gd::git diff
::gc::git commit -m
::gcae::git commit --allow-empty
::gck::git checkout
::gr::git rebase -i 
::gb::git branch -a
::gp::git push
::gpo::git push origin
::gst::git stash
::ga::git add -p
::gai::git add -i
::gf::git fetch
::gmnff::git merge --no-ff -e -
::-h::--help
::gk::gitk --all
::githelpme::git reset ORIG_HEAD
::gcrerere:: git config rerere.enabled true
```

## Windows Terminal
> https://docs.microsoft.com/en-us/windows/terminal/get-started
> https://docs.microsoft.com/en-us/windows/terminal/tutorials/powerline-setup
> https://ohmyposh.dev

# Git Index
## Working directory vs Repository

-   **Working directory** - is the directory with your source files under git control (in the root of all dirs under control .git file is present).
- **Repository** – the Git directory where Git stores metadata and object database of project (information about branches, commit etc). 

We can make some changes in working directory (for instance add new file) and update these changes to repository.

## Working directory vs Repository

Each file in working directory can be in one of two states:
- **Tracked** – all files which are in repository
- **Untracked** – files which are in working directory but not in repository

## Staging area (index)
**Staging area** – file which store information what will go into next commit. It technial name is index.

- **Modified** – means that some changed were made in file but no commited yet
- **Staged** – means that modified file was marked (by git add <path>) to go into next commit
- **Commited** – means that is already in repository


## Git commit

- **Snapshots**, not differences!
- Git store **entire new file** insted of storing only changes made in this file
- Git commit is not „change” but is **snapshot** of repository.

# What is origin?

- Origin is just default name of ref remote repository!
- By default when you use command like git push, git pull Git add origin to this command (git push origin)
- You can have reference to many remote repository.

### git fetch

- Its associated with entire remote repository more than remote branch.
- Download data to local repository – doesn’t automatically merge any work.
- Update local branch store in .git/refs/remotes/<remote>
  - ```git fetch <remote> (default origin)``` -> fetch all changes from remote repo
   - ```git fetch  <remote> <branch>``` -> fetch changes only from <branch> in  <remote> repo
   - ```git fetch –all``` -> fetch all changes for each remote repository

For instance if locally we have branch fetch_branch and we have reference to remote repo origin
git fetch will update our local branch origin/fetch_branch (remote/branch_name)
### branch tracking

- Branch tracking is telling git to pair remote branch with his local equivalent. 
- For instance we can set that branch tracked_untracket (local) should track branch origin/tracked_untracked.
If branch was created in remote repository (bitbucket/github) we can track branch by using command
```
git checkout --track <remote>/<branch
```
If branch was created in local repo but not in remote repo we have to create new branch in remote we do this by pushing our branch.
```
git push --set-upstream <remote> <branch>
```

Branch tracking is important in case like renaming branch. We have to update either local branch and remote branch.

### git merge

Incorporates changes from named commits into current branch.
```
git merge <branch>
```
If we not provide <branch> name, git will try merge our branch with currently **tracking branch**

### git pull

Incorporated changes from remote repository into current branch.
It shortland for 
``` 
git fetch <remote> <branch>
```
``` 
git merge <branch>
 ```

### branch

- Branch is pointer to some commit (snapshot)
- To know what branch you currently on git has special pointer called HEAD
```
git checkout -b <branch>
```
# Undo things

### git revert <commit>

- Create new commit to reverse the effect of some earlier commit.

### git reset --hard <commit>

- move HEAD to specified commit (snapshot)
- remove commits after specified commit 
- remove changes made in removed commits

### git reset <commit>

- move HEAD to specified commit (snapshot)
- remove commits after specified commit 
- add changes made in removed commits to working directory

# Merging

### merge vs rebase

summary table

### cherry-pick <commit>

Give one or more existing commits, apply the change each one introduces, recording a new commit for each. That mean for each cherry picking commit is creating new commit with new SHA-1