### 1. **Introduction to Git and GitHub**

#### a. **Git**
Git is a distributed version control system (VCS) that helps you track changes in your project files and collaborate with other developers.

#### b. **GitHub**
GitHub is a cloud-based platform that hosts Git repositories, allowing you to share your code, collaborate with others, and manage your projects.

---

### 2. **Installing and Setting Up Git**

#### a. **Installation**

- **Windows**: Download and install Git from [git-scm.com](https://git-scm.com).
- **MacOS**: Install using Homebrew:
  ```bash
  brew install git
  ```
- **Linux**: Install via package manager:
  ```bash
  sudo apt-get install git
  ```

#### b. **Initial Setup**

After installing Git, configure your identity and email:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

To check the configuration:

```bash
git config --list
```

---

### 3. **Git Basics: Repositories and Basic Commands**

#### a. **Creating a New Repository**

To start using Git, you need to initialize a repository (repo):

```bash
git init
```

This creates a `.git` folder where Git stores version control data.

#### b. **Cloning an Existing Repository**

You can clone a repository from GitHub or any other Git host:

```bash
git clone https://github.com/user/repo.git
```

This creates a copy of the repository on your local machine.

#### c. **Checking Repository Status**

To see the current state of your working directory:

```bash
git status
```

This command tells you which files are staged for commit, modified, or untracked.

#### d. **Tracking Files**

To track new files or changes:

```bash
git add filename.txt  # Stages a single file
git add .             # Stages all modified/new files
```

#### e. **Committing Changes**

Once files are staged, you can commit them with a descriptive message:

```bash
git commit -m "Add feature X"
```

#### f. **Viewing Commit History**

To see the history of commits:

```bash
git log
```

For a more concise log:

```bash
git log --oneline --graph
```

---

### 4. **Branching and Merging**

#### a. **What Are Branches?**

A branch in Git allows you to work on different versions of your project simultaneously. The default branch is usually called `main` or `master`.

#### b. **Creating a New Branch**

To create a new branch and switch to it:

```bash
git checkout -b feature-branch
```

Alternatively, to create without switching:

```bash
git branch feature-branch
```

#### c. **Switching Branches**

To switch between branches:

```bash
git checkout main
```

#### d. **Merging Branches**

When you finish working on a feature branch, you can merge it back into the main branch:

1. First, switch to the branch you want to merge into (usually `main`):

    ```bash
    git checkout main
    ```

2. Merge the feature branch:

    ```bash
    git merge feature-branch
    ```

#### e. **Handling Merge Conflicts**

If two branches modify the same parts of a file, Git will produce a conflict that needs manual resolution.

1. Open the conflicting file(s), look for conflict markers (`<<<<`, `====`, `>>>>`), and resolve the conflict.
2. After resolving, add the file:

    ```bash
    git add filename.txt
    ```

3. Commit the merge:

    ```bash
    git commit
    ```

---

### 5. **Working with Remote Repositories**

#### a. **Adding a Remote Repository**

A remote repository is a version of your project hosted on the internet or another network. To link your local repo to a GitHub repo:

```bash
git remote add origin https://github.com/user/repo.git
```

To check your remotes:

```bash
git remote -v
```

#### b. **Pushing Changes to GitHub**

To push changes from your local repository to a remote repository:

```bash
git push origin branch-name
```

If you’re pushing for the first time after cloning, or setting up a new branch:

```bash
git push -u origin branch-name
```

This `-u` option sets the upstream tracking reference, meaning you can just type `git push` next time.

#### c. **Pulling Changes from GitHub**

To update your local repo with the latest changes from the remote repository:

```bash
git pull origin branch-name
```

#### d. **Fetching from Remote**

Fetching retrieves the latest updates from the remote repository but doesn’t merge them into your local branches. It updates your remote-tracking branches.

```bash
git fetch origin
```

To merge the fetched changes:

```bash
git merge origin/branch-name
```

---

### 6. **Git Reset, Revert, and Checkout**

#### a. **Undoing Changes with `git checkout`**

To discard changes in a working directory (before staging):

```bash
git checkout -- filename.txt
```

#### b. **Unstaging Changes**

If you’ve staged files but want to unstage them:

```bash
git reset filename.txt
```

#### c. **Reverting Commits**

`git revert` creates a new commit that undoes the changes from a previous commit. This is useful for reverting changes in a public branch.

```bash
git revert commit-hash
```

#### d. **Resetting Commits**

- `git reset --soft HEAD~1`: Moves the `HEAD` pointer back by one commit, but keeps the changes staged.
- `git reset --mixed HEAD~1`: Moves the `HEAD` pointer back by one commit, and unstages the changes.
- `git reset --hard HEAD~1`: Completely removes the last commit and discards all changes.

Be cautious with `--hard` as it deletes data permanently.

---

### 7. **Stashing Changes**

Stashing allows you to temporarily save changes without committing them, so you can work on something else.

#### a. **Saving Changes with Stash**

```bash
git stash
```

#### b. **Applying Stash**

When you're ready to apply your stashed changes:

```bash
git stash apply
```

#### c. **Listing and Dropping Stashes**

To list all saved stashes:

```bash
git stash list
```

To remove a stash from the list:

```bash
git stash drop stash@{0}
```

---

### 8. **Collaborating with Pull Requests (PRs)**

Pull Requests (PRs) allow developers to propose changes to a codebase and have them reviewed before merging.

#### a. **Creating a PR on GitHub**

1. Push your feature branch to GitHub.
2. Go to the GitHub repository and create a new PR from your branch into `main` (or any other target branch).
3. Provide a description and submit the PR for review.

#### b. **Merging PRs**

Once the PR is approved, you can merge it on GitHub using the merge button, or you can fetch the changes and merge locally.

#### c. **Rebasing**

Rebasing moves your branch on top of another branch’s history, making for a cleaner history.

```bash
git checkout feature-branch
git rebase main
```

This rewrites the commit history of `feature-branch` to apply after `main`.

---

### 9. **Forking and Contributing to Other Projects**

#### a. **Forking a Repository**

To contribute to a repository you don’t own, you need to fork it (create a personal copy) on GitHub:

1. Click the "Fork" button on GitHub.
2. Clone the forked repository:

    ```bash
    git clone https://github.com/your-username/repo.git
    ```

#### b. **Setting Up an Upstream**

After cloning your fork, you’ll want to track the original repository so you can pull the latest changes:

```bash
git remote add upstream https://github.com/original-owner/repo.git
```

To fetch the latest changes from the original repository:

```bash
git fetch upstream
```

To merge them into your local `main` branch:

```bash
git merge upstream/main
```

---

### 10. **Git Ignore Files**

A `.gitignore` file tells Git which files or directories to ignore (e.g., build files, logs, environment settings).

Example `.gitignore` file:

```
node_modules/
*.log
.env
```

---

### 11. **Git Hooks**

Git hooks allow you to run custom scripts when certain Git events occur. For example, you can run a script every time you commit.

Hooks are stored in the `.git/hooks` directory.

Example of enabling a pre-commit hook:

```bash
#!/bin/sh
# pre-commit hook to check for TODO comments before committing
if grep -r TODO .; then
  echo "There are TODOs in the code. Please address them before committing."
  exit 1
fi
```

---

### 12. **Git Best Practices**

1. **Commit Often, Commit Early**: Make small, frequent commits.
2. **Write Clear Commit Messages**: Explain why a change was made.
3. **Use Branches**

: Keep your main branch stable and use feature branches.
4. **Avoid Pushing to `main`/`master` Directly**: Use PRs for code review.
5. **Rebase Before Merging**: To keep the commit history clean and linear.

---

### 13. **Advanced Git Tools**

#### a. **Cherry-picking**

Cherry-picking allows you to apply a specific commit from one branch to another.

```bash
git cherry-pick commit-hash
```

#### b. **Reflog**

Git’s reflog tracks all changes made to `HEAD`, even if they aren’t visible in the commit history.

```bash
git reflog
```

#### c. **Squashing Commits**

When merging or rebasing, you can squash multiple commits into one to simplify the history.

```bash
git rebase -i HEAD~3
```

In the interactive rebase menu, choose `squash` for the commits you want to combine.

---
