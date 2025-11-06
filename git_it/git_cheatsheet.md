# 🧾 **Git Cheat Sheet**

| Action | Command |
| --- | --- |
| Init repo | `git init` |
| Stage all changes | `git add .` |
| Commit | `git commit -m "message"` |
| Rename branch | `git branch -M main` |
| Add remote | `git remote add origin <url>` |
| Push first time | `git push -u origin main` |
| Create branch | `git checkout -b <branch>` |
| Merge branch | `git merge <branch>` |
| Check status | `git status` |
| View log | `git log --oneline --graph --decorate --all` |

---

> ⚠️ Undo Safety
> 
> - Undo last commit (keep changes):
>     
>     `git reset --soft HEAD~1`
>     
> - Unstage file:
>     
>     `git restore --staged <file>`
>     
> - Discard local edits:
>     
>     `git restore <file>`
>