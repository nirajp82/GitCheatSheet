```sh 
git switch master
```

# Remove target_branch branch on remote
```sh
  git push origin --delete target_branch
  git fetch --prune --tags --progress
```
# Remove local target_branch branch
```sh 
git branch -D target_branch
```

# Recreate the target_branch using Master branch
```sh
  git switch -C target_branch
  git push --set-upstream origin target_branch
```
