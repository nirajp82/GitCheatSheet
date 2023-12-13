How to revert changes from branch

* Get latest branch
  *	>> `git fetch --prune --tags –progress`
* Check out the branch that contains the commit from where we want to revert the commit. 
  * If Branch does not exists in local 
  	* >> `git switch -t <<origin/target_branch_name>>`
  * If branch exists (Switch to that branch and apply latest changes from remote that was fetched earlier using rebase)
  	* >> `git switch <<target_branch_name>>`
	* >> `git rebase`
* Create a new branch off of the branch that contains commits that we need to revert
	* >> `git switch -c <<NewBranchName_Revert_Changes>>`
* Find out the commit # that you want to revert
 	* >> `git revert <<Commit_Number>>`
* Push changes to remote
	* >> `git push --set-upstream origin <<NewBranchName_Revert_Changes>>`
* Create a PR that targets the branch that contains commit that we have to remove
* In the PR , Source will be <<NewBranchName_Revert_Changes>> and destination will be <<target_branch_name>>
* Once Approved merge the changes in the  <<target_branch_name>>
