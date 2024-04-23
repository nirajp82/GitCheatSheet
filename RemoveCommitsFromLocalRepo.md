If you have committed a file in Git but have not yet pushed it to a remote repository, you can undo the commit using the following steps:

1. **Use `git reset HEAD~1`:** This command will undo your last commit but keep the changes from that commit in your working directory. Replace `1` with the number of commits you want to undo if you have multiple commits.

    ```bash
    git reset HEAD~1
    ```

2. **Check your working directory status:** After running the reset command, your changes will be unstaged. You can use `git status` to see the status of your working directory.

    ```bash
    git status
    ```

3. **Unstage the changes (if needed):** If you want to unstage the changes from the undone commit, you can use `git reset HEAD <file>`.

    ```bash
    git reset HEAD <file>
    ```

4. **Modify the file (if needed):** Make any necessary changes to the file to revert it to the state you want.

5. **Commit the changes:** Once you're satisfied with the changes, commit them again.

    ```bash
    git commit -m "Your commit message"
    ```

6. **Push your changes (if needed):** If you still want to push your changes to a remote repository, use `git push`.

    ```bash
    git push <remote-name> <branch-name>
    ```

By following these steps, you can undo a commit that has not been pushed to a remote repository yet. Make sure to review the changes in your working directory and stage them accordingly before committing again.
