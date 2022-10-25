Here is a simple way for removing the wrong commit 

1.  git checkout my-pull-request-branch
1.  git rebase -i HEAD~n // where n is the number of last commits you want to include in interactive rebase.
1.  Replace pick with drop for commits you want to discard.
1.  Save and exit.
1.  git push --force-with-lease
