# Commits and branches naming best practices 

## 1.	Git commit messages : Best practices
Standard types help automation (e.g., changelogs, versioning):
- feat: a new feature
- fix: a bug fix
- docs: documentation changes
- style: formatting only (no code change)
- refactor: code change that doesn’t fix a bug or add a feature
- test: adding or refactoring tests
- chore: changes to build process or tools
- perf: performance improvements
- ci: CI/CD-related changes
- revert: revert a previous commit

## 2.	Git branch naming 

### a.	General Rules

- Use lowercase letters.
- Use hyphens (-) instead of spaces or underscores.
- Use slash-separated prefixes to categorize branches.
- Be descriptive but concise.

### b.	Common Naming Patterns

| Branch Type | Naming Convention | Example |
|:-----------|:------------:|------------:|
| Feature      | `feature/<short-description>`       | `feature/login-api`       |
| Bugfix     | `bugfix/<issue-or-description>`         | `bugfix/typo-homepage`      |
| Hotfix      | `hotfix/<critical-issue>`       | `hotfix/payment-crash`       |
| Release     | `release/<version>`         | `release/1.3.0`       |
| Experiment      | `experiment/<idea>`       | `experiment/new-layout`       |
| Chore/infra     | `chore/<task>`         | `chore/update-deps`       |

### c. Pro Tip: Add Ticket/Issue IDs

```bash
feature/123-add-user-profile
bugfix/456-fix-navbar
```

### d. Example Workflow

```bash
# Create a new feature branch
git checkout -b feature/search-filter

# Create a bugfix branch
git checkout -b bugfix/null-pointer-exception

# Push to remote with upstream
git push --set-upstream origin feature/search-filter
```

### e. Optional: Protect Your `main` and `develop` Branches

In a team:
- Keep `main` for production.
- Use `develop/dev` for integration/testing.
- Feature branches are merged into `develop/dev`, not `main`.
