* **What is cherry-pick command?**
   Cherry picking in Git is a way to select and apply a specific commit (or a range of commits) from one branch to another.
   
* **Why we have to use cherry-pick command?**
   There are several reasons why you may want to use cherry picking in Git:
  - **Backporting changes:** If you have made a change to a file on a branch that is not the main development branch, but you want that change to be included in the main branch as well, you can use cherry picking to apply that change to the main branch.
  - **Fixing bugs:** If you have identified a bug in the code on one branch, and you have already fixed that bug on another branch, you can use cherry picking to apply that fix to the branch with the bug.
  - **Reverting changes:** If a commit has been made that introduces a problem, you may want to revert that commit. You can use cherry picking to apply the changes from a previous commit that undoes the problematic changes.
  - **Applying changes selectively:** If a commit contains several changes, and you only want to apply some of those changes to another branch, you can use cherry picking to select only the changes you want to apply.
  - **Cherry picking:** is a powerful tool that can help you manage changes between branches in Git. However, it is important to use it carefully, as it can also introduce conflicts or break the code if used incorrectly.

* **How to apply selective changes using cherry-pick Command?**
    To apply changes selectively using cherry pick in Git, you can specify the commit(s) and the specific files or lines you want to apply. Here's an example of how to do this:    
   - Identify the commit that contains the changes you want to apply. You can use `git log` to find the commit hash or commit message that identifies the commit.
     
   - Use `git cherry-pick` with the `-n` option to apply the changes, but without automatically committing the changes. For example:
   	`git cherry-pick -n <commit-hash>`

   - Use `git add` to stage the specific changes you want to apply. For example, if you only want to apply changes to a specific file, you can use:
     	`git add path/to/file`

   - If you only want to apply changes to specific lines in a file, you can use:
   	`git add -p path/to/file`
	This will open an interactive prompt where you can choose which changes to stage.
	
   - Use `git commit` to create a new commit with the selected changes. Be sure to include a descriptive commit message that explains what changes were made. For example:
   	`git commit -m "Apply changes to path/to/file from commit <commit-hash>"`
	
	This commit will only include the specific changes you selected, and not any other changes that were made in the original commit.
	
	By using the `n`option with cherry-pick and selectively staging the changes, you can choose exactly which changes to apply from a commit, instead of applying all changes in the commit. This can be useful in situations where you only want to apply a specific feature or bug fix, rather than all changes in a particular commit.


* **How to revert changes using cherry-pick Command?**
  To revert changes using `git cherry-pick`, you would essentially be using the `git revert` command in combination with cherry-picking. The steps to do this are as follows:

   - Identify the commit that introduced the changes you want to revert. You can use `git log` to see a list of commits and find the one you want.

   - Create a new branch for the revert, to avoid modifying any existing branches. You can use the `git branch` command to create a new branch, or the `git checkout -b` command to create a new branch and switch to it at the same time. For example:
     `git checkout -b revert-feature-branch`

   - Use `git cherry-pick` to apply the changes from the commit you want to revert, but with the -n flag to prevent it from automatically committing the changes. This will apply the changes to the working directory, but leave them staged so you can modify them before committing. For example:
   `git cherry-pick -n <commit-hash>`

   - Use git reset to unstage the changes. For example:
     `git reset`
     This step is optional, depending on your preference for how to handle the changes that were cherry-picked. If you skip this step, the changes that were cherry-picked will still be staged and ready for commit. However, if you do not want to commit those changes as-is, you will need to modify them before committing.
     If you do use git reset as described above, the changes will be unstaged and you can modify them as needed before committing.

   - Use `git add` to stage the modified changes.

   - Use `git commit` to create a new commit that reverts the original changes. You should include a message that explains that this commit is a revert of the original commit. For example:
     `git commit -m "Revert changes introduced by commit <commit-hash>"`

   - Push the new branch and the revert commit to the remote repository. For example:
     `git push origin revert-feature-branch`
   This will create a new branch with a revert of the original changes. You can then merge this branch into any other branches as needed, or discard it if you no longer need it.





