# 🤖 Automation Suite Documentation

This repository is equipped with a comprehensive automation suite for CI/CD, dependency management, and repository maintenance.

## 📋 Deployed Workflows

### 1. **Auto-Merge Dependabot PRs** (`.github/workflows/auto-merge.yml`)
- **Trigger:** When Dependabot creates a PR
- **Actions:**
  - Installs dependencies
  - Runs tests (if configured)
  - Builds project (if configured)
  - Auto-merges PRs on successful tests
  - Squashes commits for clean history
  - Adds `automated` and `merged-by-bot` labels

### 2. **Close Stale PRs & Issues** (`.github/workflows/close-stale.yml`)
- **Trigger:** Weekly on Sunday at midnight UTC
- **Actions:**
  - Closes PRs inactive for 6+ months
  - Closes issues inactive for 1+ year
  - Deletes merged branches
  - Posts automated closure comments

### 3. **Continuous Integration** (`.github/workflows/ci.yml`)
- **Trigger:** On push to main/develop/master, on all PRs
- **Actions:**
  - Tests across Node.js 16.x, 18.x, 20.x
  - Runs linting and build scripts
  - CodeQL security analysis
  - Dependency audit checks

### 4. **PR Automation & Triage** (`.github/workflows/pr-triage.yml`)
- **Trigger:** On PR/issue events
- **Actions:**
  - Auto-labels issues (bug, enhancement, documentation)
  - Labels PRs by size (small, medium, large, xlarge)
  - Auto-assigns PRs to authors

### 5. **Repository Maintenance** (`.github/workflows/maintenance.yml`)
- **Trigger:** Daily at 3 AM UTC
- **Actions:**
  - Generates repository statistics
  - Updates STATS.md file
  - Ensures README.md exists
  - Auto-commits metadata updates

## 🔄 Dependabot Configuration

Enhanced `.github/dependabot.yml`:
- **Daily npm updates** - Keeps dependencies current
- **Weekly GitHub Actions updates** - Maintains workflow tools
- **Auto-assigns** to @Corsica88
- **Auto-labels** as `dependencies` and `automated`
- **Squash commits** for clean history
- **50 open PRs limit** - Manages workload

## 📊 Workflow Schedule

| Workflow | Schedule | Purpose |
|----------|----------|---------|
| Auto-Merge | On PR event | Merge safe Dependabot PRs |
| Close Stale | Sunday 00:00 UTC | Weekly cleanup |
| CI/CD | On push/PR | Continuous testing |
| PR Triage | On PR/issue event | Auto-labeling |
| Maintenance | Daily 03:00 UTC | Stats & README |
| Dependabot | Daily 02:00 UTC | Dependency updates |

## 🚀 Features

✅ **Zero-Touch Automation** - Workflows run without manual intervention
✅ **Safe Merging** - Tests run before any auto-merge
✅ **Intelligent Labeling** - Auto-labels by issue type and PR size
✅ **Repository Health** - Automated cleanup and maintenance
✅ **Dependency Security** - Continuous monitoring and updates
✅ **Cross-Version Testing** - Tests on multiple Node.js versions

## 📝 Manual Triggers

Run workflows manually via GitHub CLI:

```bash
# Close stale PRs and issues
gh workflow run close-stale.yml --repo Corsica88/claud-stuff

# Run CI tests
gh workflow run ci.yml --repo Corsica88/claud-stuff

# Run maintenance tasks
gh workflow run maintenance.yml --repo Corsica88/claud-stuff
```

## 🔧 Customization

All workflows are in `.github/workflows/` and can be customized:

- **Disable auto-merge:** Edit `auto-merge.yml`
- **Change stale thresholds:** Edit `close-stale.yml`
- **Add test languages:** Edit `ci.yml`
- **Adjust labels:** Edit `pr-triage.yml`
- **Modify schedules:** Edit cron expressions

## 📞 Support

For issues or modifications:
1. Edit workflow files in `.github/workflows/`
2. Create a PR for testing
3. Merge when verified

---

**Status:** ✅ Active
**Last Deployed:** 2026-06-06
**Maintained By:** @Corsica88
