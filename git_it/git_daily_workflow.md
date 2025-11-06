# 🔄 **Daily Workflow (Solo or Team)**

```bash
git checkout main
git pull origin main

git checkout -b feat/login-page

# work, stage, commit
git add .
git commit -m "feat(login): add login UI"

git push -u origin feat/login-page

```

Then open GitHub → **New Pull Request**

---

> 💬 Best Practice:
> 
> 
> Branch naming convention:
> 
> - `feat/` → feature
> - `fix/` → bug fix
> - `chore/` → cleanup
> - `docs/` → documentation