# Git Cheat Sheet
Reference: https://www.interviewbit.com/git-cheat-sheet/
#
- https://github.com/nirajp82/Powershell_Util/blob/main/Git_Powershell_OhMyPosh_Setup.md
- https://anshbadaya.medium.com/customizing-windows-terminal-with-posh-git-and-oh-my-posh-752c0e0eb8cb
- https://www.hanselman.com/blog/my-ultimate-powershell-prompt-with-oh-my-posh-and-the-windows-terminal
- Install-Module posh-git -Scope CurrentUser
- Install-Module oh-my-posh -Scope CurrentUser
- Install-Module -Name PSReadLine -Scope CurrentUser -Force -SkipPublisherCheck

#Import the modules
- Import-Module posh-git
- Import-Module oh-my-posh
- #Set-PoshPrompt -Theme Paradox
- Set-PoshPrompt C:\Users\NirajP\Documents\PowerShell\Themes\agnoster.omp.json
- #Produce UTF-8 by default
- #https://news.ycombinator.com/item?id=12991690
- $PSDefaultParameterValues["Out-File:Encoding"] = "utf8"
- #bash-style completion
- Set-PSReadlineKeyHandler -Key Tab -Function Complete
#
## https://www.interviewbit.com/git-interview-questions/
#

## How to Resolve Git Conflict while pushing the code

```bash
# Switch to the target branch
git switch Target_Branch

# Rebase the target branch with changes from the master branch
git rebase Master_Branch

# Resolve conflicts in TortoiseGit

# Continue with the rebase after conflict resolution
git rebase --continue

# If using vim editor, add comments or exit by typing ":q"

# Once conflicts are resolved, push the changes to the target branch
git push --force-with-lease
```

## Git Cherry-Pick

Assume we have branch A with (X, Y, Z) commits. We need to add these commits to branch B.

```bash
# Checkout to Branch B
git checkout B

# Cherry-pick commits from Branch A to Branch B
git cherry-pick SHA-COMMIT-X
git cherry-pick SHA-COMMIT-Y
git cherry-pick SHA-COMMIT-Z
```

Reference: [Stack Overflow](https://stackoverflow.com/questions/2474353/how-to-copy-commits-from-one-branch-to-another).

## Git Log Visualization

```bash
# View a decorated, graph-based, one-line log with author and date information
git log --pretty="%C(Yellow)%h%C(reset) %ad (%C(Green)%cr%C(reset))%x09 %C(Cyan)%an: %C(reset)%s%x09%C(Magenta)(%d)%C(reset)" --date=short -15 --decorate --remotes --graph
```
## Git Reset

```bash
# Reset to a specific commit hash
git reset --hard e5555ca54258113a51c417b2f27edcfac69dbb6f

# Reset to HEAD
git reset --hard HEAD

# Reset all changes, including staged files
git reset --hard

# Continue a rebase
git rebase --continue
```

## Git Fetch and Rebase

```bash
# Fetch changes from the remote repository
git fetch origin

# Rebase the current branch with remote changes
git rebase
```

## Other Git Commands

```bash
# List all files and directories in the .git directory
ls .git

# Fetch changes from the remote repository and prune deleted branches
git fetch --prune --tags --progress

# Commit changes with a message
git commit -m "Your message"

# Amend the last commit
git commit --amend

# Add and commit changes with a message
git commit -a -amend -m "Your message"

# Add and commit changes
git commit -am

# Force-push changes to the remote repository
git push --force-with-lease

# Discard changes in a file
git checkout -- [filename]

# Create and switch to a new branch
git checkout -b <branch_name>

# Checkout an existing remote branch
git checkout -t 'remote branch name'

# List all branches sorted by commit date
git branch --all --sort=-committerdate

# Restore changes in a file
git restore -- [filename]

# Unstage a staged file
git restore --staged [filename]

# View changes between staged and last commit
git diff --staged [filename]

# Open a visual diff tool for changes in a file
git difftool [filename]

# View changes between two commits
git diff [COMMIT_ID] [FILENAME] [OTHER_COMMIT_ID]

# View changes between a local branch and a remote branch
git diff [local_branch] [remote_branch_name]

# Merge changes from a target branch with a commit message
git merge [target_branch_name] -m "Your message"

# View only the names of files changed between branches
git diff --name-only US120006_LoggingWithAppInsights origin/master

# Remove bin and obj directories recursively
Get-ChildItem .\ -include bin,obj -Recurse | foreach { remove-item $_.fullname -Force -Recurse }
```

## Git Branch and Pull Commands

```bash
# List all branches
git branch -a

# Delete a branch
git branch -d <branch_name>

# Pull changes from a specific branch and commit hash
git pull [branch name] <commit_hash>
```

## Git Switch Commands

```bash
# Checkout a remote branch
git switch -t 'origin/branch_name'

# Create and switch to a new branch
git switch -c <new-branch>
```

## Git Rebase Commands

```bash
# Abort an ongoing rebase
git rebase --abort

# Continue an ongoing rebase
git rebase --continue

# Perform an interactive rebase
git rebase --interactive

# Rebase the current branch with changes from another branch
git rebase [source-branch-name]

# Pull with rebase
git pull --rebase [branch name]
```

## Git Stash Commands

```bash
# Save uncommitted changes to the stash with a message
git stash save [message]

# Apply changes from the stash
git stash apply

# List all stashes
git stash list

# Drop a specific stash
git stash drop [stash@index]

# Stash untracked files as well
git stash -u

# Stash changes with pathspec
git stash -p

# Show changes in a specific stash
git stash show [stash@index]

# Apply changes from a specific stash
git stash apply [stash@index]

# Clear all stashes
git stash clear

# Create a new branch from a stash
git stash branch [branch name]
```

### Ignore specific files.

```
git update-index --assume-unchanged <file>
```
git update-index --assume-unchanged is a Git command that allows you to temporarily ignore changes to a specific file, making Git think that the file hasn't been modified, even though it may have been.
http://source.kohlerville.com/2009/02/untrack-files-in-git/

##### Find all the changes done by specific user in last 6 month (Time period)
```bash
git log --author="John.Doe@abc.io" --name-only --pretty=format: --since="6 months ago" | sort -u
```

## How to Delete the Most Recent Commit

```bash
# Delete the most recent commit, preserving changes
git reset --soft HEAD~1

# Delete the most recent commit and remove changes
git reset --hard HEAD~1
```

* git tag [tagName]
* git tag --list
* git tag --delete [tagName]
* git tag -a [annotation]
* git difftool [tag_name_1] [tag_name_2]
* git tag -a [annotation] [commit_id]
* git tag -a [tagName] -f [new_commit_id] 
* git push origin master [tag_name]
* git push origin master --tags 
* git push origin :[tagName]
* git push --force-with-lease
####

# How to Revert changes:
	* git fetch --prune --tags –progress
	#####	Check out the branch that contains the commit that we want to revert. 
	* If Branch does not exists
	``` git switch -t <<origin/branch_name>> ```
	* If branch exists (Switch to that branch and apply latest changes from remote that was fetched earlier using rebase)
```
	git switch <<branch_name>>
	git rebase
```
	* Create a new branch off of the branch that contains commits that we need to revert 
	``` git switch -c <<NewBranchName_Revert_Changes>>
	* Find out the commit # that you want to revert
``
	git revert <<Commit_Number>>
``
	* Push changes to remote
`` 
 git push --set-upstream origin <<NewBranchName_Revert_Changes>> 
``
	* Create a PR that targets the branch that contains commit that we have to remove
	* In the PR , Source will be <<NewBranchName_Revert_Changes>> and destination will be <<branch_name>>

###
Zip modified files to C:\ Drive
zip "C:\MyFolder_$(git branch --show-current)_$((Get-Date).ToString('yyyyMMdd_HHmmss')).zip" $(git diff --name-only --cached --diff-filter=AM)
####

##### Rebase vs merge  
Short Version
Merge takes all the changes in one branch and merges them into another branch in one commit.
Rebase says  use another branch as the new base .

So when do you use either one?

Merge
Let's say you have created a branch for the purpose of developing a single feature. When you want to bring those changes back to master, you probably want merge (you don't care about maintaining all of the interim commits).

Rebase
A second scenario would be if you started doing some development and then another developer made an unrelated change. You probably want to pull and then rebase to base your changes from the current version from the repository.Short Version
Merge takes all the changes in one branch and merges them into another branch in one commit.
Rebase says I want the point at which I branched to move to a new starting point
So when do you use either one?

Merge
Let's say you have created a branch for the purpose of developing a single feature. When you want to bring those changes back to master, you probably want merge (you don't care about maintaining all of the interim commits).

Rebase
A second scenario would be if you started doing some development and then another developer made an unrelated change. You probably want to pull and then rebase to base your changes from the current version from the repository.

#####
git ls-files

$ git init

> git config --global alias.hist "log --all --graph --decorate --oneline"
shortcut
	q: 
	esc:
	ctrl + r
	https://docs.microsoft.com/en-us/powershell/module/psreadline/get-psreadlinekeyhandler?view=powershell-7.1
	
>> git push origin remote-demo-branch: (git push <repo name> <branch name>)
	• Origin refers to the github copy of our repository (remote Server origin - remote repo where sd cloned our directory from). "origin" is a shorthand name for the remote repository that a project was originally cloned from. 
	• remote-demo-branch is the name of the remote branch where we want to push your changes to


The staging area is like a rough draft space, it's where you can git add the version of a file or multiple files that you want to save in your next commit (in other words in the next version of your project).Mar 12, 2018

HEAD Pointer in Git
Git maintains a variable for referencing, called HEAD. The HEAD points out the last commit in the current checkout branch.  We can imagine HEAD as the “current committed branch”


What is tracked files in Git?

Git views untracked and modified files similarly. Untracked means that the file is new to your Git project. Modified means that the file has been seen before, but has been changed, so is not ready to be snapshotted by Git. Modification of a file occurs in your working directory.



2) Staged and Staging Area
When a file becomes staged, it's taken into the staging area. This is where Git is able to take a snapshot of it and store its current state to your local repository. This area is also known as the Index.
3) Committed and the Git Directory
Committed means that Git has officially taken a snapshot of the files in the staging area, and stored a unique index in the Git directory. The terms snapshotted and committed are very similar. The significance of being committed is that you can now revert back to this project's current state at any time in the future.

From <https://snipcademy.com/git-fundamentals> 


### Configuration of mergetool
* git config --global merge.tool bc4
* git config --global mergetool.bc4.path "C:/Program Files/Beyond Compare 4/BCompare.exe"
* git config --global diff.tool bc4
* git config --global difftool.bc4.path "C:/Program Files/Beyond Compare 4/BCompare.exe"
* git config --global difftool.prompt false
* git config --global mergetool.prompt false
![image](https://user-images.githubusercontent.com/61636643/150656490-8da2f9d6-7f33-4960-b110-3bab00824f17.png)
