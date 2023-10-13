* Get Latest version of source branch.  it's a good practice to fetch the latest changes from the remote repository. This ensures that you have the most recent updates from the origin/master branch.
  ```sh
  git switch master
  git fetch --tags --progress --prune
  git rebase 
  ```
* Switch to the target branch that contains the commit and Use the git restore command to restore the specific file from origin/master. Make sure to specify the correct file path:
```sh
  git switch target_branch
  git restore --source origin/master path/to/file
```
* Commit the changes
  ```git commit -m 'commit message'```
* Push the changes
  ```git push --force-with-lease```
