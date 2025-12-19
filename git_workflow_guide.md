# 🚀 GitHub Setup & Git Workflow Guide

**Project**: Global E-Commerce Sales Dashboard  
**Last Updated**: December 2024  
**Version**: 1.0

---

## 📖 Table of Contents

1. [Initial Setup](#initial-setup)
2. [Repository Structure](#repository-structure)
3. [Git Workflow](#git-workflow)
4. [Branching Strategy](#branching-strategy)
5. [Commit Conventions](#commit-conventions)
6. [Pull Request Process](#pull-request-process)
7. [Common Git Commands](#common-git-commands)
8. [Troubleshooting](#troubleshooting)

---

## ⚙️ Initial Setup

### Step 1: Create GitHub Repository

**On GitHub.com**:
1. Click **+** icon → Select **New repository**
2. Repository name: `ecommerce-tableau-analysis`
3. Description: "Global E-Commerce Sales Analysis Dashboard with Tableau and GitHub"
4. Choose **Public** (or Private for sensitive data)
5. Initialize with:
   - ✅ Add README.md
   - ✅ Add .gitignore (select template)
   - ✅ Add LICENSE (MIT)
6. Click **Create repository**

### Step 2: Clone Locally

```bash
# Open terminal/command prompt
cd ~/Documents  # or your preferred location

# Clone the repository
git clone https://github.com/YOUR-USERNAME/ecommerce-tableau-analysis.git

# Navigate to project folder
cd ecommerce-tableau-analysis

# Verify connection
git remote -v
# Should show:
# origin  https://github.com/YOUR-USERNAME/ecommerce-tableau-analysis.git (fetch)
# origin  https://github.com/YOUR-USERNAME/ecommerce-tableau-analysis.git (push)
```

### Step 3: Configure Git

```bash
# Set your identity (global configuration)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Verify configuration
git config --list | grep user

# Optional: Set default branch name to 'main'
git config --global init.defaultBranch main
```

### Step 4: Set Up .gitignore

Create `.gitignore` file in root directory:

```
# Copy content from gitignore_template.txt provided

# Tableau files
*.twb~
*.twbx~
*.hyper

# Python
__pycache__/
*.py[cod]
venv/
.env

# OS files
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/
```

---

## 📁 Repository Structure

```
ecommerce-tableau-analysis/
│
├── README.md                          # Project overview & documentation
├── LICENSE                            # MIT License
├── .gitignore                         # Git exclusion rules
├── CONTRIBUTING.md                    # Contribution guidelines
│
├── data/
│   ├── raw_data.csv                  # Main dataset (100K+ rows)
│   ├── data_dictionary.md            # Column definitions & metadata
│   └── data_cleaning_notes.md        # Preprocessing documentation
│
├── tableau_workbooks/
│   ├── ecommerce_sales_analysis.twb  # Editable workbook (TRACKED)
│   └── ecommerce_sales_analysis_final.twbx  # Packaged version (snapshot)
│
├── analysis/
│   ├── methodology.md                # Analysis approach & findings
│   ├── insights.md                   # Key findings documentation
│   ├── conclusions.md                # Summary & recommendations
│   └── calculations.md               # Formula reference
│
├── screenshots/
│   ├── dashboard_1_executive.png
│   ├── dashboard_2_sales_trends.png
│   ├── dashboard_3_customer.png
│   ├── dashboard_4_regional.png
│   ├── dashboard_5_profitability.png
│   ├── dashboard_6_shipping.png
│   ├── dashboard_7_discount.png
│   └── dashboard_8_summary.png
│
├── scripts/  (optional)
│   ├── validate_data.py
│   ├── preprocess_data.py
│   └── generate_report.py
│
└── docs/
    ├── INSTALLATION_GUIDE.md
    ├── TABLEAU_PUBLIC_LINK.md
    ├── FAQ.md
    └── TROUBLESHOOTING.md
```

---

## 🔄 Git Workflow

### Main Workflow (Feature Branch)

```bash
# 1. Start: Ensure you're on main branch and up-to-date
git checkout main
git pull origin main

# 2. Create feature branch
git checkout -b feature/dashboard-enhancement

# 3. Make changes (edit files, update dashboard, etc)
# ... modify files in your editor ...

# 4. Check status
git status
# Shows which files changed

# 5. Stage changes
git add .  # Add all changes
# OR
git add data/raw_data.csv README.md  # Add specific files

# 6. Commit changes
git commit -m "feat: Add customer cohort analysis dashboard"

# 7. Push to GitHub
git push origin feature/dashboard-enhancement

# 8. Create Pull Request on GitHub
# (See Pull Request section below)

# 9. After approval & merge, clean up
git checkout main
git pull origin main
git branch -d feature/dashboard-enhancement
```

### Typical Workflow Timeline

```
DAY 1: Create feature branch
  ↓
  git checkout -b feature/new-dashboard
  ↓

DAYS 1-3: Work on changes
  ↓
  (Edit files, save, test in Tableau)
  ↓

DAY 3: Commit & push
  ↓
  git add .
  git commit -m "feat: Add new dashboard"
  git push origin feature/new-dashboard
  ↓

DAY 3-4: Create Pull Request
  ↓
  GitHub PR created, reviewer assigned
  ↓

DAY 4: Address feedback
  ↓
  (Make requested changes)
  git add .
  git commit -m "fix: Address PR feedback"
  git push origin feature/new-dashboard
  ↓

DAY 5: Approval & Merge
  ↓
  PR approved, merged to main
  ↓

DAY 5: Cleanup
  ↓
  git checkout main
  git pull origin main
  git branch -d feature/new-dashboard
```

---

## 🌿 Branching Strategy

### Branch Types

#### 1. **main** (Production)
- Stable, production-ready code
- Always working, fully tested
- Deployable at any time
- ✅ Protected branch (requires PR review)

```bash
git checkout main
```

#### 2. **develop** (Optional: for larger teams)
- Integration branch for features
- Staging area before main
- Contains latest development work

```bash
git checkout develop
```

#### 3. **feature/** (Feature Development)
- For new features or enhancements
- Created from: `main` or `develop`
- Naming: `feature/short-description`

```bash
git checkout -b feature/dashboard-enhancement
git checkout -b feature/discount-analysis
git checkout -b feature/regional-expansion
```

#### 4. **fix/** (Bug Fixes)
- For bug corrections
- Created from: `main`
- Naming: `fix/issue-description`

```bash
git checkout -b fix/profit-calculation-error
git checkout -b fix/filter-not-working
```

#### 5. **docs/** (Documentation)
- Documentation improvements
- Created from: `main`
- Naming: `docs/what-updated`

```bash
git checkout -b docs/update-readme
git checkout -b docs/add-faq
```

### Naming Convention

**Pattern**: `[type]/[brief-description]`

✅ **Good**:
- `feature/customer-lifetime-value-calc`
- `fix/shipping-cost-error`
- `docs/installation-guide`
- `refactor/dashboard-performance`

❌ **Bad**:
- `feature1` (too vague)
- `new-thing` (unclear purpose)
- `fix_stuff` (unclear what fixed)
- `main` (reserved)

---

## 💬 Commit Conventions

### Commit Format

```
<type>: <subject>

<body (optional)>

<footer (optional)>
```

### Type Categories

- `feat`: New feature or visualization
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Formatting, no code logic change
- `refactor`: Code restructuring
- `perf`: Performance improvement
- `test`: Test additions
- `chore`: Maintenance

### Subject Line

- Use imperative mood: "add feature" not "added feature"
- Capitalize first letter
- Keep under 50 characters
- No period at end

### Body (Optional)

- Explain WHAT and WHY, not HOW
- Wrap at 72 characters
- Separate from subject with blank line
- Include issue numbers: "Fixes #123"

### Examples

**Example 1: Feature**
```
feat: Add customer cohort retention analysis

- New sheet showing cohort analysis by year
- Includes 3 calculated fields for retention metrics
- Dashboard updated with new visualization

Related: #45
```

**Example 2: Bug Fix**
```
fix: Correct profit margin calculation for discounted orders

Profit margin was not accounting for discount impact.
Updated formula: (Sales - Discount*Sales - Cost) / Sales

Fixes #78
```

**Example 3: Documentation**
```
docs: Update installation troubleshooting section

Added common errors and solutions:
- CSV not found error
- Data type mismatch
- Dashboard loading slowly
```

**Example 4: Simple Fix**
```
fix: Correct region filter tooltip text
```

### Commit Shortcuts

```bash
# Short commit (one line)
git commit -m "feat: Add new dashboard"

# Detailed commit (opens editor)
git commit  # Opens text editor for detailed message

# Quick fix (adds all changes)
git commit -am "fix: Typo in filter label"

# Amend last commit (if not pushed yet)
git commit --amend --no-edit  # Changes files only
git commit --amend -m "New message"  # Changes message
```

---

## 📥 Pull Request Process

### Step 1: Prepare Your Branch

```bash
# Ensure your branch is up-to-date
git fetch origin
git rebase origin/main

# Push to GitHub
git push origin feature/your-feature

# If rebase caused conflicts, force push carefully:
git push origin feature/your-feature --force-with-lease
```

### Step 2: Create Pull Request

**On GitHub**:
1. Click **"Compare & Pull Request"** button
2. Or: Go to **Pull Requests** → **New Pull Request**

### Step 3: Fill PR Template

```markdown
## Description
Brief description of changes

## Type of Change
- [x] New feature/dashboard
- [ ] Bug fix
- [ ] Documentation update
- [ ] Performance improvement

## Related Issues
Closes #123

## Testing
How was this tested?
- [x] Tested with all filter combinations
- [x] Verified data accuracy
- [x] Checked dashboard performance
- [x] Reviewed visualizations

## Screenshots
[Optional: Add screenshot of new dashboard]

## Checklist
- [x] Documentation updated
- [x] No breaking changes
- [x] Tested thoroughly
- [x] Commit messages clear
```

### Step 4: Request Review

1. Assign reviewers (right sidebar)
2. Add labels (optional): `bug`, `enhancement`, `documentation`
3. Add to project (optional)

### Step 5: Address Feedback

When reviewer requests changes:

```bash
# Make changes
# ... edit files ...

# Stage and commit
git add .
git commit -m "fix: Address PR feedback from review"

# Push to same branch (automatically updates PR)
git push origin feature/your-feature

# Conversation updates automatically
# No need to create new PR
```

### Step 6: Merge

Once approved:
1. Maintainer clicks **"Merge Pull Request"**
2. Choose merge type:
   - **Squash & Merge**: Combine all commits into one (recommended)
   - **Create Merge Commit**: Preserve all commits
   - **Rebase & Merge**: Rebase on main

3. Delete branch (automatically offered)

---

## 🛠️ Common Git Commands

### Status & Info

```bash
# Show repository status
git status

# Show git log (commit history)
git log
git log --oneline  # Shorter format
git log --graph --oneline --all  # Visual branch history

# Show changes in working directory
git diff

# Show changes between branches
git diff main feature/dashboard
```

### Branching

```bash
# List branches
git branch  # Local only
git branch -a  # All (local + remote)

# Create branch
git branch feature/new-feature

# Switch branch
git checkout feature/new-feature

# Create and switch
git checkout -b feature/new-feature

# Delete branch
git branch -d feature/old-feature
git branch -D feature/old-feature  # Force delete

# Rename branch
git branch -m old-name new-name
```

### Changes

```bash
# Stage files
git add .  # All files
git add filename.txt  # Specific file
git add data/  # Entire folder

# Unstage files
git reset HEAD filename.txt

# Discard changes (WARNING: permanent!)
git checkout -- filename.txt  # Single file
git reset --hard HEAD  # All files

# See what's staged
git diff --staged
```

### Commit & History

```bash
# Commit
git commit -m "message"

# Amend last commit (before pushing)
git commit --amend

# Undo last commit (keep changes)
git reset HEAD~1

# Revert commit (create new commit that undoes it)
git revert HEAD
```

### Push & Pull

```bash
# Pull latest changes
git pull origin main

# Push changes
git push origin feature/branch-name

# Push all branches
git push origin --all

# Force push (use carefully!)
git push origin feature/branch-name --force-with-lease
```

### Stashing (Temporary Storage)

```bash
# Save uncommitted changes temporarily
git stash

# List stashed changes
git stash list

# Apply stashed changes
git stash pop  # Latest stash
git stash apply stash@{0}  # Specific stash

# Delete stash
git stash drop stash@{0}
```

### Merging & Rebasing

```bash
# Merge branch into main
git checkout main
git merge feature/branch-name

# Rebase (cleaner history)
git checkout feature/branch-name
git rebase main

# Interactive rebase (squash commits)
git rebase -i HEAD~3  # Last 3 commits
```

---

## 🚨 Troubleshooting

### Problem: "fatal: not a git repository"

**Cause**: Not in Git project directory

```bash
# Solution: Navigate to project folder
cd ecommerce-tableau-analysis

# Or initialize new repo
git init
git remote add origin https://github.com/username/repo.git
```

### Problem: Merge Conflicts

**Cause**: Same file changed in different branches

```bash
# 1. See conflicted files
git status

# 2. Open file and resolve conflicts (manually edit)
# Look for: <<<<< main | ===== | >>>>> feature/branch

# 3. Choose which version to keep
# Delete conflict markers

# 4. Stage resolved files
git add resolved_file.txt

# 5. Complete merge
git commit -m "Resolve merge conflicts"
```

### Problem: "Your branch is ahead of 'origin/main'"

**Cause**: Local commits not pushed

```bash
# Push commits
git push origin feature/branch-name

# Or reset if you want to discard
git reset --hard origin/main  # WARNING: Loses local work
```

### Problem: "Permission denied" when pushing

**Cause**: SSH key not configured or wrong credentials

```bash
# Option 1: Use HTTPS with personal access token
git remote set-url origin https://github.com/username/repo.git
git push  # Will prompt for token

# Option 2: Configure SSH
# Follow: https://docs.github.com/en/authentication/connecting-to-github-with-ssh
```

### Problem: Large file rejected

**Cause**: File too large for GitHub (>100MB)

```bash
# Solution 1: Use Git LFS (Large File Storage)
git lfs install
git lfs track "*.hyper"  # For Tableau extracts
git add .gitattributes
git commit -m "Configure Git LFS"

# Solution 2: Add to .gitignore
echo "*.hyper" >> .gitignore
git add .gitignore
git commit -m "Ignore large Tableau files"
```

### Problem: Accidentally committed sensitive data

**Cause**: Password, API key, or credentials committed

```bash
# URGENT: Rotate credentials immediately!

# Option 1: Remove from recent commit (not pushed yet)
git reset HEAD~1
git checkout -- sensitive_file.txt
git commit -m "Remove sensitive data"

# Option 2: Remove from history (pushed)
# Use git-filter-repo or BFG
# See: https://help.github.com/en/articles/removing-sensitive-data-from-a-repository
```

---

## 📚 Git Resources

### Learning
- [GitHub Learning Lab](https://lab.github.com)
- [Git Official Documentation](https://git-scm.com/doc)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
- [Pro Git Book](https://git-scm.com/book/en/v2) (Free)

### Tools
- **GitHub Desktop**: Visual Git client
- **GitKraken**: Advanced Git UI
- **SourceTree**: Free Git client
- **VS Code**: Built-in Git support

### References
- [GitHub Guides](https://guides.github.com)
- [GitHub Docs](https://docs.github.com)
- [Conventional Commits](https://www.conventionalcommits.org)

---

## 📝 Cheat Sheet

```bash
# SETUP
git clone <url>
git config --global user.name "Name"

# CREATE BRANCH
git checkout -b feature/name

# MAKE CHANGES
git status
git add .
git commit -m "feat: description"

# PUSH & REVIEW
git push origin feature/name
# Create PR on GitHub

# AFTER APPROVAL
git checkout main
git pull origin main
git branch -d feature/name

# EMERGENCY UNDO
git reset --hard HEAD~1  # Undo last commit
git reflog  # See all changes (recovery)
```

---

## ✅ Best Practices

1. **Commit Often**: Small, logical commits (not huge changes)
2. **Clear Messages**: Write descriptive commit messages
3. **Stay Updated**: Pull before working on long tasks
4. **One Feature**: One branch = one feature
5. **Test Before Pushing**: Verify changes work
6. **Review Your Own PR First**: Check before requesting review
7. **Be Responsive**: Address feedback promptly
8. **Document Changes**: Update README/docs with changes

---

**Version**: 1.0  
**Last Updated**: December 2024  
**Maintained By**: Project Team  

For questions, check GitHub Issues or README FAQ section.
