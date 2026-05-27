## init
`git init` initializes a new local git repository
## status
- Files can be `untracked`, `staged` or `commited`
## add
- Stages files (to the staging area/index)
## commit 
- Saves the state of the repository
- `-m` for adding a message
- `--amend`: amends the last commit
## log
- Shows commit history
- `git log [<remote>/<branch>]` for logging commits of a remote repo
- `--nopager log -n 10` for displaying without pager and a limited amount of commits
- `--oneline` shows a compact version of the log
- `--graph`
- `--all
- `--parents`
- `--decorate` gives more information about heads, tags, etc
## Trees and Blobs
- Objects that git uses
- `tree`: directory
- `blob`: file
### cat-file
- Provide information about repository objects
## Config
- More specific configs will override less specific ones
### set
`git config set --global user.name "Arthur"`
- `--local` or omission stores the config for just the current repository
- `section.key` could be any kind of combination to store the value for it
- local config stays in `.git/config`, global in `~/.gitconfig`
### unset
`git config unset <key>`
- `unset --all <key>` for purging all instances of a key, git allows duplicate keys
### remove-section
`git config remove-section <section>`
## Branch
- Under the hood it is just a named pointer to a specific commit
`git branch -d old_branch` deletes branch
### switch
`git switch -c my_new_branch`
    - Creates a new branch and switches to it, based on the current commit
    - `<commit_hash>` will cause the branch to be created from a specified commit
- `git checkout` is the older version of `switch`, which is less intuitive and user-friendly
## Merging
`git merge other_branch`
- `[<remote>/<branch>]` other branch can be from a remote
- **Fast forward** merge is a merge with **no merge commit**, because both branches have the same history
## Rebase
Changes the history of a branch to reflect the recent main commits
`git rebase main`
- `git config set --global pull.rebase true` will make it so git rebases by default on pull, rather than merge, keeping a linear history
## Reset
`git reset --soft <commit_hash>`
- `--soft` go to previous commit but keep all changes
    - Committed changes will be uncommitted and staged
    - Uncommitted changes will remain staged or unstaged as before
- `--hard` go to previous commit and match it exactly, discarding local changes
    - Will remove changes from history, deleted for good
## Remote
`git remote add <name> <uri>`
## Fetch
`git fetch`
- Copies contents of the `.git/objects` directory and other bookkeeping information from remote repo into current
## Push
`git push origin main`
- `git push origin <localbranch>:<remotebranch>` push to a remote with a different name
- `git push origin :<remotebranch>` deletes remote branch by pushing and empty branch to it
## Pull
`git pull [<remote>/<branch>]`
## Pull Request
Pull requests on GitHub, with compare as the branch that wants to merge to main
## Gitignore
- A `.gitignore` file only applies to the directory it's in and its subdirectories
- The file will ignore files and directories with the specified names
- `/main.py` will ignore only the file in the root directory, not in any subdirectories. `/src/main.py` will not be ignored
- `!important.txt` negates a pattern
- The order is important, and can override each other