# Git Commands Guide for Software Engineers

A comprehensive reference for essential Git commands you'll use in your development workflow.

---

## Table of Contents
1. [Initial Setup](#initial-setup)
2. [Repository Basics](#repository-basics)
3. [Branching](#branching)
4. [Staging & Committing](#staging--committing)
5. [Pushing & Pulling](#pushing--pulling)
6. [Merging](#merging)
7. [Viewing History](#viewing-history)
8. [Undoing Changes](#undoing-changes)
9. [Stashing](#stashing)
10. [Rebasing](#rebasing)
11. [Tagging](#tagging)
12. [Remote Management](#remote-management)

---

## Initial Setup

### Configure Git Identity
```bash
git config --global user.name "aquibgitt"
git config --global user.email "aquibhussain53@gmail.com"
```

### Check Configuration
```bash
git config --global user.name
git config --global user.email
git config --list
```

### Set Default Editor
```bash
git config --global core.editor "code"
```

---

## Repository Basics

### Create a New Repository
```bash
git init                    # Initialize a new Git repository locally
```

### Clone an Existing Repository
```bash
git clone <repository-url>  # Clone a remote repository
git clone <url> <directory> # Clone into a specific directory
```

### Check Repository Status
```bash
git status                  # Show current branch and uncommitted changes
git status --short          # Compact version
```

---

## Branching

### View Branches
```bash
git branch                  # List local branches
git branch -a               # List all branches (local + remote)
git branch -v               # Show branches with commit info
```

### Create a Branch
```bash
git branch <branch-name>    # Create a new branch (doesn't switch)
git checkout -b <branch>    # Create and switch to new branch
git switch -c <branch>      # Modern alternative to checkout -b
```

### Switch Between Branches
```bash
git checkout <branch-name>  # Switch to existing branch
git switch <branch-name>    # Modern alternative to checkout
```

### Delete a Branch
```bash
git branch -d <branch-name> # Delete local branch (safe - checks for merge)
git branch -D <branch-name> # Force delete local branch
git push origin --delete <branch-name> # Delete remote branch
```

### Rename a Branch
```bash
git branch -m <old-name> <new-name> # Rename local branch
git push origin -u <new-name>       # Push renamed branch to remote
git push origin --delete <old-name> # Delete old branch from remote
```

---

## Staging & Committing

### Stage Changes
```bash
git add <file>              # Stage specific file
git add .                   # Stage all changes
git add *.js                # Stage all .js files
git add -A                  # Stage all changes (deleted, modified, new)
```

### Unstage Changes
```bash
git restore --staged <file> # Unstage a file
git reset HEAD <file>       # Alternative unstage method
```

### Commit Changes
```bash
git commit -m "message"     # Commit with message
git commit -am "message"    # Stage and commit tracked files
git commit --amend          # Modify the last commit
git commit --amend --no-edit # Amend without changing message
```

### View Staged Changes
```bash
git diff                    # Show unstaged changes
git diff --staged           # Show staged changes
git diff <branch1> <branch2> # Compare branches
```

---

## Pushing & Pulling

### Push to Remote
```bash
git push                    # Push current branch to remote
git push origin <branch>    # Push specific branch to origin
git push -u origin <branch> # Push and set upstream (-u for first push)
git push --all              # Push all branches
git push --tags             # Push all tags
```

### Pull from Remote
```bash
git pull                    # Fetch and merge remote changes
git pull --rebase           # Fetch and rebase instead of merge
git fetch                   # Only fetch (don't merge)
```

### Push with Token/PAT
```bash
git push https://<token>@github.com/<user>/<repo>.git <branch>
```

---

## Merging

### Merge Branches
```bash
git merge <branch-name>     # Merge branch into current branch
git merge --no-ff <branch>  # Merge and create merge commit
git merge --squash <branch> # Squash commits before merging
```

### Handle Merge Conflicts
```bash
git status                  # See which files have conflicts
# Edit conflicted files manually, then:
git add <resolved-file>
git commit -m "Resolve merge conflict"
```

### Abort Merge
```bash
git merge --abort           # Cancel ongoing merge
```

---

## Viewing History

### View Commit Log
```bash
git log                     # Show full commit history
git log --oneline           # Compact one-line format
git log --graph --all --oneline --decorate # Visual branch graph
git log -5                  # Show last 5 commits
git log -p                  # Show changes in each commit
git log --author="name"     # Filter commits by author
git log --since="2 weeks ago" # Show commits from specific time
```

### View Specific Commit
```bash
git show <commit-hash>      # Show specific commit details
git show <branch-name>      # Show latest commit of branch
```

### Compare Versions
```bash
git diff <commit1> <commit2> # Compare two commits
git log <file>              # Show history of specific file
git blame <file>            # Show who changed each line
```

---

## Undoing Changes

### Discard Changes
```bash
git checkout -- <file>      # Discard changes in working directory
git restore <file>          # Modern alternative
git restore --staged <file> # Unstage file
```

### Undo Commits
```bash
git revert <commit-hash>    # Create new commit that undoes changes
git reset --soft HEAD~1     # Undo last commit, keep changes staged
git reset --mixed HEAD~1    # Undo last commit, keep changes unstaged
git reset --hard HEAD~1     # Undo last commit, discard changes
```

### Revert to Previous Version
```bash
git checkout <commit-hash> -- <file> # Restore file from specific commit
git reset --hard <commit-hash>       # Go back to specific commit
```

---

## Stashing

### Save Work Temporarily
```bash
git stash                   # Stash current changes
git stash save "message"    # Stash with descriptive message
git stash list              # Show all stashes
git stash pop               # Apply and delete last stash
git stash apply             # Apply last stash (keep it)
git stash apply stash@{n}   # Apply specific stash
git stash drop              # Delete last stash
git stash drop stash@{n}    # Delete specific stash
git stash clear             # Delete all stashes
```

---

## Rebasing

### Rebase Branch
```bash
git rebase <branch-name>    # Rebase current branch onto another
git rebase -i HEAD~3        # Interactive rebase last 3 commits
git rebase --continue       # Continue after resolving conflicts
git rebase --abort          # Cancel rebase
```

### Interactive Rebase
```bash
git rebase -i HEAD~<number> # Squash, edit, or reorder commits
# Commands in interactive mode:
# pick   = use commit
# reword = use commit but edit message
# squash = use commit but meld into previous
# fixup  = like squash but discard commit message
# drop   = remove commit
```

---

## Tagging

### Create Tags
```bash
git tag <tag-name>                    # Create lightweight tag
git tag -a <tag-name> -m "message"    # Create annotated tag
git tag -a v1.0.0 -m "Version 1.0.0" # Tag for releases
```

### View Tags
```bash
git tag                     # List all tags
git tag -l "v1.*"           # List tags matching pattern
git show <tag-name>         # Show tag details
```

### Push Tags
```bash
git push origin <tag-name>  # Push specific tag
git push origin --tags      # Push all tags
```

### Delete Tags
```bash
git tag -d <tag-name>       # Delete local tag
git push origin --delete <tag-name> # Delete remote tag
```

---

## Remote Management

### View Remotes
```bash
git remote                  # List remote names
git remote -v               # List remotes with URLs
git remote show origin      # Show origin details
```

### Add Remote
```bash
git remote add origin <url> # Add remote repository
git remote add upstream <url> # Add upstream for open source
```

### Remove Remote
```bash
git remote remove <name>    # Remove remote
```

### Rename Remote
```bash
git remote rename <old> <new> # Rename remote
```

### Change Remote URL
```bash
git remote set-url origin <new-url> # Update origin URL
git remote set-url origin https://<token>@github.com/<user>/<repo>.git # Add token to URL
```

### Fetch from Remote
```bash
git fetch origin            # Fetch from origin
git fetch upstream          # Fetch from upstream
git fetch --all             # Fetch from all remotes
```

---

## Common Workflows

### Creating a Feature Branch (Standard Workflow)
```bash
git checkout main
git pull origin main                    # Ensure main is updated
git checkout -b feature/new-feature     # Create feature branch
# Make changes...
git add .
git commit -m "Add new feature"
git push -u origin feature/new-feature  # First push sets upstream
# Create Pull Request on GitHub
```

### Syncing with Upstream (Open Source)
```bash
git remote add upstream <original-repo-url>
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

### Squashing Commits Before Push
```bash
git rebase -i HEAD~3        # Interactive rebase last 3 commits
# Mark commits to squash
git push --force-with-lease # Push after rebase
```

### Recovering Deleted Commits
```bash
git reflog                  # Show all commit references
git checkout <commit-hash>  # Go to specific commit
git checkout -b recovery-branch # Create branch from recovery point
```

---

## Tips & Best Practices

1. **Commit Often**: Make small, logical commits with clear messages
2. **Pull Before Push**: Always pull latest changes before pushing
3. **Use Descriptive Messages**: Write clear, concise commit messages
4. **Branch Naming**: Use `feature/`, `bugfix/`, `hotfix/` prefixes
5. **Review Before Committing**: Use `git diff` to review changes
6. **Keep History Clean**: Use rebase for linear history (if your team agrees)
7. **Use .gitignore**: Don't commit unnecessary files (node_modules, .env, etc.)
8. **Never Force Push to Main**: Use `git push --force-with-lease` carefully
9. **Communicate in PRs**: Use pull requests for code review and discussion
10. **Document Your Workflow**: Different teams may have different conventions

---

## Emergency Commands

```bash
git reflog              # See all actions performed
git bisect              # Find which commit introduced a bug
git cherry-pick <hash>  # Apply specific commit to current branch
git clean -fd           # Remove untracked files and directories
git gc                  # Garbage collection to optimize repository
```

---

## Resources

- [Official Git Documentation](https://git-scm.com/docs)
- [GitHub Guides](https://guides.github.com)
- [Git Cheat Sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf)

---

**Last Updated:** January 17, 2026
