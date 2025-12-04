# 🔧 How to Set `main` as Default Branch on GitHub

## 📸 Current Situation
You have 2 branches:
- `main` - Has your recent commits ✅
- `master` - Currently the default branch ⚠️

---

## ✅ **Solution: Set `main` as Default Branch**

### **Method 1: Via GitHub Web Interface (Easiest)**

#### **Step 1: Go to Repository Settings**
1. Open your repository: https://github.com/singhravish486/Blockchain-Chance
2. Click on **"Settings"** tab (top right, near "Code" tab)
3. In the left sidebar, click **"Branches"** (under "Code and automation")

#### **Step 2: Change Default Branch**
1. Under **"Default branch"** section, you'll see `master`
2. Click the **switch icon** (⇄) or **"Switch to another branch"** button
3. Select **`main`** from the dropdown
4. Click **"Update"**
5. Confirm by clicking **"I understand, update the default branch"**

#### **Step 3: Verify**
- The default branch should now show `main`
- Your repository page will now show `main` branch by default

---

### **Method 2: Delete `master` Branch (Optional)**

If you don't need the `master` branch anymore:

#### **On GitHub:**
1. Go to your repository
2. Click **"Branches"** (near the top, shows "2 Branches")
3. Find `master` branch
4. Click the **trash icon** 🗑️ to delete it
5. Confirm deletion

#### **Locally (in your terminal):**
```bash
# Delete local master branch
git branch -d master

# Delete remote master branch
git push origin --delete master
```

---

### **Method 3: Via Git Command Line**

```bash
# Set main as default branch on GitHub
git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main

# Push the change
git push origin main
```

---

## 🔍 **Why You Have 2 Branches:**

### **Historical Context:**
- **Old Git convention**: Default branch was called `master`
- **New Git convention** (2020+): Default branch is called `main`
- Your repository was created with `master` as default
- You pushed to `main` recently

### **What Happened:**
1. Your local repository uses `main` branch
2. You pushed to `main` (which created it on GitHub)
3. GitHub still has `master` as the default branch
4. Now you have both branches

---

## ✅ **Recommended Actions:**

### **Option A: Keep Only `main` (Recommended)**
1. Set `main` as default on GitHub (Method 1 above)
2. Delete `master` branch (Method 2 above)
3. Result: Clean repository with only `main` branch

### **Option B: Keep Both Branches**
1. Set `main` as default on GitHub
2. Keep `master` for historical purposes
3. Result: Both branches exist, but `main` is primary

---

## 📝 **Step-by-Step Visual Guide:**

### **Setting Default Branch:**

```
GitHub Repository
  └─ Settings (tab)
      └─ Branches (sidebar)
          └─ Default branch
              ├─ Current: master ⚠️
              └─ Change to: main ✅
                  └─ Click "Update"
                      └─ Confirm
```

### **Deleting `master` Branch:**

```
GitHub Repository
  └─ Branches (near Code tab)
      └─ All branches (2)
          ├─ main ✅ (default)
          └─ master
              └─ 🗑️ Delete
                  └─ Confirm
```

---

## 🎯 **After Setting `main` as Default:**

### **Benefits:**
- ✅ Repository shows `main` branch by default
- ✅ Clone operations use `main` automatically
- ✅ Pull requests default to `main`
- ✅ Follows modern Git conventions
- ✅ Cleaner repository structure

### **What Changes:**
- Default branch badge shows `main`
- Repository homepage shows `main` branch code
- New clones checkout `main` by default
- GitHub Actions and workflows target `main`

---

## 🔄 **Update Local Repository (After Setting Default):**

```bash
# Update your local repository to track main as default
git branch -m master main  # Rename local master to main (if needed)
git fetch origin
git branch -u origin/main main
git remote set-head origin -a
```

---

## ⚠️ **Important Notes:**

### **Before Deleting `master`:**
- ✅ Ensure all important commits are in `main`
- ✅ Update any CI/CD pipelines that reference `master`
- ✅ Notify collaborators (if any)
- ✅ Check if any external services reference `master`

### **Protected Branches:**
- If `master` is protected, you'll need to:
  1. Remove protection rules from `master`
  2. Add protection rules to `main`
  3. Then delete `master`

---

## 📞 **Quick Reference:**

| Task | Command/Action |
|------|----------------|
| **Set default on GitHub** | Settings → Branches → Change default |
| **Delete master on GitHub** | Branches → master → 🗑️ Delete |
| **Delete master locally** | `git branch -d master` |
| **Delete master remotely** | `git push origin --delete master` |
| **Verify default** | Check repository homepage |

---

## ✅ **Summary:**

1. **Go to**: https://github.com/singhravish486/Blockchain-Chance/settings/branches
2. **Click**: Switch icon next to "Default branch"
3. **Select**: `main`
4. **Confirm**: Update default branch
5. **Optional**: Delete `master` branch

**Done! Your repository will now use `main` as the default branch.** 🎉

---

## 🔗 **Direct Links:**

- **Repository Settings**: https://github.com/singhravish486/Blockchain-Chance/settings
- **Branches Settings**: https://github.com/singhravish486/Blockchain-Chance/settings/branches
- **All Branches**: https://github.com/singhravish486/Blockchain-Chance/branches

---

**Need help? The process takes less than 1 minute!** ⚡
