# Git Workflow Guide — CHN Asset Tracking

## The Golden Rule
**Never push directly to `main`.** All changes go through a branch and a Pull Request (PR).

---

## One-Time Setup: Protect the `main` Branch

Do this once on GitHub to prevent accidental direct pushes:

1. Go to your repo on GitHub
2. Click **Settings** → **Branches**
3. Click **Add branch protection rule**
4. Branch name pattern: `main`
5. Check **Require a pull request before merging**
6. Check **Require approvals** (set to 1)
7. Click **Save changes**

Now nobody can push to `main` without a review.

---

## Daily Workflow (Every Time You Work)

### Step 1 — Always pull first
```bash
git checkout main
git pull
```
This ensures you start from the latest version.

### Step 2 — Create your own branch
```bash
git checkout -b your-name/what-youre-doing
```
Example:
```bash
git checkout -b yuxian/update-asset-table
```

### Step 3 — Make your changes
Edit your files as usual.

### Step 4 — Save and push your branch
```bash
git add .
git commit -m "brief description of what you changed"
git push -u origin your-name/what-youre-doing
```

### Step 5 — Open a Pull Request on GitHub
1. Go to your repo on GitHub
2. You'll see a banner: **"Compare & pull request"** — click it
3. Add a title and short description of what you changed
4. Click **Create pull request**
5. Tag your teammate to review it

---

## Reviewing a Teammate's PR

1. Go to the repo → **Pull requests** tab
2. Click their PR
3. Click **Files changed** to see what they edited
4. Leave comments on any lines you're unsure about
5. If it looks good → click **Review changes** → **Approve**
6. Click **Merge pull request**
7. Click **Delete branch** (keeps things tidy)

---

## If There's a Conflict

When you open a PR and GitHub says there's a conflict:

```bash
git checkout main
git pull
git checkout your-branch
git merge main
```

Git will mark the conflicting lines in the file like this:
```
<<<<<<< HEAD
your version
=======
teammate's version
>>>>>>> main
```

Manually edit the file to keep the correct version, delete the markers, then:
```bash
git add .
git commit -m "resolve merge conflict"
git push
```

---

## Quick Reference

| Action | Command |
|--------|---------|
| Start fresh | `git checkout main && git pull` |
| New branch | `git checkout -b name/feature` |
| Save changes | `git add . && git commit -m "message"` |
| Push branch | `git push -u origin branch-name` |
| Next pushes | `git push` |
