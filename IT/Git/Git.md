### status
- Files can be `untracked`, `staged` or `commited`
### add
- Stages files (to the staging area/index)
### commit 
- Saves the state of the repository
- `-m` for adding a message
- `--amend`: amends the last commit
### log
- Shows commit history
- `--nopager log -n 10` for displaying without pager and a limited amount of commits
- `--oneline` shows a compact version of the log
- `--graph`
- `--all
- `--parents`
- `--decorate` gives more information about heads, tags, etc
## Trees and Blobs
- Objects that git usesd
- `tree`: directory
- `blob`: file
### cat-file
- Provide information about repository objects
## Config
- More specific configs will override less specific ones
### set
- `git config set --global user.name "Arthur"`
    - `--local` or omission stores the config for just the current repository
    - `section.key` could be any kind of combination to store the value for it
    - local config stays in `.git/config`, global in `~/.gitconfig`
### unset
- `git config unset <key>`
    - `unset --all <key>` for purging all instances of a key, git allows duplicate keys
### remove-section
- `git config remove-section <section>`
## Branch
- Under the hood it is just a named pointer to a specific commit
- `git branch -d old_branch` deletes branch
### switch
- `git switch -c my_new_branch`
    - Creates a new branch and switches to it, based on the current commit
    - `<commit_hash>` will cause the branch to be created from a specified commit
- `git checkout` is the older version of `switch`, which is less intuitive and user-friendly
## Merging
- `git merge other_branch`
- **Fast forward** merge is a merge with **no merge commit**, because both branches have the same history
## Rebase
