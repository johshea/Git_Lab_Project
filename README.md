# Learn The Github Basics in an Hour or Less!

Welcome to the GitHub lab for beginners! This guide walks you through creating a repository, making branches, committing changes, and merging pull requests.

---

##  Lab 1: Create a New Repository

1. Log in to https://github.com  
2. Click the '+' icon on the top right -> Select 'New repository'  
3. Fill in the repository name (e.g., `my-first-repo`)  
4. Check 'Initialize this repository with a README'  
5. Click 'Create repository'  

![Create repo](https://docs.github.com/assets/images/help/repository/repo-create.png)

---

##  Lab 2: Clone the Repository

1. Click the green 'Code' button -> Copy the HTTPS link  
![Code button](https://docs.github.com/assets/images/help/repository/code-button.png)

2. Run in your terminal:
```bash
git clone https://github.com/YOUR-USERNAME/my-first-repo.git
cd my-first-repo
```

---

##  Lab 3: Create a Branch and Commit

1. Create and switch to a new branch:
```bash
git checkout -b feature-hello
```

2. Create a file and add content:
```bash
echo "Hello, GitHub!" > hello.txt
```

3. Commit the change:
```bash
git add hello.txt
git commit -m "Add hello.txt with greeting"
```

---

##  Lab 4: Push and Open a Pull Request

1. Push your branch:
```bash
git push origin feature-hello
```

2. On GitHub, click 'Compare & pull request':
![Pull request](https://docs.github.com/assets/images/help/pull_requests/pull-request-start-review-button.png)

3. Add a message -> Click 'Create pull request'

---

##  Lab 5: Merge the Pull Request

1. Click 'Merge pull request'
2. Confirm merge
3. Optionally delete the feature branch

![Merge PR](https://docs.github.com/assets/images/help/pull_requests/merge-pull-request-button.png)

---

##  Lab 6: Sync Your Local Main Branch

```bash
git checkout main
git pull origin main
```

---

##  Bonus: View Commit History

```bash
git log --oneline
```

---

## Included Files

- `hello.txt`  Example file created in the lab  
- `git_lab_steps.sh`  Shell script with all Git steps  
- `GitHub_Beginners_Lab_Guide.pdf`  Printable PDF guide  

Happy Coding!


# Advanced GitHub Lab Guide

Welcome to the **Advanced GitHub Lab**! This guide builds on beginner concepts and teaches:

- Conflict resolution
- Interactive rebase
- Using GitHub Desktop
- Using GitHub with VS Code

---

##  Lab 1: Git Rebase
git rebase is a powerful Git command that lets you move or "replay" commits from one branch onto another. 
It's used to create a clean, linear commit history by integrating changes from one branch into another 
without creating a merge commit.

### Step 1: Create Two Branches
```bash
git checkout -b base-feature
echo "Base Feature" > base.txt
git add base.txt
git commit -m "Add base feature"
git checkout main
```

```bash
git checkout -b new-feature
echo "New Feature" > new.txt
git add new.txt
git commit -m "Add new feature"
```

### Step 2: Rebase onto Main
```bash
git checkout new-feature
git rebase main
```

---

##  Lab 2: Conflict Resolution

### Simulate Conflict:
1. Edit the same line in `conflict.txt` in both `main` and `conflict-branch`.

```bash
# On main
echo "Hello from main" > conflict.txt
git commit -am "Main edit"

# On branch
git checkout -b conflict-branch
echo "Hello from branch" > conflict.txt
git commit -am "Branch edit"
```

2. Try to merge:
```bash
git checkout main
git merge conflict-branch
```

3. Resolve conflict manually in `conflict.txt`, then:
```bash
git add conflict.txt
git commit
```

---

##  Lab 3: GitHub Desktop

1. Download: [GitHub Desktop](https://desktop.github.com/)
2. Clone a repo using File -> Clone repository
3. Make changes, commit via UI
4. Push changes and create PR from Desktop

 ![GitHub Desktop](https://docs.github.com/assets/images/help/desktop/gh-desktop-commit.png)

---

##  Lab 4: VS Code Integration

### Step 1: Install GitHub Extension
1. Open VS Code
2. Go to Extensions -> Install "GitHub Pull Requests and Issues"

### Step 2: Clone & Work
1. Clone from VS Code (`Ctrl+Shift+P` -> Git: Clone)
2. Make changes -> Source Control panel -> Commit
3. Push & sync with GitHub

 ![VS Code Git](https://code.visualstudio.com/assets/docs/editor/versioncontrol/sourcecontrol.png)

---

##  Summary

You've learned:

- How to rebase branches
- How to resolve merge conflicts
- How to use GitHub Desktop and VS Code for Git

Practice and integrate these into your real projects!

---


---

##  Lab 5: Using Git with PyCharm

PyCharm has built-in Git integration to help you work more visually.

### Step 1: Open or Clone Project

1. Open PyCharm
2. Go to **VCS > Get from Version Control**
3. Paste your GitHub repository URL and click **Clone**

### Step 2: Make Changes and Commit

1. Open any file or create a new one
2. Make changes
3. Go to **VCS > Commit** or click the **Commit** button at the bottom

### Step 3: Push to GitHub

1. After committing, click **Push** or go to **VCS > Git > Push**
2. The changes will be sent to GitHub

 ![PyCharm VCS](https://resources.jetbrains.com/help/img/idea/2022.3/commit_changes.png)



---

## 🧪 Lab 6: GitHub Actions Basics

GitHub Actions is a powerful CI/CD tool built into GitHub.

### Step 1: Create a Workflow File

Create `.github/workflows/ci.yml` with this content:

```yaml
name: CI Pipeline

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Run a script
      run: echo "✅ Build completed!"
```

### Step 2: Push Changes

Push this to GitHub and check the **Actions** tab for workflow runs.

---


