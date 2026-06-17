# 📅 Day 20 — GitHub Actions, GitLab CI & Git-Driven DevOps Automation ⚙️🚀

Welcome back, Jeevan!

Congratulations! 🎉

You have reached the final day of your 20-day Git, GitHub, and GitLab mastery journey.

So far, you have learned:

✅ Git fundamentals
✅ Branching and merging
✅ Conflict resolution
✅ Rebase and cherry-pick
✅ Pull Requests and Merge Requests
✅ Branch protection
✅ Tags and releases

Today, you will learn how Git becomes the engine that powers DevOps automation.

---

# 🎯 Today's Goals

By the end of Day 20, you will:

✅ Understand CI/CD concepts

✅ Learn how Git triggers automation

✅ Create your first GitHub Actions workflow

✅ Create your first GitLab CI pipeline

✅ Understand common DevOps pipeline stages

✅ Learn real-world DevOps automation workflows

---

# 🧠 1️⃣ Concept — What is CI/CD?

## Continuous Integration (CI)

Developers frequently merge code changes into a shared repository.

Every change automatically triggers:

* Code validation
* Testing
* Security scans
* Build processes

Goal:

```text
Detect problems early.
```

---

## Continuous Delivery (CD)

After successful testing, applications are automatically prepared for deployment.

Goal:

```text
Deploy quickly and reliably.
```

---

## Continuous Deployment

Every validated change is automatically deployed to production.

Goal:

```text
No manual deployment steps.
```

---

# 🔄 Git-Driven Automation Workflow

```text
Developer
   ↓
Git Commit
   ↓
Push to GitHub/GitLab
   ↓
CI/CD Pipeline Starts
   ↓
Build
   ↓
Test
   ↓
Security Scan
   ↓
Deploy
```

Git events trigger everything.

---

# 🔹 Common Pipeline Triggers

* Push to branch
* Pull Request / Merge Request
* Tag creation
* Scheduled execution
* Manual execution

---

# 🏗️ Common Pipeline Stages

```text
Source → Build → Test → Scan → Deploy
```

Example:

```text
Code
 ↓
Build Docker Image
 ↓
Run Tests
 ↓
Scan for Vulnerabilities
 ↓
Deploy to Server
```

---

# 🖥️ 2️⃣ GitHub Actions Basics (1 Hour)

GitHub Actions workflows are stored in:

```text
.github/workflows/
```

---

## Step 1 — Create Workflow Directory

```bash
mkdir -p .github/workflows
```

---

## Step 2 — Create Workflow File

```bash
nano .github/workflows/basic-ci.yml
```

Add:

```yaml
name: Basic CI Pipeline

on:
  push:
    branches:
      - main

jobs:
  validate:

    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Display Message
        run: echo "CI pipeline started successfully"

      - name: Show Files
        run: ls -la
```

Save and exit.

---

## Step 3 — Commit Changes

```bash
git add .
git commit -m "Added GitHub Actions workflow"
git push origin main
```

---

## Step 4 — Verify Pipeline

Go to:

```text
Repository → Actions
```

You will see your workflow running.

---

# 🔹 Understanding the Workflow

| Keyword   | Purpose                        |
| --------- | ------------------------------ |
| `name`    | Workflow name                  |
| `on`      | Trigger event                  |
| `jobs`    | Tasks to execute               |
| `runs-on` | Runner operating system        |
| `steps`   | Commands executed sequentially |

---

# 🔹 Common GitHub Actions Triggers

Run on pull requests:

```yaml
on:
  pull_request:
```

Run on tags:

```yaml
on:
  push:
    tags:
      - "v*"
```

Run manually:

```yaml
on:
  workflow_dispatch:
```

---

# 🖥️ 3️⃣ GitLab CI Basics (1 Hour)

GitLab pipelines are configured using:

```text
.gitlab-ci.yml
```

in the repository root.

---

## Step 1 — Create File

```bash
nano .gitlab-ci.yml
```

Add:

```yaml
stages:
  - validate

validate_job:

  stage: validate

  script:
    - echo "GitLab CI started"
    - ls -la
```

Commit:

```bash
git add .
git commit -m "Added GitLab CI pipeline"
git push origin main
```

---

## Step 2 — Verify Pipeline

Navigate to:

```text
Build → Pipelines
```

View pipeline execution.

---

# 🔹 GitLab Pipeline Structure

| Keyword  | Purpose         |
| -------- | --------------- |
| `stages` | Pipeline phases |
| `stage`  | Current phase   |
| `script` | Commands to run |

---

# 🔄 Real-World DevOps Pipeline

Most companies use pipelines similar to:

```text
Validate
   ↓
Test
   ↓
Build
   ↓
Security Scan
   ↓
Deploy
```

---

# Example

```text
Terraform Validate
       ↓
Docker Build
       ↓
Unit Tests
       ↓
Container Scan
       ↓
Deploy to Kubernetes
```

---

# 🏷️ Tag-Based Production Deployment

Remember Day 19?

Production deployments often start when tags are created.

Example:

```bash
git tag -a v1.0.0 -m "Production release"
git push origin v1.0.0
```

Pipeline trigger:

```text
Build → Test → Deploy Production
```

---

# 🔹 GitHub Actions Tag Example

```yaml
on:
  push:
    tags:
      - "v*"
```

---

# 🔹 GitLab Tag Example

```yaml
deploy_production:

  stage: deploy

  only:
    - tags

  script:
    - echo "Deploying production release"
```

---

# 🛡️ CI/CD Best Practices

Always include:

✅ Automated testing

✅ Security scanning

✅ Code review before merge

✅ Branch protection

✅ Version tagging

---

Never:

❌ Deploy directly from local machine

❌ Bypass CI/CD

❌ Store secrets in Git

❌ Disable validation checks

---

# 🔐 Managing Secrets

Do NOT store:

```text
password=admin123
api_key=abcdef
```

inside repositories.

Use:

* GitHub Secrets
* GitLab CI/CD Variables

---

## GitHub Secrets

Navigate:

```text
Repository
  ↓
Settings
  ↓
Secrets and Variables
  ↓
Actions
```

---

## GitLab Variables

Navigate:

```text
Settings
  ↓
CI/CD
  ↓
Variables
```

---

# 🛠️ 4️⃣ Real-World DevOps Scenario (30 min)

Scenario:

You update a Dockerfile.

Workflow:

```text
Create Feature Branch
       ↓
Push Changes
       ↓
Pull Request
       ↓
CI Pipeline Runs
       ↓
Code Review
       ↓
Merge
       ↓
Tag Release
       ↓
Deploy Production
```

Git drives the entire process.

---

# 📘 5️⃣ Important Files Learned Today

| File                      | Purpose                 |
| ------------------------- | ----------------------- |
| `.github/workflows/*.yml` | GitHub Actions workflow |
| `.gitlab-ci.yml`          | GitLab pipeline         |
| `CODEOWNERS`              | Automatic reviewers     |
| `.gitignore`              | Ignore sensitive files  |

---

# 🧪 6️⃣ Final Hands-On Challenge

Create a repository called:

```text
devops-git-lab
```

Complete these tasks:

### Challenge 1

Initialize repository:

```bash
git init
```

---

### Challenge 2

Create:

```text
README.md
Dockerfile
.github/workflows/basic-ci.yml
```

---

### Challenge 3

Push to GitHub.

---

### Challenge 4

Enable branch protection.

---

### Challenge 5

Create feature branch:

```bash
git switch -c feature/docker-update
```

---

### Challenge 6

Commit and push changes.

---

### Challenge 7

Create Pull Request.

---

### Challenge 8

Merge PR.

---

### Challenge 9

Create release tag:

```bash
git tag -a v1.0.0 -m "Initial release"
git push origin v1.0.0
```

---

### Challenge 10

Verify CI/CD pipeline execution.

---

# 💡 DevOps Tips of the Day

## 🔹 Tip 1 — Git Is the Single Source of Truth

Everything should live in Git:

* Infrastructure code
* Dockerfiles
* Kubernetes manifests
* CI/CD pipelines
* Documentation

---

## 🔹 Tip 2 — Automate Repetitive Tasks

If you repeat a task manually:

```text
More than twice
```

consider automating it.

---

## 🔹 Tip 3 — Keep Pipelines Fast

Good pipelines:

```text
5–10 minutes
```

Long pipelines reduce developer productivity.

---

# 🔥 Common Interview Questions

### Q1: What triggers a CI/CD pipeline?

**Answer:**

* Push events
* Pull Requests / Merge Requests
* Tags
* Schedules
* Manual triggers

---

### Q2: Where are GitHub Actions workflows stored?

**Answer:**

```text
.github/workflows/
```

---

### Q3: What is the GitLab CI configuration file?

**Answer:**

```text
.gitlab-ci.yml
```

---

### Q4: Why should secrets never be stored in Git?

**Answer:**

Because repository history is permanent and exposed to collaborators.

Use secret management solutions instead.

---

### Q5: What is the role of Git in DevOps?

**Answer:**

Git acts as the central source of truth and triggers automation pipelines for building, testing, and deploying applications and infrastructure.

---

# 🏆 Congratulations, Jeevan!

You have completed your **20-Day Git, GitHub, and GitLab Mastery Journey.**

You now understand:

✅ Git fundamentals

✅ Branching strategies

✅ Collaboration workflows

✅ Release management

✅ GitHub and GitLab features

✅ CI/CD automation basics

These are the exact Git skills expected from junior DevOps engineers.

---

# 🚀 Next Step in Your DevOps Journey

Now apply Git to:

* Docker
* Terraform
* Ansible
* Kubernetes
* Jenkins
* GitHub Actions
* GitLab CI/CD

Every DevOps tool you learn from now on should be version-controlled in Git.

Keep using Git daily until these commands become muscle memory.
