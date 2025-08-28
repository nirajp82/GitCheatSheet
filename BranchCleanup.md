# Git Branch Cleanup Guide

## Overview
How to clean a feature branch so it contains only your commits. Common scenarios for this cleanup:

* You accidentally pulled in unwanted commits from the base branch.
* Your branch history has diverged from remote.
* You want a clean commit history before merging.

## Branches Example

* Base branch: `master`
* Original feature branch: `my_new_branch`
* Temporary clean branch: `my_new_branch_clean`

## Steps

1. **Commit or stash local changes (if any)**

* If you have uncommitted changes, either commit them:

```bash
git add .
git commit -m "Your commit message"
```

* Or stash them temporarily:

```bash
git stash
```

2. **Switch to base branch and update it**

```bash
git switch master
 git fetch origin
 git rebase origin/master
```

* If you stashed changes, you can pop them now:

```bash
git stash pop
```

3. **Create a clean branch from base**

```bash
git switch -c my_new_branch_clean
```

4. **Cherry-pick all your commits that you would like to keep it in your branch**

```bash
git cherry-pick <first-commit-sha>
git cherry-pick <second-commit-sha>
```

5. **Rename clean branch to original name**

```bash
git branch -D my_new_branch
 git branch -m my_new_branch_clean my_new_branch
```

6. **Force push to remote**

```bash
git push origin my_new_branch --force-with-lease
```

7. **Verify history**

```bash
git fetch origin
git log --oneline --graph --decorate origin/my_new_branch
```
