### How to Create a Revert PR

#### 1. Fetch the Latest Changes
First, fetch the latest changes from the remote repository, including tags.

```bash
git fetch --prune --tags --progress
```

#### 2. Check Out the Target Branch
Switch to the branch that contains the commit you want to revert. If you want to revert a commit from the `dev` branch, switch to `dev` and apply the latest changes using rebase.

```bash
git switch dev
git rebase
```

#### 3. Create a New Branch for the Revert
Create a new branch off of the target branch (e.g., `dev`) to revert the specific commit.

```bash
git switch -c <NewBranchName_Revert_Changes>
```

#### 4. Revert the Commit
Find the commit hash of the commit you want to revert, and then revert it.

```bash
git revert <Commit_Number>
```

#### 5. Push the Revert Branch to Remote
Push the new branch with the reverted commit to the remote repository.

```bash
git push --set-upstream origin <NewBranchName_Revert_Changes>
```

#### 6. Create a Pull Request
Create a Pull Request (PR) with the following details:
- **Source Branch:** `<NewBranchName_Revert_Changes>`
- **Destination Branch:** The branch that originally contained the commit you are reverting (e.g., `dev`).

This PR will be ready to be merged if you need to revert the changes.

---

This step-by-step guide should help you create a revert PR efficiently.
