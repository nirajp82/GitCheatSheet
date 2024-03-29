If we have multiple commits, it makes difficult for our team to see our changes. A solution to this problem is combining multiple commits into one. To do so, you should follow the steps below.

go to the future branch that contains multiple commits. >> git switch My_Branch_Name
OPTIONAL Step: In case if you want to merge future branch with latest changes from other branch say "Master" branch pull that master branch.

            >> git pull origin my_master

       Note: git pull origin my_master pulls the my_master branch from the remote called origin into your current branch. It only affects your current branch, not your local dev My_Branch_Name. 

               Your local my_master branch is irrelevant in this. git pull is essentially a combination of git fetch and git merge; it fetches the remote branch then merges it into your current branch. It's a merge like any other; it doesn't do anything magical.

Run git rebase in interactive mode

Suppose that you want to merge the last 3 commits into a single commit. To do that, you should run git rebase in interactive mode (-i) providing the last commit to set the ones that come after it. Here, HEAD is the alias of the very last commit.

>> git rebase -i HEAD~3

Note: HEAD~3 means three commits prior to the HEAD (Git uses zero based index). You can select the appropriate commit by its hash.
Type "squash"

            After the previous step, the editor window will show up offering you to input the command for each commit. All you need to do is replacing "pick" with "squash" or "s" , starting from the second line. For top one keep "pick" as is . (which means you will provide a new comment for this commit in the next step)  Then, save the file.

For ex:  turn following
pick CommitMessageOne
pick CommitMessageTwo
pick CommitMessageThree

                into

pick CommitMessageOne
squash CommitMessageTwo
squash CommitMessageThree

The line you mark up with the keyword 'squash' will be combined with the line directly above! 

![image](https://user-images.githubusercontent.com/61636643/185156924-791e9d90-f163-45d6-99cf-1ffa7b9b2b55.png)


When the next screen comes up, Update a new commit message.

One more editor window will show up to change the resulting commit message. Here, you can find all your commit messages and change them according to your exact needs.

![image](https://user-images.githubusercontent.com/61636643/185156981-7d6ba763-9b5e-4093-ae8c-821347ff252c.png)

Check the git log and make sure there is only one commit

             >> git log --oneline

Pushing changes: 

You should run git push to add a new commit to the remote origin. If you have already pushed your commits, then you should force push them using the git push command with --force flag (suppose, the name of remote is origin, which is by default):

>> git push --force-with-lease
  

Note: --force overwrites the remote branch on the basis of your local branch. It destroys all the pushed changes made by other developers. It refers to the changes that you don't have in your local branch.

--force-with-lease is considered a safer option that will not overwrite the work done on the remote branch in case more commits were attached to it (for instance, by another developer). Moreover, it helps you to avoid overwriting another developer's work by force pushing.
