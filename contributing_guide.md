# Contributing to Global E-Commerce Sales Dashboard

Thank you for your interest in contributing! This project welcomes contributions from data analysts, Tableau developers, and business intelligence professionals. Here's how to get involved.

---

## 📋 Table of Contents

1. [Code of Conduct](#code-of-conduct)
2. [Types of Contributions](#types-of-contributions)
3. [Getting Started](#getting-started)
4. [Development Workflow](#development-workflow)
5. [Commit Message Guidelines](#commit-message-guidelines)
6. [Submitting Changes](#submitting-changes)
7. [Review Process](#review-process)
8. [Questions?](#questions)

---

## 🤝 Code of Conduct

### Our Commitment
We are committed to providing a welcoming and inspiring community for all. Please read and adhere to our [Code of Conduct](CODE_OF_CONDUCT.md).

**Expected Behavior**:
- Be respectful and inclusive
- Provide constructive feedback
- Accept criticism gracefully
- Focus on what is best for the community
- Show empathy toward other community members

**Unacceptable Behavior**:
- Harassment, intimidation, or discrimination
- Offensive comments or personal attacks
- Public or private harassment
- Publishing private information without consent
- Other conduct unethical or unprofessional

---

## 🎯 Types of Contributions

We welcome contributions in these areas:

### 1. Bug Reports & Fixes
- Found an issue with the dashboard?
- Spotted data inconsistencies?
- Create an issue with details and submit a fix

**How to Report**:
1. Check if bug already reported in [Issues](https://github.com/your-username/ecommerce-tableau-analysis/issues)
2. If not, create new issue with title, description, steps to reproduce, and expected behavior
3. Include screenshots if applicable
4. Submit pull request with fix

### 2. Documentation Improvements
- Unclear instructions?
- Missing details?
- Enhance README, guides, or comments

**Areas for Improvement**:
- Installation steps
- Dashboard explanations
- Data dictionary clarity
- Analysis methodology
- Troubleshooting guides

### 3. New Visualizations & Dashboards
- New insights to surface?
- Additional metrics to track?
- Propose new dashboard pages

**Requirements**:
- Aligns with business questions
- Uses existing or well-sourced data
- Includes clear business rationale
- Includes documentation

### 4. Data Enhancements
- New data sources to integrate?
- Improved data quality processes?
- Additional calculated fields?

**Requirements**:
- Maintains data integrity
- Documented source and methodology
- Backward compatible with existing analysis

### 5. Performance Optimization
- Slow dashboard loading?
- Inefficient calculations?
- UI/UX improvements?

**Focus Areas**:
- Dashboard load times
- Extract optimization
- Filter efficiency
- Visual hierarchy clarity

### 6. Accessibility Improvements
- Color blindness considerations?
- Keyboard navigation?
- Screen reader compatibility?

---

## 🚀 Getting Started

### Prerequisites
- **Tableau Desktop** 2024.1+ (or latest version)
- **Git** for version control
- **GitHub Account** for collaboration
- **Basic knowledge** of Tableau and data analysis
- **Familiarity** with this project's structure

### Fork the Repository
```bash
# 1. Click "Fork" button on GitHub
# 2. Creates your own copy of the project

# 3. Clone your fork locally
git clone https://github.com/YOUR-USERNAME/ecommerce-tableau-analysis.git
cd ecommerce-tableau-analysis

# 4. Add upstream remote
git remote add upstream https://github.com/ORIGINAL-OWNER/ecommerce-tableau-analysis.git
```

### Set Up Your Environment
```bash
# 1. Create feature branch
git checkout -b feature/your-feature-name

# 2. For Tableau work:
# - Open Tableau Desktop
# - File → Open → Navigate to project folder
# - Select workbook file

# 3. For documentation/scripts:
# - Use any text editor (VS Code recommended)
# - Python 3.8+ for script development
```

---

## 💻 Development Workflow

### Before Making Changes

1. **Sync with Latest**
   ```bash
   git fetch upstream
   git checkout main
   git merge upstream/main
   ```

2. **Create Feature Branch**
   ```bash
   # Use descriptive name
   git checkout -b feature/dashboard-enhancement
   git checkout -b fix/discount-calculation
   git checkout -b docs/update-readme
   ```

### Making Changes

#### For Tableau Workbook Modifications

1. **Open the workbook**
   - File → Open → ecommerce_sales_analysis.twb
   - Wait for data source connection

2. **Make your changes**
   - Edit dashboards/sheets as needed
   - Test all interactive elements
   - Verify filters work across all dashboards
   - Check data accuracy

3. **Save frequently**
   - Ctrl+S (Windows) or Cmd+S (Mac)
   - Keep file as .twb (not .twbx) for version control

4. **Test thoroughly**
   - Apply all filter combinations
   - Verify dashboard performance
   - Check tooltips and formatting
   - Validate calculations

5. **Backup before major changes**
   - File → Save As → ecommerce_sales_analysis_backup_[DATE].twbx

#### For Documentation/Code Changes

1. **Edit files** in your text editor
2. **Follow style guide** (see below)
3. **Test** (run scripts if applicable)
4. **Verify** changes don't break anything

### Style Guide

#### Markdown Documentation
```markdown
# Heading 1 (One # for main titles)

## Heading 2 (Two ## for sections)

### Heading 3 (Three ### for subsections)

- Use bullet points for lists
- Keep lines under 100 characters
- Use code blocks for technical content

**Bold** for emphasis
*Italic* for definitions
`Inline code` for variables
```

#### Calculated Fields (Tableau)
- Name clearly: `[Profit Margin %]` not `pm`
- Add description: Profit / Sales
- Comment any complex logic
- Test with edge cases (zero sales, negative profits)

#### Python Scripts
- Follow PEP 8 style guide
- Add docstrings to functions
- Include comments for complex logic
- Use meaningful variable names

---

## 📝 Commit Message Guidelines

### Format
```
type: brief description

Optional detailed explanation

Related issues: #123, #456
```

### Type Categories
- **feat**: New feature or visualization
- **fix**: Bug fix
- **docs**: Documentation changes
- **style**: Formatting, no logic changes
- **refactor**: Code/dashboard restructuring
- **perf**: Performance improvement
- **test**: Test additions or modifications
- **chore**: Maintenance tasks

### Examples

**Good Commit Messages**:
```
feat: Add customer cohort analysis dashboard

- New dashboard showing customer retention by acquisition year
- Includes 3 new calculated fields for cohort metrics
- Adds drill-down capability to customer details

Related issues: #42
```

```
fix: Correct profit margin calculation for discounted orders

Profit margin was not accounting for discount impact.
Formula updated: (Sales - Discount - Cost) / Sales

Fixes #78
```

```
docs: Update installation guide for Tableau 2024.1

- Add screenshot of data source connection
- Clarify troubleshooting section
- Add FAQ for common errors
```

### Bad Commit Messages ❌
```
"fixed stuff"
"updates"
"changes"
"WIP"
"asdf"
```

---

## 📤 Submitting Changes

### Step 1: Commit Your Work
```bash
# Stage changes
git add .

# Commit with message
git commit -m "feat: Add regional drill-down dashboard"

# Push to your fork
git push origin feature/your-feature-name
```

### Step 2: Create Pull Request
1. Go to GitHub repository
2. Click "New Pull Request"
3. Select your feature branch
4. Fill out PR template:

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation
- [ ] Performance
- [ ] Other: ___

## Testing
How was this tested?

## Screenshots/Visuals
If applicable, add screenshots

## Checklist
- [ ] Tested thoroughly
- [ ] Documentation updated
- [ ] No breaking changes
- [ ] Commit messages clear
- [ ] Tableau file validates
```

### Step 3: Address Feedback
- Reviewer will provide feedback
- Make requested changes
- Push to same branch (automatically updates PR)
- Resolve all conversations

### Step 4: Merge
Once approved:
- Maintainer will merge to main
- Celebrate your contribution! 🎉

---

## 🔍 Review Process

### What Reviewers Look For

#### Tableau Changes
- ✅ Functionality works correctly
- ✅ Dashboard is responsive
- ✅ Filters interact properly
- ✅ Calculations are accurate
- ✅ Performance acceptable
- ✅ Data connections valid
- ✅ UI/UX consistent
- ✅ Tooltips informative

#### Documentation Changes
- ✅ Spelling and grammar
- ✅ Clarity and completeness
- ✅ Accurate information
- ✅ Proper formatting
- ✅ Examples relevant
- ✅ Links functional

#### Code Changes
- ✅ Follows style guide
- ✅ No breaking changes
- ✅ Well-commented
- ✅ Error handling included
- ✅ Tested thoroughly
- ✅ Performance acceptable

### Response Time
- Non-urgent: 3-5 business days
- Urgent/bug fixes: 1-2 business days
- Major features: May require discussion before review

### Approval Requirements
- Minimum 1 approval required
- All conversations must be resolved
- CI checks must pass (if applicable)

---

## 🤔 Questions?

### Getting Help
1. Check [FAQ](docs/FAQ.md)
2. Search [GitHub Issues](https://github.com/your-username/ecommerce-tableau-analysis/issues)
3. Review [Documentation](README.md)
4. Email project maintainer

### Communication Channels
- **GitHub Issues**: For bug reports and feature requests
- **Discussions**: For questions and ideas
- **Email**: For sensitive matters

---

## 📚 Additional Resources

### Learning Resources
- [Tableau Desktop Help](https://help.tableau.com)
- [Git & GitHub Guides](https://guides.github.com)
- [Markdown Guide](https://www.markdownguide.org)
- [Community Best Practices](#)

### Similar Projects
- [Tableau Community Viz Gallery](https://public.tableau.com)
- [Analytics Dashboard Projects](#)

### References
- [Contributor Covenant](https://www.contributor-covenant.org)
- [GitHub Contributing Guide](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions)

---

## 🎓 Contributor Recognition

### Recognition Levels

**All Contributors** recognized in:
- Contributors section of README
- GitHub Contributors page
- Release notes (if applicable)

**Major Contributors** (10+ contributions):
- Listed as project collaborator
- Invited to become maintainer (if interested)
- Featured in project announcements

### How to Get Listed
Contributors are automatically recognized on GitHub. To be included in README:
1. Ensure PR is merged
2. Check contributors page: github.com/[owner]/[project]/graphs/contributors

---

## 📋 Contribution Ideas

### Quick Wins (Great for First Contributors)
- [ ] Add missing documentation
- [ ] Improve README clarity
- [ ] Add FAQ entries
- [ ] Fix typos/grammar
- [ ] Update screenshots

### Medium Complexity
- [ ] Add new visualization
- [ ] Enhance existing dashboard
- [ ] Add calculated field
- [ ] Create tutorial

### Advanced Projects
- [ ] New data source integration
- [ ] Performance optimization
- [ ] Mobile dashboard version
- [ ] Automated testing

---

## ✨ Thank You!

Thank you for considering contributing to this project. Your time and effort help make this a better resource for the entire data community.

**Happy contributing!** 🚀

---

**Last Updated**: December 2024  
**Maintained By**: Project Team  
**Version**: 1.0
