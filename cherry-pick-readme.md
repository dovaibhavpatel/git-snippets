# 🧠 What is git cherry-pick?
- It copies one or more commits from one branch and applies them to another.
- Useful when you want to apply specific changes (not the whole branch).
- Example use case: pick a bug fix from ```dev``` and apply it to ```release/hotfix```.


# ✅ How to Cherry-Pick Commits from One Branch to Another

## 1. Get the list of commits from the old branch

Switch to the source branch and get the commit IDs in order:

```bash
git checkout old-branch
git log
```
## 🔀 2. Checkout to Target Base Branch

Move to the branch where you want to create the new feature or bugfix branch.

```bash
git checkout main  # or your base branch
```

---

## 🌿 3. Create a New Branch

Create a new branch from the base branch to apply the cherry-picked commits.

```bash
git checkout -b feature/cherry-pick-fixes
```

---

## 🍒 4. Cherry-Pick Commits One by One

Apply the commits in the same order as noted:

```bash
git cherry-pick <commit-id-1>
git cherry-pick <commit-id-2>
git cherry-pick <commit-id-3>
```

Example:

```bash
git cherry-pick a1b2c3d
git cherry-pick e4f5g6h
```

---

## 🍒 How to Cherry-Pick from Multiple PRs

Follow these 5 steps to cherry-pick commits from multiple PRs safely and in the right order:

### 1. 📋 List All PRs

Start by identifying all the pull requests you want to cherry-pick from.

---

### 2. 🕒 Get All Commits with Timestamps

Go to each PR on GitHub and collect the commit hashes along with their **commit times** (not PR creation time).

---

### 3. 📊 Sort Commits by Time

Reorder the commits from **oldest to newest** based on commit time.  
⚠️ Skip merge-only commits (like syncing with `main` or `integration` branches).

---

### 4. 🍒 Cherry-Pick Commits in Order

Switch to the target branch and apply each commit one by one in order:

```bash
git cherry-pick <commit-1>
git cherry-pick <commit-2>
git cherry-pick <commit-3>
```

---

### 5. 🛠️ Handle Conflicts if Any

If a conflict occurs during cherry-pick:

```bash
# Fix the conflicts in files manually, then run:
git add .
git cherry-pick --continue
```

Resolve each conflict before moving to the next commit.

---


## ⚠️ Common Issues While Cherry-Picking

### ❗ 1. Conflicts

Conflicts occur when the same lines of code were changed in both branches.

Git will show the conflicted files. You need to resolve them manually:

```bash
git add .
git cherry-pick --continue
```

---

### 🔁 2. Wrong Commit Order

If a commit depends on another, make sure to cherry-pick them in the correct order.

---

### 🚫 3. To Cancel a Cherry-Pick

If you're in the middle of a cherry-pick and want to stop (e.g., due to conflicts):

```bash
git cherry-pick --abort
```
