### Stage and commit changes in one step
git commit -am "<changes made>"

git log
git log -p  # detailed log
git log --oneline
git log --graph
git log --grep='removes' -i  # search for specific commit message

git show defaf2c8a1b1ddeae76efea0b2a135f52cf20fa4  # shows details of this commit

git mv currrent_filename new_filename  # rename file without using delete `current_filename` and `git add new_filename` 

git checkout afd0005  # partial hash of the commit we want to check
git checkout main  # return to the main branch / last commit

git restore .  # !!! restores all files to the last commit, ALL changes are lost !!!
git restore --staged filename OR filepath (folder/filename)  # restores file to last commit status

git diff  # see changes, whats added vs whats removed
git pull --all && clear  # git pull --all = fetches and merges from all remote repositories (if more than one)  && clears the screen

git revert 1d4a8cb # reverts specific commit - must follow with git push to update remote repository

### Checks available branches
git branch
### Creates a new branch
git branch <branch_name>
### Branch naming: type of change/change number/short name
git checkout -b bug/123/menu-issue
git checkout -b feat/124/new-email-feature
### Switches to branch <branch_name>
git checkout <branch_name
### Create and switch to a new branch in one step
git checkout -b <branch_name>
### Pushes/set-ups the local branch in the remote repository
git push --set-upstream origin <branch_name>

### Creates and merges a pull request using GitHub
1. Pull requests
2. New pull request
3. Select branches to merge (main and <branch_name>)
4. See changes/conflicts
5. Create pull request - use a descriptive message
6. Ask a validator to review your code
7. Optional: delete the branch <branch_name> after it has been merged into main
git branch -d your-branch-name

### Checks if the local branch was merged into main:
git pull
git merge-base --is-ancestor <branch_name> main && echo "Merged" || echo "Not merged"

### Solving a merge conflict (default behavior)
git config pull.rebase false
... followed by:
git pull  # accept current change (local) or incoming change (remote) - resolve merge conflict
git add .
git commit -m "<this is a commit message>"
git push

---

**Note:** Reverts are risky - inform team in a collaborative enviroenment. Preferably to fix the issue than to revert AND if possible to perform the revert on a feature branch, test it and then merge it into the main branch
add `.gitkeep` file to empty folders you want git to track
controls which files are shown or hidden in our local git repository by edititng this JSON object:
  "files.exclude": {
    "**/.git": false
  }
... and adding it to either one of opions 1 or 2:
1. CTRL + SHIFT + P (VSC) && User Settings (JSON)
2. edit .vscode/settings.json
