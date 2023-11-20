Adding a specific commit to a target branch. 

### Step 1: Ensure you are on the target branch
* Get latest branch
  *	>> `git fetch --prune --tags –progress`
* Check out the branch that contains the commit that we want to revert. 
  * If Branch does not exists in local 
  	* >> `git switch -t <<origin/target_branch_name>>`
  * If branch exists (Switch to that branch and apply latest changes from remote that was fetched earlier using rebase)
  	* >> `git switch <<target_branch_name>>`
	* >> `git rebase`

### Step 2: Identify the commit you want to add
Use the `git log` command to view the commit history and find the commit hash or commit message of the specific commit you want to add.

```bash
git log
```

### Step 3: Cherry-pick the commit
Use the `git cherry-pick` command to apply the specific commit to the target branch.

```bash
git cherry-pick <commit_hash>
```

Replace `<commit_hash>` with the hash of the commit you want to add.

### Step 4: Resolve conflicts (if any)
If there are conflicts during the cherry-pick process, Git will pause and ask you to resolve them. Open the conflicted files, resolve the conflicts manually, and then continue the cherry-pick process.

```bash
git cherry-pick --continue
```

### Step 5: Commit the changes
After resolving conflicts (if any), commit the changes to the target branch.

```bash
git commit -m "Cherry-pick commit: <commit_message>"
```

Replace `<commit_message>` with the commit message of the original commit.

### Step 6: Push the changes
If the target branch is a remote branch, push the changes to the remote repository.

```bash
git push origin <target_branch>
```

Replace `<target_branch>` with the name of your target branch.

Now, the specific commit should be added to the target branch. Keep in mind that cherry-picking a commit creates a new commit with a different hash, so the commit on the target branch will not be the same as the original commit. If you have any concerns about that, consider using other methods like merging or rebasing, depending on your workflow.
