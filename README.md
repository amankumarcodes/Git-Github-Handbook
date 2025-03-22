
# Git and GitHub Mastery Handbook  
**A Comprehensive Guide from Basics to Advanced Techniques**  

---

## 📖 Table of Contents  
1. [Introduction to Version Control](#-chapter-1-introduction-to-version-control)  
2. [Setting Up Git](#-chapter-2-setting-up-git)  
3. [Core Git Commands](#-chapter-3-core-git-commands)  
4. [Branching and Merging](#-chapter-4-branching-and-merging)  
5. [Collaboration with Remote Repositories](#-chapter-5-collaboration-with-remote-repositories)  
6. [GitHub Essentials](#-chapter-6-github-essentials)  
7. [Advanced Git Techniques](#-chapter-7-advanced-git-techniques)  
8. [Best Practices & Workflows](#-chapter-8-best-practices--workflows)  
9. [Troubleshooting & Recovery](#-chapter-9-troubleshooting--recovery)  
10. [Appendices & Resources](#-appendices--resources)  

---

## 🌟 Chapter 1: Introduction to Version Control  

### 1.1 What is Version Control?  
A system to track changes to files over time, enabling collaboration, history tracking, and error recovery.  

### 1.2 Why Git?  
- **Distributed Architecture**: Every developer has a full project history.  
- **Branching & Merging**: Isolate features and merge them seamlessly.  
- **Open Source & Community-Driven**: Widely adopted with robust tooling.  

### 1.3 Key Terminology  
| Term          | Description                                  |  
|---------------|----------------------------------------------|  
| Repository    | Database storing project files and history   |  
| Commit        | Snapshot of changes at a specific time       |  
| Branch        | Independent line of development              |  
| Remote        | Shared repository (e.g., GitHub, GitLab)     |  

---

## 🛠️ Chapter 2: Setting Up Git  

### 2.1 Installation Guide  
**Linux**:  
```bash  
sudo apt-get install git  # Debian/Ubuntu  
sudo yum install git      # Red Hat/CentOS  
```  

**macOS**:  
```bash  
brew install git          # Using Homebrew  
```  

**Windows**:  
Download from [git-scm.com](https://git-scm.com/download/win).  

### 2.2 First-Time Configuration  
```bash  
git config --global user.name "Jane Doe"  
git config --global user.email "jane@example.com"  
git config --global core.editor "code --wait"  # VS Code  
```  

### 2.3 Verify Setup  
```bash  
git config --list  # View all settings  
git --version      # Check installed version  
```  

---

## 💻 Chapter 3: Core Git Commands  

### 3.1 Repository Basics  
| Command                     | Description                          |  
|-----------------------------|--------------------------------------|  
| `git init`                  | Initialize a new repository          |  
| `git status`                | Check untracked/staged changes       |  
| `git add <file>`            | Stage a file for commit              |  
| `git commit -m "Message"`   | Commit staged changes                |  
| `git log --oneline --graph` | View concise commit history          |  

**Example Workflow**:  
```bash  
git init  
git add README.md  
git commit -m "Initial commit"  
```  

### 3.2 Undoing Changes  
| Scenario                  | Command                          |  
|---------------------------|----------------------------------|  
| Discard unstaged changes  | `git restore <file>`            |  
| Unstage a file            | `git reset HEAD <file>`          |  
| Amend last commit         | `git commit --amend`            |  
| Revert a commit           | `git revert <commit-hash>`      |  

---

## 🌿 Chapter 4: Branching and Merging  

### 4.1 Branch Operations  
```bash  
git branch feature/login    # Create branch  
git checkout feature/login  # Switch branch  
git merge feature/login     # Merge into current branch  
```  

### 4.2 Merge vs. Rebase  
- **Merge**: Preserves history with a merge commit.  
- **Rebase**: Linearizes history by rewriting commits.  

**Rebase Workflow**:  
```bash  
git checkout feature  
git rebase main            # Apply feature commits on top of main  
```  

### 4.3 Conflict Resolution  
1. Identify conflicts with `git status`.  
2. Edit files to resolve `<<<<<<<` markers.  
3. Mark resolved: `git add <file>`.  
4. Complete merge: `git commit`.  

---

## 🌐 Chapter 5: Collaboration with Remote Repositories  

### 5.1 Remote Basics  
```bash  
git clone https://github.com/user/repo.git  
git remote -v                # List remotes  
git push origin main         # Push changes  
git pull origin main         # Fetch + merge  
```  

### 5.2 Team Collaboration Workflow  
1. Fetch updates: `git fetch origin`.  
2. Rebase local work: `git rebase origin/main`.  
3. Push changes: `git push origin feature`.  

---

## 🐙 Chapter 6: GitHub Essentials  

### 6.1 Pull Requests (PRs)  
1. Push branch: `git push -u origin feature/login`.  
2. On GitHub: **New Pull Request** → Review → Merge.  

### 6.2 GitHub CLI  
```bash  
gh pr create --title "New Feature" --body "Description"  
gh issue create --title "Bug" --body "Steps to reproduce"  
```  

### 6.3 GitHub Actions (CI/CD)  
Example `.github/workflows/build.yml`:  
```yaml  
name: Build  
on: [push]  
jobs:  
  build:  
    runs-on: ubuntu-latest  
    steps:  
      - uses: actions/checkout@v2  
      - run: npm install && npm test  
```  

---

## ⚡ Chapter 7: Advanced Git Techniques  

### 7.1 Interactive Rebase  
```bash  
git rebase -i HEAD~3  # Edit, squash, or reorder commits  
```  

### 7.2 Git Hooks  
**Example Pre-Commit Hook**:  
```bash  
#!/bin/sh  
echo "Running tests..."  
npm test  
```  
Save as `.git/hooks/pre-commit` and make executable.  

### 7.3 Submodules  
```bash  
git submodule add https://github.com/user/lib.git  
git submodule update --init --recursive  
```  

---

## ✅ Chapter 8: Best Practices & Workflows  

### 8.1 Commit Message Guidelines  
Use [Conventional Commits](https://www.conventionalcommits.org/):  
```  
feat: Add dark mode toggle  
fix: Resolve login timeout bug  
docs: Update API documentation  
```  

### 8.2 Branch Naming Convention  
- `feature/login-page`  
- `bugfix/header-alignment`  
- `hotfix/api-endpoint`  

### 8.3 Gitflow Workflow  
```bash  
git flow init                   # Initialize  
git flow feature start login    # Start feature  
git flow feature finish login   # Merge into develop  
```  

---

## 🚨 Chapter 9: Troubleshooting & Recovery  

### 9.1 Common Issues  
**Accidental Commit**:  
```bash  
git reset --soft HEAD~1  # Undo commit, keep changes staged  
```  

**Recover Deleted Branch**:  
```bash  
git reflog               # Find lost commit hash  
git checkout -b <branch> <hash>  
```  

### 9.2 Data Recovery  
```bash  
git fsck --full          # Check repository integrity  
git gc --aggressive      # Cleanup and optimize  
```  

---

## 📚 Chapter 10 : Appendices & Resources  

### A. Git Cheatsheet  
| Command               | Description                          |  
|-----------------------|--------------------------------------|  
| `git stash`           | Save working changes                 |  
| `git tag v1.0`        | Create a release tag                 |  
| `git bisect`          | Binary search for bugs               |  

### B. Recommended Resources  
- **Books**: [Pro Git](https://git-scm.com/book/en/v2)  
- **Courses**: [GitHub Learning Lab](https://lab.github.com/)  
- **Tools**: [GitKraken](https://www.gitkraken.com/), [Sourcetree](https://www.sourcetreeapp.com/)  

### C. Practice Exercises  
1. Create a branch, make changes, and merge via PR.  
2. Resolve a simulated merge conflict.  

---
 
**Contributors**: Aman Kumar 

--- 

🌟 **Happy Coding!** 🚀  
