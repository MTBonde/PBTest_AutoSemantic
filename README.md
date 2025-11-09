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
package was build v0.2.0, which is not what was expected
What happened:
- Expectation: first commit using feat: would result in minor bump v0.0.0 -> v0.1.0 therefor a package(first release)
- Reality: Step 1.1 created v0.1.0, Step 1.3 created v0.2.0
- Root cause: allow-initial-development-versions: true creates v0.1.0 from ANY commit type for the very first release
Learned:
- This is actually GOOD - v0.1.0 represents "walking skeleton" (initial setup)
- Industry standard: React, Vue, Kubernetes all started with 0.x.x versions
- 0.x.x = pre-release/development phase, 1.0.0 = production-ready
- The quirk is expected behavior for establishing baseline version

---

### Step 1.4: The v1.0.0 Discovery
**What I did**: Changed allow-initial-development-versions from true to false, then committed documentation
**Commits**:
```
fix: add CHANGELOG.md auto-commit and set allow-initial to false
docs: document allow-initial-development-versions discovery and results
```

**Expected result**:
- v0.2.0 -> v0.2.1 (PATCH bump from fix:)
- docs: commit creates no release

**Actual result**:
- v0.2.0 -> v1.0.0 (MAJOR bump - graduated to production!)
- Switching from true to false caused project to "graduate" from pre-release (0.x.x) to production-ready (1.x.x)
- CHANGELOG.md now appears in repo (auto-commit works!)

**What I learned**:
- Changing allow-initial from true→false triggers v1.0.0 graduation
- This is semantically correct: leaving 0.x (development) for 1.x (production)
- For future projects: decide upfront whether to use 0.x.x or 1.x.x
- Best practice: Start with true (0.x.x) and graduate to 1.0.0 when API stabilizes
- CHANGELOG.md is now versioned in repo, not just in GitHub Releases

---

### Step 1.5: Test PATCH Release (Bug Fix)
**What I did**: commit a empty Fix to trigger PATCH version bump
**Commit**:
```
fix: something was fixed, patch bump expected
```

**Expected result**:
- Release created: v1.0.1 (PATCH bump from v1.0.0)
- Bug fix triggers PATCH increment
- CHANGELOG.md updated with fix entry
- GitHub Release v1.0.1 appears

**Actual result**:
worked as planned.
---
