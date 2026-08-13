# 🛡️ Trivy Zero to Hero

## What is Trivy?

Trivy is an open-source security scanner used in DevSecOps to find vulnerabilities and security issues in container images, filesystems, Git repositories, Kubernetes configurations, Infrastructure as Code (IaC), dependencies, and potential secrets.

## Why Trivy?

- Lightweight
- Fast
- Easy to use
- CI/CD integration
- Container security
- Infrastructure as Code scanning
- Dependency vulnerability scanning

## What Can Trivy Scan?

- Container Images
- Filesystems
- Git Repositories
- Kubernetes configurations
- Terraform / IaC
- Dependencies
- Potential Secrets

## Basic Commands

```bash
trivy --version
trivy image nginx:latest
trivy fs .
trivy config .
trivy k8s .
```

## Container Image Scanning

Scan a Docker image:

```bash
trivy image nginx:latest
```

Trivy can report:

- Vulnerability ID
- Package name
- Severity
- Installed version
- Fixed version (when available)

## Severity Levels

Common severity levels:

- UNKNOWN
- LOW
- MEDIUM
- HIGH
- CRITICAL

Scan only HIGH and CRITICAL vulnerabilities:

```bash
trivy image --severity HIGH,CRITICAL nginx:latest
```

## Filesystem Scanning

Scan a project directory:

```bash
trivy fs .
```

This can identify vulnerable dependencies and other security findings.

## Infrastructure as Code Scanning

Trivy can scan Terraform and other supported IaC configurations.

```bash
trivy config .
```

## Secret Scanning

Trivy can detect potential secrets and sensitive information in supported targets.

Never commit:

- Passwords
- API Keys
- Access Tokens
- Private Keys

## Trivy in CI/CD

Typical DevSecOps workflow:

```text
Developer
    ↓
GitHub
    ↓
CI/CD Pipeline
    ↓
Build
    ↓
Trivy Scan
    ↓
Container Registry
    ↓
Deploy
```

A CI/CD pipeline can be configured to fail when vulnerabilities meet a defined severity threshold.

## Docker + Trivy

Build an image:

```bash
docker build -t myapp:1.0 .
```

Scan it:

```bash
trivy image myapp:1.0
```

The image should be scanned before pushing it to a registry or deploying it.

## Kubernetes + Trivy

Trivy can be used to scan:

- Container images
- Kubernetes configurations
- Workloads
- Security-related configurations

This helps identify security issues before or during Kubernetes deployment workflows.

## Useful Trivy Options

### Severity

```bash
trivy image --severity HIGH,CRITICAL nginx:latest
```

### JSON Output

```bash
trivy image --format json nginx:latest
```

### Exit Code

```bash
trivy image --exit-code 1 nginx:latest
```

This can be useful in CI/CD pipelines to fail a build when findings are detected.

### Ignore Unfixed Vulnerabilities

```bash
trivy image --ignore-unfixed nginx:latest
```

## Trivy + Jenkins

Example CI/CD flow:

```text
GitHub
   ↓
Jenkins
   ↓
Build Docker Image
   ↓
Trivy Scan
   ↓
If Secure → Push Image
   ↓
Deploy
```

Trivy can be added as a security stage in a Jenkins pipeline.

## Trivy + GitHub Actions

Example workflow:

```text
Developer
   ↓
Git Push
   ↓
GitHub Actions
   ↓
Build
   ↓
Trivy Scan
   ↓
Push / Deploy
```

## Best Practices

- Scan container images before deployment.
- Use trusted and minimal base images.
- Keep dependencies updated.
- Fix HIGH and CRITICAL vulnerabilities promptly.
- Integrate Trivy into CI/CD.
- Avoid committing secrets.
- Define an acceptable vulnerability threshold.
- Scan Infrastructure as Code before deployment.

## DevSecOps Workflow

```text
Code
 ↓
Git
 ↓
Build
 ↓
Security Scan
 ↓
Test
 ↓
Container Image
 ↓
Registry
 ↓
Deployment
 ↓
Kubernetes
```

## Interview Questions

1. What is Trivy?
2. Why is Trivy used in DevSecOps?
3. How do you scan a Docker image using Trivy?
4. What is filesystem scanning?
5. How do you scan Terraform files?
6. What are Trivy severity levels?
7. How can Trivy fail a CI/CD pipeline?
8. What is the purpose of `--exit-code`?
9. How can Trivy be integrated with Jenkins?
10. How can Trivy be integrated with GitHub Actions?
11. How is Trivy useful with Kubernetes?
12. Why should container images be scanned before deployment?

## Learning Checklist

- [ ] Install Trivy
- [ ] Scan Docker Images
- [ ] Understand Severity Levels
- [ ] Scan Filesystems
- [ ] Scan Git Repositories
- [ ] Scan Terraform / IaC
- [ ] Scan for Secrets
- [ ] Integrate with Jenkins
- [ ] Integrate with GitHub Actions
- [ ] Add Trivy to a DevSecOps Pipeline

---

## 🎯 DevSecOps Takeaway

**Trivy brings security scanning into the development and CI/CD workflow, helping DevOps teams identify vulnerabilities and insecure configurations before production deployment.**
