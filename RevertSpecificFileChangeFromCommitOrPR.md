* Find the Commit ID from where you want to revert the changes.
* Get Latest version of source branch
  ```sh
  git switch master
  git fetch --tags --progress --prune
  git rebase 
  ```
* Switch to the target branch that contains the commit
```sh
  git switch target_branch
  git restore --source origin/master path/to/file
```
* Commit the changes
  ```git commit -m 'commit message'```
* Push the changes
  ```git push --force-with-lease```
