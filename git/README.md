# ❓Problem

---

You renamed your GitHub remote repository, but your local Git repo still points to the old name. So now git push or git pull may fail or go to the wrong place.

## ✅ How to Fix: Update the Remote URL

1. Check your current remote URL
```bash
git remote -v
```
You’ll see something like:
```bash
origin  git@github.com:yourname/old-repo.git (fetch)
origin  git@github.com:yourname/old-repo.git (push)
```
2. Update the remote URL to the new repo
```bash
git remote set-url origin git@github.com:yourname/new-repo.git
```
If you use HTTPS instead of SSH:
```bash
git remote set-url origin https://github.com/yourname/new-repo.git
```
3. Verify the change
```bash
git remote -v
```
You should now see:
```bash
origin  git@github.com:yourname/new-repo.git (fetch)
origin  git@github.com:yourname/new-repo.git (push)
```

---
