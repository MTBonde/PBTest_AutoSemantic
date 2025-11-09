# PBTest_AutoSemantic

## Overview

Repository for learning and testing automatic semantic versioning with go-semantic-release.

### Repositories

- **[PBTest_AutoSemantic](https://github.com/MTBonde/PBTest_AutoSemantic)** (this repo): Learn automatic semantic versioning with go-semantic-release
- **[PBTest_GitOps](https://github.com/MTBonde/PBTest_GitOps)**: Learn GitOps workflows and environment promotion
- **[PBTest_Infra](https://github.com/MTBonde/PBTest_Infra)**: Learn Infrastructure as Code with Terraform 
## How I'm Using This Repository

This README.md file serves as my **learning journal**. As I work through each step, I'll document:
- What I did in each step
- The commit message I used
- Expected vs. actual results
- What I learned from each step
Each commit to this README will test different commit types (feat, fix, docs, etc.) and demonstrate how semantic versioning works in practice.


### Commit Type Reference Conventional commit:
**Reference**: [Conventional Commits](https://www.conventionalcommits.org/)

| Type       | Description             | Version Bump | Example                            |
|------------|-------------------------|--------------|------------------------------------|
| `feat`     | New feature             | MINOR        | `feat: add user login`             |
| `fix`      | Bug fix                 | PATCH        | `fix: resolve null pointer`        |
| `docs`     | Documentation only      | None         | `docs: update README`              |
| `style`    | Code formatting         | None         | `style: fix indentation`           |
| `refactor` | Code refactoring        | None         | `refactor: extract method`         |
| `perf`     | Performance improvement | PATCH        | `perf: optimize query`             |
| `test`     | Test changes            | None         | `test: add unit tests`             |
| `build`    | Build system changes    | None         | `build: update webpack`            |
| `ci`       | CI configuration        | None         | `ci: add release workflow`         |
| `chore`    | Other changes           | None         | `chore: update dependencies`       |
| `feat!`    | Breaking feature        | MAJOR        | `feat!: change API format`         |
| `fix!`     | Breaking fix            | MAJOR        | `fix!: remove deprecated endpoint` |

**Breaking Changes**: Adding `!` after any commit type (e.g., `feat!:`, `fix!:`, `refactor!:`) triggers a MAJOR version bump. Alternatively, include `BREAKING CHANGE:` in the commit body.

---

## My Learning Journey

### Step 1.1: Initial Workflow Setup
**What I did**: Created GitHub Actions workflow for go-semantic-release
**Commit**:
```
git commit -m "ci: add go-semantic-release workflow"
git push origin main
```
**Expected result**:
- Workflow runs successfully
- No release created (ci: commits don't trigger releases)
- Workflow visible in GitHub Actions tab
**Actual result**:
worked as planned, the pipeline said "no release.."

---

### Step 1.2: Configure .gitignore
**What I did**: Added go-semantic-release cache to .gitignore
**Commit**:
```
git commit -m "chore: add go-semantic-release to gitignore"
```

**Expected result**:
- No release created (chore: commits don't trigger releases)
- Workflow runs successfully

**Actual result**:
worked as planned.
OMFG! jetbrains recognized semantic, so auto added this message: "chore: add go-semantic-release cache to .gitignore and update README documentation"
results will be committed using: "docs: added results"

---

### Step 1.3: First Feature - First Release!
**What I did**: Adding step 1.3 to trigger first semantic release
**Commit**:
```
git commit -m "feat: add step 1.3 documentation"
```

**Expected result**:
- **First release created: v0.1.0**
- GitHub Release appears in Releases tab
- Git tag v0.1.0 created
- CHANGELOG.md file created with entry for this feature

**Actual result**:


---
