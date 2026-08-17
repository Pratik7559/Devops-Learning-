# 🚀 GitHub Actions Zero to Hero

## What is GitHub Actions?
GitHub Actions is a CI/CD and automation platform built into GitHub. It can automatically build, test, scan, package, and deploy applications when events occur in a repository.

## Why GitHub Actions?
- Continuous Integration
- Continuous Delivery
- Automated Testing
- Build Automation
- Docker Image Build
- Security Scanning
- Cloud Deployment
- Scheduled Automation

## Architecture

```text
Developer → Git Push / Pull Request → GitHub Repository
                         ↓
                 GitHub Actions Workflow
                         ↓
                    Job → Steps
                         ↓
              Build / Test / Scan / Deploy
```

## Workflow

Workflow files are stored in:

```text
.github/workflows/
```

Example:

```text
.github/
└── workflows/
    └── ci.yml
```

## Events

Events define when a workflow runs.

```yaml
on:
  push:
    branches: [main]

  pull_request:
    branches: [main]
```

Common events:
- push
- pull_request
- workflow_dispatch
- schedule
- release

## Jobs

A workflow contains one or more jobs.

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
```

## Steps

A job contains individual steps.

```yaml
steps:
  - name: Checkout
    uses: actions/checkout@v4

  - name: Run tests
    run: npm test
```

## Runners

A runner is the machine that executes the workflow.

```yaml
runs-on: ubuntu-latest
```

Common runners:
- Ubuntu
- Windows
- macOS

## Basic Workflow Example

```yaml
name: CI Pipeline

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

## Actions

Actions are reusable units of automation.

```yaml
uses: actions/checkout@v4
```

## Run Commands

```yaml
steps:
  - name: Build
    run: mvn clean package
```

Multiple commands:

```yaml
run: |
  mvn clean
  mvn test
  mvn package
```

## Environment Variables

```yaml
env:
  APP_ENV: production
```

## GitHub Secrets

Never hardcode passwords, API keys, AWS credentials, or tokens.

```yaml
env:
  AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
  AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```

## CI/CD Workflow

```text
Git Push
   ↓
GitHub Actions
   ↓
Checkout
   ↓
Build
   ↓
Unit Test
   ↓
SonarQube
   ↓
Trivy Scan
   ↓
Docker Build
   ↓
Push to ECR
   ↓
Deploy to Kubernetes / EKS
```

## GitHub Actions + Maven

```yaml
name: Java CI

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Set up Java
        uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: "21"

      - name: Build with Maven
        run: mvn clean package
```

## GitHub Actions + Docker

```yaml
- name: Build Docker image
  run: docker build -t myapp:latest .

- name: Push image
  run: docker push myapp:latest
```

## GitHub Actions + Trivy

```text
Build → Trivy Scan → If Secure → Push Image → Deploy
```

## Job Dependencies

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo "Build"

  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - run: echo "Deploy"
```

## Artifacts

Artifacts allow workflow-generated files to be stored and shared.

Examples:
- Test reports
- Build packages
- Logs
- JAR files

## Matrix Strategy

Run the same job against multiple versions:

```yaml
strategy:
  matrix:
    node-version: [18, 20, 22]
```

## Manual Workflow

```yaml
on:
  workflow_dispatch:
```

## Scheduled Workflow

```yaml
on:
  schedule:
    - cron: "0 0 * * *"
```

## GitHub Actions vs Jenkins

| Feature | GitHub Actions | Jenkins |
|---|---|---|
| Platform | GitHub integrated | Standalone |
| Configuration | YAML | Jenkinsfile / UI |
| Infrastructure | GitHub-hosted or self-hosted runners | Controller + agents |
| Setup | Easy for GitHub projects | More infrastructure |
| CI/CD | Yes | Yes |

## Best Practices

- Keep workflows in `.github/workflows/`.
- Never hardcode secrets.
- Use GitHub Secrets.
- Carefully manage Action versions.
- Keep workflows reusable.
- Use branch protection.
- Add automated tests.
- Add security scanning.
- Use separate deployment environments where appropriate.

## Interview Questions

1. What is GitHub Actions?
2. What is a workflow?
3. What is a job?
4. What is a step?
5. What is a runner?
6. What is an Action?
7. Difference between `run` and `uses`?
8. What are GitHub Secrets?
9. What is `workflow_dispatch`?
10. What is `needs`?
11. What is a matrix strategy?
12. GitHub Actions vs Jenkins?
13. Where are workflow files stored?
14. How do you build and push a Docker image?
15. How do you integrate Trivy into GitHub Actions?

## Learning Checklist

- [ ] GitHub Actions Basics
- [ ] Workflow
- [ ] Events
- [ ] Jobs
- [ ] Steps
- [ ] Runners
- [ ] Actions
- [ ] YAML
- [ ] Secrets
- [ ] Artifacts
- [ ] Matrix Strategy
- [ ] Manual Workflows
- [ ] Scheduled Workflows
- [ ] Maven CI
- [ ] Docker CI/CD
- [ ] Trivy Security Scan
- [ ] AWS Deployment
- [ ] Kubernetes Deployment

---

## 🎯 DevOps Takeaway

GitHub Actions can automate the complete software delivery lifecycle directly from a GitHub repository — from code checkout and testing to security scanning, containerization, and deployment.
