git switch master
# Remove target_branch branch on remote
git push origin --delete target_branch
git fetch --prune --tags --progress
# Remove local target_branch branch
git branch -D target_branch
# Recreate the target_branch using Master branch
git switch -C target_branch
git push --set-upstream origin target_branch
