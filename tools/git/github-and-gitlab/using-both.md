# Git Workflow Cheat Sheet

I used this cheat sheet during my AI Engineering - spring semester 2026

## Remotes

- **origin** → School GitLab repo (submission)
- **portfolio** → Personal GitHub repo (portfolio)

Check remotes:
```bash
git remote -v
```

## Branch

Check current branch:

```
git branch
```

Rename to `main` if needed:

```
git branch -M main
```

## Daily Workflow

1️⃣ During the day (push to school)

Save progress often:

```
git add .
git commit -m "Describe your changes"
git push origin main
```

2️⃣ At the end of the day (update portfolio)

Push all commits to GitHub:

```
git push portfolio main
```

OR vice versa! 

## Initial setup for portfolio (only once)

### Add GitHub as a remote

```
git remote add portfolio git@github.com:YOUR_USERNAME/YOUR_REPO.git
```

### Push first time

```
git push -u portfolio main
```

## Common Checks & Fixes

### Check commit history

```
git log --oneline
```

### If GitHub repo already has commits (like a README)

```
git pull portfolio main --allow-unrelated-histories
git push -u portfolio main
```

## Optional: Push to both remotes at once

(Not required; manual is safer)

```
git remote set-url --add --push origin git@gitlab:...your-school-repo.git
git remote set-url --add --push origin git@github.com:YOUR_USERNAME/YOUR_REPO.git

# Then this pushes to both:
git push origin main
```

## Notes

Always check your current branch before pushing.

Push to origin frequently during the day for school submissions.

Push to portfolio at the end of the day for your personal backup/portfolio.