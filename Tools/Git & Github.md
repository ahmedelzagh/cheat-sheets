# Git & GitHub

### Creating a local repository and pushing it to a remote repository:

```bash
git init #initializing a local repo
git add "file" #adding files to the staging area
git commit -m "your commit" #commiting changes
git branch -M main #forcefully rename the branch to main
git remote add origin repolink.git #associate the local repo with the remote
git push -u origin main #pushing local repo to remote
```

### Git Commands

| Command                               | Desc                                                                                                                                                                                                                                                                            |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `git init`                            | initializes a local repo                                                                                                                                                                                                                                                        |
| `git add "file"`                      | adds a change in the working directory to the staging area                                                                                                                                                                                                                      |
| `git commit -m "initial commit"`      | commit changes, `-m` is used for allowing you to specify a commit message directly on the command line                                                                                                                                                                          |
| `git branch -m main`                  | renaming the current branch forcefully                                                                                                                                                                                                                                          |
| `git remote add origing repoLink.git` | associate a remote repository with the name "origin" to your local repository. This allows you to push and pull changes between your local and the remote repositories                                                                                                          |
| `git push -u origin main`             | pushes local repo to remote, `-u` or `--set-upstream` flag is used to set the upstream branch. It tells Git to associate the local branch with the remote branch, enabling you to use `git push` or `git pull` without specifying the remote branch and local branch every time |
| `git status`                          | display the current state of local Git repository (Branch information, Staging area, Untracked files, Upstream information)                                                                                                                                                     |
| `git log --oneline`                   | display commits that have been made to the repo, `--oneline` is used to consolidate them to one line each                                                                                                                                                                       |
| `git revert hash`                     | revert a particular commit and prompts you to add a message, add the hash number of the commit you want to revert                                                                                                                                                               |
| `git clone repo.git`                  | clones a remote repo to local machine                                                                                                                                                                                                                                           |
