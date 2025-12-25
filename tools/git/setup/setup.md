# Repository Setup & Project Connection

This guide explains how to create a Git repository, set up a local project
folder, and connect it to a remote repository (e.g. GitHub).

## Prerequisites
- Git installed (`git --version`)
- A GitHub/GitLab account
- SSH key configured (recommended)

## Setup Options
Choose one of the following:
1. Create a remote repo first, then clone it locally (most common)
2. Create a local project first, then connect it to a remote repo

## Option A: Create Remote Repo First (Recommended)

### 1. Create the repository
- Go to GitHub
- Click "New Repository"
- Name it
- Do NOT initialize with a README (unless stated)

### 2. Create a local project folder
```bash
cd ~/Desktop
mkdir my-project
cd my-project
```
### 3. Clone the repo
```bash
git clone git@github.com:username/my-project.git
cd my-project
```

### 4. Verify connection
```bash
git remote -v
```

### 5. Option B: Local first → connect remote

This is where a lot of beginners get confused — document it clearly.
