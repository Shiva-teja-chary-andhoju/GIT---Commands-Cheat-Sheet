# Git Commands Cheat Sheet
 
> Open working directory in Visual Studio and write below commands in command prompt.
 
## Getting Help
 
Check Git version:
```bash
git --version
```
 
### Help Commands
 
Displays a synopsis of commonly used Git commands:
```bash
git help
```
 
Prints all available Git commands on the standard output:
```bash
git help -a
git help --all
```
 
Prints a list of useful Git guides and conceptual documentation:
```bash
git help -g
git help --guides
```
 
Shows the manual page (manpage) for a specific Git command:
```bash
git help <command>
git help remote
```
 
Alternative way to show manual page:
```bash
git <command> --help
git remote --help
```
 
Provides a quick summary of the options and usage for a specific command:
```bash
git <command> -h
git remote -h
```
 
## Configuration
 
### Setting Up User Information
 
Set your email:
```bash
git config --global user.email "youremail@domain.com"
git config --global user.email "andhoju.shivatejachary@cbre.com"
```
 
Set your username:
```bash
git config --global user.name "Your GitHub Username"
git config --global user.name "ShivatejacharyAndhoju"
```
 
### View Configuration
 
Display all global Git configuration settings:
```bash
git config --global --list
```
 
**Output:**
- user.email=andhoju.shivatejachary@cbre.com
- user.name=ShivatejacharyAndhoju
 
### Changing Git Origin Login Credentials
 
Update email and username:
```bash
git config --global user.email "andhojushiva1234@gmail.com"
git config --global user.name "Shiva-teja-chary-andhoju"
git config --global --list
```
 
## Remote Repository Management
 
### Adding a Remote Repository
 
Add a new remote repository reference (usually named `origin`). This tells Git where to push/pull code from. This sets up a remote named origin pointing to your GitHub repo.
 
```bash
git remote add origin https://<new-username>@github.com/<new-username>/<repo>.git
git remote add origin https://github.com/Shiva-teja-chary-andhoju/GIT---Commands-Cheat-Sheet.git
```
 
### Updating Remote URL
 
Change the URL of an existing remote:
```bash
git remote set-url origin https://github.com/newuser/newrepo.git
git remote set-url origin https://github.com/Shiva-teja-chary-andhoju/Adventure-Works-Report-PowerBI.git
```
 
### Viewing Remote Repositories
 
List remote repositories (usually origin) hosted elsewhere (like on GitHub, GitLab, Bitbucket, etc.):
```bash
git remote
```
 
**Output:** `origin`
 
Displays the remote names and their URLs (for fetch and push):
```bash
git remote -v
```
 
**Output:**
- origin  https://github.com/Shiva-teja-chary-andhoju/GIT---Commands-Cheat-Sheet.git (fetch)
- origin  https://github.com/Shiva-teja-chary-andhoju/GIT---Commands-Cheat-Sheet.git (push)
 
### Show Remote Details
 
Display detailed information about a remote:
```bash
git remote show origin
```
 
**Output:**
```
* remote origin
  Fetch URL: https://github.com/Shiva-teja-chary-andhoju/GIT---Commands-Cheat-Sheet.git
  Push  URL: https://github.com/Shiva-teja-chary-andhoju/GIT---Commands-Cheat-Sheet.git
  HEAD branch: main
  Remote branch:
    main new (next fetch will store in remotes/origin)
```
 
### Fetching and Pulling
 
Downloads new data (commits, branches, tags) from the remote but does not merge it into your working branch. Updates your local copy of the remote branches. Lets you review changes before merging.
```bash
git fetch origin
```
 
Merges the fetched changes from origin/main into your current local branch:
```bash
git merge origin/main
```
 
Downloads data and merges it into your current branch. Equivalent to `git fetch` + `git merge`. Automatically updates your working directory with remote changes.
```bash
git pull origin main
```
 
### Removing and Renaming Remotes
 
Removes a remote reference. This deletes the link to the remote repository named origin:
```bash
git remote remove origin
```
 
Rename a remote:
```bash
git remote rename oldname newname
```
 
## Cloning a Repository
 
Downloads the entire repository (code, history, branches). Creates a local copy of a remote repository in the current folder you are in. Also initializes a new Git repo on that local repo (`.git`).
 
```bash
git clone https://github.com/user/repo.git
git clone https://github.com/Shiva-teja-chary-andhoju/Adventure-Works-Report-PowerBI.git
```
 
## Initializing a Repository
 
Initialize git repository in working directory:
```bash
git init
```
 
## Checking Status
 
Shows what changes have been made, what is staged for the next commit, and what files are not being tracked by Git:
```bash
git status
```
 
## Staging Files
 
Add all files to staging area:
```bash
git add .
```
 
Add specific file:
```bash
git add test.sql
git add test
```
 
Add multiple files:
```bash
git add test1 test2 test3
```
 
Add all files with specific extension:
```bash
git add *.sql
```
 
## Committing Changes
 
Commit changes to present branch:
```bash
git commit -m "initial commit"
```
 
## Viewing Commit History
 
Shows the commit history of your repository:
```bash
git log
```
 
Shows condensed commit history:
```bash
git log --oneline
```
 
## Branch Management
 
Create new branch:
```bash
git branch new_branch
```
 
Lists all branches:
```bash
git branch
```
 
Switch HEAD to a branch (modern replacement for `git checkout`):
```bash
git switch new_branch
```
 
## Checkout Command
 
`git checkout` is a multi-purpose Git command that can be used for:
 
Switch HEAD to a branch:
```bash
git checkout new_branch
```
 
Switch HEAD to a commit (detached HEAD):
```bash
git checkout a1b2c3d4
```
 
Restore the file to its last committed state from the current branch. Discards changes in test.sql in your working directory. It does not affect commit history.
```bash
git checkout test.sql
```
 
## Restore Command
 
Modern replacement for `git checkout` when restoring files. Discard changes in a file in your working directory or staging area. It does not affect commit history.
 
```bash
git restore test.sql
```
 
## Reset Command
 
Unstages the file test.sql. It does not undo the last commit. The file's contents remain unchanged in your working directory:
```bash
git reset test.sql
```
 
Undo the last commit and removes contents as well:
```bash
git reset --hard <commit-hash>
git reset --hard a3f5e9d
git reset --hard HEAD~1
```
 
### Reset Modes
 
**Soft Reset** - Moves HEAD to the specified commit. Keeps all changes in the staging area (index) and working directory. Use case: Undo a commit but keep the changes staged for a new commit.
```bash
git reset --soft <commit>
```
 
**Mixed Reset** (default) - Undo the last commit, keep changes in files, but unstage them:
```bash
git reset --mixed <commit>
git reset test.sql
```
 
**Hard Reset** - Undo the last commit and erase all changes:
```bash
git reset --hard <commit>
```
 
### Understanding HEAD Notation
 
Imagine your commit history looks like this:
 
```
a3f5e9d (HEAD) - "Fix login bug"
b2d4c8a        - "Add login feature"
c1a2b3c        - "Initial commit"
```
 
- `HEAD` → points to a3f5e9d
- `HEAD~1` → points to b2d4c8a
- `HEAD~2` → points to c1a2b3
 
## Revert Command
 
Does not delete the original commit. Adds a new commit that undoes the changes. It's safe for shared/public branches because it preserves history.
 
```bash
git revert <commit-hash>
```
 
## Stashing Changes
 
If you want to keep your changes, consider stashing them first.
 
Saves unstaged and staged changes. Cleans your working directory:
```bash
git stash
```
 
Adds a stash with a custom message:
```bash
git stash push -m "Save changes to test.sql"
```
 
### Viewing Stashes
 
Shows all saved stashes:
```bash
git stash list
```
 
**Output:**
```
stash@{0}: WIP on main: abc123 Fix bug
stash@{1}: WIP on main: def456 Add feature
```
 
Shows what changes are in the most recent stash:
```bash
git stash show
```
 
To see full diffs:
```bash
git stash show -p
```
 
### Applying Stashes
 
Applies the most recent stash without removing it:
```bash
git stash apply
```
 
To apply a specific stash without removing it:
```bash
git stash apply stash@{1}
```
 
Applies the most recent stash and removes it from the stash list:
```bash
git stash pop
```
 
To pop a specific stash:
```bash
git stash pop stash@{1}
```
 
### Deleting Stashes
 
Deletes all stashes:
```bash
git stash clear
```
 
Deletes a specific stash:
```bash
git stash drop stash@{0}
```
 
## Pushing Changes
 
Upload your local commits to a remote repository, such as GitHub:
```bash
git push origin main
```
 
### Setting Upstream Branch
 
"Upstream" refers to the remote branch that your local branch is tracking — typically the branch you pull changes from and push changes to.
 
The `-u` (or `--set-upstream`) flag tells Git: "Track the remote branch origin/main as the upstream for my local main branch."
 
```bash
git push -u origin main
```
 
This means future `git pull` or `git push` commands can be run without specifying the remote and branch:
 
```bash
git pull
git push
```
 
### Viewing Upstream Tracking
 
To see what upstream branch your current branch is tracking:
```bash
git branch -vv
```
 
## Viewing Differences
 
Shows changes in your working directory that haven't been staged yet:
```bash
git diff
```
 
Shows changes that have been staged with `git add` but not yet committed:
```bash
git diff --cached
git diff --staged
```
 
Shows the difference between two commits:
```bash
git diff commit1 commit2
```
 
Shows what's different between two branches:
```bash
git diff branch1 branch2
```
 
## Key Concepts
 
- **Branch** is a label
- **HEAD** is a pointer
 
---
 
*Created by Shiva Teja Chary Andhoju*
