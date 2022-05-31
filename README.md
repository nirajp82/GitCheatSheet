# Git Cheat Sheet
Reference: https://www.interviewbit.com/git-cheat-sheet/
#
https://www.interviewbit.com/git-interview-questions/

git log
git log --graph --decorate --oneline
git reset --hard e5555ca54258113a51c417b2f27edcfac69dbb6f
Git reset HEAD
$ git reset --hard HEAD       (going back to HEAD)
git reset --hard
git rebase continue
Git fetch origin
Git rebase
ls .git

$ git reset --hard HEAD^      (going back to the commit before HEAD)
The “–hard” option is used in order to reset the files of the index (or the staging area) and of the working directory.

git fetch
git -h
git status
git add 
Git add .
git show some_commit_sha1  -- *.cs | git apply -R :---- Revert changes to commit 
git fetch --prune --tags --progress: 
git commit -m "Your message"
git commit --amend
git commit -a -amend -m "Your message"
git commit -am
git push --force-with-lease
Git checkout --[filename]
Git checkout -b: To Create and switch branch 
git checkout -t 'remote branch name' - Checkout existing remote branch
git branch --all --sort=-committerdate
Git restore --[filename]
git restore --staged: To unstage, staged file (Added but not committed yet)
Git diff --staged [filename]
Git difftool [filename]
Git diff [COMMIT_ID] [FILENAME] [OTHER_COMMIT_ID] Git diff [local_branch] [remote_branch_name]
Git diff [local_branch] [other_branch_name]
Git merge [target_branch_name] -m
git diff --name-only US120006_LoggingWithAppInsights origin/master
Get-ChildItem .\ -include bin,obj -Recurse | forech ($_) {​​ remove-item $_.fullname -Force -Recurse }​​

Git branch -a: list all branch
Git branch -d: Delete branch
Git pull [branch name] {{snapshot hash (commit)}}

Git switch -t [branch name] - Checkout Remote Branch 
	FOR EX.  git switch -t 'origin/branch_name'
Git switch -t [branch name]

Git rebase --abort
Git rebase --continue
Git rebase --interactive 
Git rebase [source-branch-name] -- Rebase current branch with source branch changes 
Git pull --rebase [branch name]

Git stash: stash in Git saves uncommitted changes so you can work on other things in your repository without losing your work.
Git stash save [message]
Git stash apply
Git stash list
Git stash drop [stash@index]
Git stash -u
Git stash p
Git stash show [stash@index]
Git stash apply [stash@index] 
Git stash clear
Git stash branch [branch name]

Git tag [tagName]
Git tag --list
Git tag --delete [tagName]
Git tag -a [annotation]
Git difftool [tag_name_1] [tag_name_2]
Git tag -a [annotation] [commit_id]
Git tag -a [tagName] -f [new_commit_id] 
Git push origin master [tag_name]
Git push origin master --tags 
Git push origin :[tagName]
git push --force-with-lease

Rebase vs merge  
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


Configuration of mergetool
git config --global merge.tool bc4
git config --global mergetool.bc4.path "C:/Program Files/Beyond Compare 4/BCompare.exe"
git config --global diff.tool bc4
git config --global difftool.bc4.path "C:/Program Files/Beyond Compare 4/BCompare.exe"
git config --global difftool.prompt false
git config --global mergetool.prompt false
![image](https://user-images.githubusercontent.com/61636643/150656490-8da2f9d6-7f33-4960-b110-3bab00824f17.png)
