git show HEAD
git checkout HEAD(or --) filename : rolls back filename to HEAD (-- separate paths from revisions)
git reset HEAD filename : resets filename in the staging area to head, 
                          doesn't discard changes in the working directory
git reset commitHASH : resets HEAD to the commit specified by the first 7 characters of their hash
git stash : store work in a hidden directory when commits are not appropriate
git stash pop : restore saved stash to continue working on it
git log --oneline : logs in oneline with the 7 hash characters
git log -S "keyword" : search commits with keyword
git log --oneline --graph : shows graph to see interactions with features and other commits
git commit --amend (--no-edit) : updates the previous commit with the new staged changes instead of 
                                 making a new commit. --no-edit uses the same commit message
git config --global alias.co "checkout" : makes an alias, enabling "git co branch"
git status
git remote add remoteName remoteAdress
git push : -u sets upstream for the current branch, allowing better tracking and not needing to specify remote branch every time