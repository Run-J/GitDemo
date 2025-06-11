
# Git Common Commands

A quick reference for essential Git Operations, with explanations. <br>
Author: Run-J



## Basic Setup

```bash
git --version                             # Check installed Git version

git config --list                         # View all Git configuration values
git config --list --show-origin           # Show config file source for each value

git config --global user.name "Run-J"     # Set your Git username (global)
git config --global user.email jirun040403@hotmail.com  # Set your Git email (global)

git remote set-url origin https://github.com/Run-J/GitDemo.git  # Change the remote URL

git update-git-for-windows                # Update Git on Windows
brew upgrade git                          # Update Git on macOS
```



## Core Commands
```bash
git init              # Initialize a local Git repository
git status            # Show current status of working directory and staging area
git remote -v         # Show the current remote repository URLs

git fetch             # Download changes from remote (does not merge)
git pull              # Fetch + merge changes from remote
git merge             # Merge another branch into the current branch

git stash             # Temporarily save uncommitted changes
git stash pop         # Reapply the most recent stash
```




## Branching

```bash
git branch                               # List local branches
git branch -r                            # List remote-tracking branches
git branch bug-FixFileName               # Create a new branch (from current branch)

git checkout -b feat-ChangeToMarkDown    # Create and switch to a new branch
git checkout bug-FixFileName             # Switch to an existing branch
git branch -d bug-FixFileName            # Delete a local branch
```



## Committing
```bash
git add .                                # Stage all changes
git commit                               # Commit staged changes

# Update the most recent commit (e.g. fix a file then rewrite the commit)
git add <file>
git commit --amend -m "Fixed Commit"

# Change only the commit message (no file changes)
git commit --amend -m "Updated commit message"
```



## Undo && Reset
```bash
# Reset local branch to match remote branch exactly / if want to move a commit to a branch
git reset --hard origin/main

# Revert a specific commit (undo the change but keep history) / Undo an Old Commit
git revert <commit-hash>

# Discard changes in a file (revert to last committed version) / Undo Changes to a File
git checkout README.md

# Untrack a file but keep it in working directory
git rm --cached Testing.rj
```



## When Local Repo Gets Messy
```
If your local Git repo becomes messy or unsalvageable:

👉 Just create a new folder and re-clone the repository:
git clone <remote-url>
```



## Basic Process
```bash
# 1. Switch to main branch and sync with remote
git checkout main
git pull

# 2. Create a new feature or bugfix branch
git checkout -b bug-00-branch-name

# 3. Work on your changes
git add .
git commit

# 4. Sync with the latest main branch
git checkout main
git pull
git checkout bug-00-branch-name
git merge main                         # Resolve any conflicts if needed

# 5. Merge your branch back to main
git checkout main
git merge bug-00-branch-name

# 6. Push the updated main branch to remote
git pull                               # Optional safety check
git push

# 7. Delete the feature/bugfix branch locally
git branch -d bug-00-branch-name
```