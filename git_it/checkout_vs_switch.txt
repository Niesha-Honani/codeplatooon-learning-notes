# 🧭 Git `switch` vs `checkout`

## 🧩 Background

Originally, **`git checkout`** did *everything*:

- Switching branches
- Restoring files
- Creating new branches

…but this made it **confusing** and **error-prone**.

So Git introduced **`git switch`** (and `git restore`) in **Git 2.23 (2019)** to make commands **clearer and safer**.

---

## ⚖️ Command Comparison

| Task | Old Way (Legacy) | New Way (Modern / Preferred) | What It Does |
| --- | --- | --- | --- |
| ✅ Switch to another branch | `git checkout <branch>` | `git switch <branch>` | Move between branches |
| 🌿 Create and switch to new branch | `git checkout -b <branch>` | `git switch -c <branch>` | Make a new branch and switch to it |
| 🔁 Restore files (undo changes) | `git checkout -- <file>` | `git restore <file>` | Revert file(s) to last commit |

---

## 🧠 Concept Difference

| Command | Focus | Behavior | Risk Level |
| --- | --- | --- | --- |
| **`git checkout`** | All-in-one | Switch branch *or* restore files | 🟠 Medium – easy to overwrite changes if used wrong |
| **`git switch`** | Branch management only | Cleanly moves between branches | 🟢 Safe – won’t overwrite file content |
| **`git restore`** | File content recovery | Restores working directory files | 🟢 Safe for undoing local file edits |

---

## 🧪 Example Scenarios

### 🧱 1. You just finished coding a feature and want to switch to another branch

```bash
git switch main

```

✅ *Best practice:* Use `switch` since you’re only changing branches.

---

### 🌿 2. You want to start a new feature

```bash
git switch -c feature/add-login

```

Equivalent to:

```bash
git checkout -b feature/add-login

```

✅ *Best practice:* Use `switch -c` — easier to read and safer.

---

### 🔁 3. You messed up a file and want to restore it

```bash
git restore app.js

```

Old way:

```bash
git checkout -- app.js

```

✅ *Best practice:* Use `restore` to make intent clear — you’re undoing changes, not switching branches.

---

## 💡 When to Use Each

| Use Case | Recommended Command | Why |
| --- | --- | --- |
| Switching branches | `git switch` | Safer, cleaner |
| Creating new branch | `git switch -c <name>` | Modern syntax |
| Undoing file changes | `git restore` | More explicit |
| Older Git version (< 2.23) | `git checkout` | Only option available |
| Scripted automation or legacy CI/CD | `git checkout` | Still supported everywhere |

---

## 🧭 Summary

> Use switch and restore for clarity
> 
> 
> **Use `checkout` only for older systems or scripts**
> 
- `git switch` → move between branches
- `git restore` → revert file changes
- `git checkout` → older all-purpose command (still works)

---

## 🧱 Quick Memory Trick

> 🧩 Switch → Branch
> 
> 
> 🧩 **Restore → Files**
> 
> 🧩 **Checkout → Both (Legacy)**
>