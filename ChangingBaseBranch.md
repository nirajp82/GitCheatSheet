```markdown
# 📘 Git Rebase: Changing Base Branch from a Nested Structure

## 🧩 Scenario

You have the following Git branch hierarchy:

```
master
  └─> Branch1
         └─> Branch2
    ```

- You've created `Branch1` from `master`.
- Then you created `Branch2` from `Branch1`.
- You’ve already merged `Branch1` back into `master`.
- Now, you want to **rebase `Branch2` onto `master`** instead of having it based on `Branch1`.


## ✅ Goal

Rebase `Branch2` so that it looks like it was branched directly from `master`, **not `Branch1`**, and keep commit history clean.

---

## 🔧 Step-by-Step Guide

1. **Switch to your working branch**:
```bash
   git switch Branch2
```

2. **Rebase `Branch2` onto `master`, skipping `Branch1`**:
   ```bash
   git rebase --onto master Branch1 Branch2
   ```

   ### What this does:
   - It takes the commits that exist in `Branch2` but **not in `Branch1`**.
   - Then it **re-applies those commits on top of `master`**.
   - The result: `Branch2` is now based off `master`.

## 🔐 Pushing the Rebased Branch

Since you've rewritten commit history with `rebase`, you'll need to update the remote version of `Branch2`.

Instead of using the risky `--force`, prefer the **safer** alternative:

### ✅ Safer Push:
```bash
git push --force-with-lease
```

### Why use `--force-with-lease`?
- It ensures you're not accidentally overwriting someone else's changes.
- It only pushes if the remote branch is exactly as you last saw it.

## ⚠️ Handling Merge Conflicts

If you hit any conflicts during rebase:
- Git will pause and let you resolve them.
- Use:
  ```bash
  git status
  ```
  to see which files need attention.

After resolving:
```bash
git add <resolved-files>
git rebase --continue
```

Or, to abort the rebase at any time:
```bash
git rebase --abort
```

