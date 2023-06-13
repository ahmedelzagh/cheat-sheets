# Git and GitHub

Git is a distributed version control system (VCS) designed to manage source code repositories. It allows multiple developers to collaborate on a project, track changes, and manage different versions of files efficiently. GitHub, on the other hand, is a web-based hosting service that provides additional features and functionality built on top of Git.
Documentation: [Git documentation](https://git-scm.com/doc).

## Git

Git offers several key features that make it popular among developers:

- **Distributed Version Control:** Git is a distributed system, which means that every developer has a complete copy of the entire repository, including its history. This allows developers to work offline and independently, making it easier to merge changes and collaborate effectively.
    
- **Branching and Merging:** Git provides powerful branching and merging capabilities. Developers can create branches to work on specific features or bug fixes without affecting the main codebase. Git allows for easy merging of changes from one branch to another, enabling collaboration and efficient code integration.
    
- **Fast and Efficient:** Git is designed to be fast and perform well, even with large repositories. It uses advanced algorithms to handle version control operations quickly, making it suitable for projects of all sizes.
    
- **Integrity and Data Protection:** Git uses cryptographic hashing to ensure the integrity of files and track changes. Each file and commit in Git has a unique identifier, making it difficult to tamper with or lose data without detection.
    
- **Flexible Workflow:** Git allows developers to choose from various workflows based on their project needs. The most common workflow is the **feature branch workflow**, where each developer works on a separate branch and merges changes into the main branch when ready.
	
- **Snapshots**
	Git uses a "snapshot-based" approach to version control. Instead of storing differences between versions, it captures the entire state of the project at each commit. This makes branching and merging fast and efficient.
- **History and Tracking**
	Git maintains a complete history of all commits made to a repository, enabling developers to track changes over time, understand who made specific changes, and revert to previous versions if needed.
- **Staging Area**
	Git has a staging area (also called the index) where changes can be selectively prepared for commit. This allows developers to review and organize changes before committing them.

## GitHub

GitHub is a cloud-based platform that provides additional features and services built around Git. It enhances collaboration and provides a centralized place for hosting Git repositories. Some key features of GitHub include:

- **Remote Repository Hosting:** GitHub allows developers to store their Git repositories in the cloud, making it easy to access and share code with others. It provides a user-friendly web interface for managing repositories, branches, and files.
    
- **Collaboration and Pull Requests:** GitHub enables seamless collaboration among developers. It provides a mechanism called pull requests, where developers can propose changes to a project. Other team members can review and discuss the changes before merging them into the main codebase.
    
- **Issue Tracking:** GitHub includes an issue tracking system, where users can create, assign, and track issues or tasks related to a project. It facilitates project management and helps teams stay organized.
    
- **Continuous Integration/Continuous Deployment (CI/CD):** GitHub integrates with popular CI/CD tools, such as Jenkins or Travis CI. Developers can set up automated workflows to build, test, and deploy their code directly from GitHub, ensuring high code quality and faster development cycles.
    
- **Community and Open Source Projects:** GitHub hosts a vast ecosystem of open source projects. It provides tools for collaboration, discovery, and contribution, making it easier for developers to participate in open source communities and contribute to projects they are interested in.

GitHub has become a widely adopted platform for both open source and private projects due to its extensive features, user-friendly interface, and strong integration with Git. It promotes collaboration, code sharing, and provides a robust infrastructure for version control and project management.

## Usage
Git is widely used in various software development workflows, including open-source projects, enterprise software development, and individual projects. It is supported on multiple operating systems and has a vast ecosystem of tools and services built around it, making it highly versatile and adaptable to different development environments.

---
## Using GitHub on a New Machine
1. Create an [**SSH key**](OpenSSH.md)
2. Display and copy your **public SSH key**:
	```bash
	cat .ssh/id_ed25519.pub
	```
3. Add the **public SSH key** to your **GitHub** account by going to `settings > SSH and GPG keys`, then pressing on `New SSH key` button and give a title to your **SSH key** and press `Add SSH key` after pasting your key.
4. Tell **Git** who we are by running the following commands:
```bash
git config --global user.name "Ahmed Elzagh"
git config --global user.email "contact@aelzagh.com"
```
*Note: That can be found later at `~/.gitconfig`.*

## Creating a local repository and pushing it to a remote repository

```bash
git init #initializing a local repo
git add "file" #adding files to the staging area
git commit -m "your commit" #commiting changes
git branch -M main #forcefully rename the branch to main
git remote add origin repolink.git #associate the local repo with the remote
git push -u origin main #pushing local repo to remote
```

## Git Commands

| Command                                               | Desc                                                                                                                                                                                                                                                                             |
| ----------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `git init`                                            | initializes a local repo.                                                                                                                                                                                                                                                        |
| `git add`                                             | adds a change in the working directory to the staging area.                                                                                                                                                                                                                      |
| `git commit -m "initial commit"`                      | commit changes, `-m` is used for allowing you to specify a commit message directly on the command line.                                                                                                                                                                          |
| `git commit -am "your commit"`                        | adds all changes and commit them at the same time. *note: Files in which changes happened must be added to the version control before*                                                                                                                                                                                                                                                                                 |
| `git branch -m main`                                  | renaming the current branch forcefully.                                                                                                                                                                                                                                          |
| `git remote add origing repoLink.git`                 | associate a remote repository with the name "origin" to your local repository. This allows you to push and pull changes between your local and the remote repositories.                                                                                                          |
| `git push -u origin main`                             | pushes local repo to remote, `-u` or `--set-upstream` flag is used to set the upstream branch. It tells Git to associate the local branch with the remote branch, enabling you to use `git push` or `git pull` without specifying the remote branch and local branch every time. |
| `git status`                                          | display the current state of local Git repository (Branch information, Staging area, Untracked files, Upstream information).                                                                                                                                                     |
| `git diff`                                            | Shows the differences between the working directory and the previous commit for all modified files.                                                                                                                                                                              |
| `git diff --staged`                                   | Shows the differences between the staged changes and the previous commit.                                                                                                                                                                                                        |
| `git diff file.txt`                                   | Shows the differences for a specific file.                                                                                                                                                                                                                                       |
| `git diff directory/`                                 | Shows the differences for all files in a specific directory.                                                                                                                                                                                                                     |
| `git log --oneline`                                   | display commits that have been made to the repo, `--oneline` is used to consolidate them to one line each.                                                                                                                                                                       |
| `git revert hash`                                     | revert a particular commit and prompts you to add a message, add the hash number of the commit you want to revert.                                                                                                                                                               |
| `git clone repo.git`                                  | clones a remote repo to local machine.                                                                                                                                                                                                                                           |
| `git branch`                                          | display available branches.                                                                                                                                                                                                                                                      |
| `git fetch`                                           | fetch a remote branch.                                                                                                                                                                                                                                                           |
| `git checkout branch-name`                            | switches branch, if the destination branch doesn't exist you have to append the `-b` option.                                                                                                                                                                                     |
| `git checkout commit-hash` or `git checkout tag-name` | checks out a specific commit or tag.                                                                                                                                                                                                                                             |
| `git checkout -- .` or `git checkout -- <file>`       | discards local changes in the current branch.                                                                                                                                                                                                                                    |
| `git checkout -t <remote_name>/<branch_name>`         | switches to a remote branch, `-t` option stands for `track` and it is used to create the branch and setting up the upstream branch automatically to the remote branch.                                                                                                           |
| `git switch branch-name`                              | switches branch, if the destination branch doesn't exist you have to append the `-c` option.                                                                                                                                                                                     |
| `git switch --discard-changes`                        | discards local changes in the current branch.                                                                                                                                                                                                                                    |
| `git switch -- <file>`                                | restores the state of a specific file to match the branch.                                                                                                                                                                                                                       |
