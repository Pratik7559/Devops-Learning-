# 🔍 SonarQube Zero to Hero

## What is SonarQube?

SonarQube is a code quality and security platform used to continuously inspect source code and identify bugs, vulnerabilities, code smells, duplicated code, and maintainability issues.

## Why SonarQube?

- Improve code quality
- Detect bugs early
- Find security vulnerabilities
- Detect code smells
- Measure code coverage
- Reduce technical debt
- Integrate quality checks into CI/CD

## SonarQube Architecture

```text
Developer
    ↓
GitHub
    ↓
CI/CD
    ↓
SonarScanner
    ↓
SonarQube Server
    ↓
Database
    ↓
Quality Gate
    ↓
Deploy
```

## Important Components

### SonarQube Server
Main platform that receives and displays code analysis results.

### SonarScanner
Analyzes source code and sends the analysis results to SonarQube.

### Database
Stores SonarQube analysis data and configuration.

### Quality Profile
Defines the rules that are applied while analyzing source code.

### Quality Gate
Defines whether the analyzed code meets the required quality conditions.

## Common Code Issues

### Bug
A problem that can cause incorrect application behavior.

### Vulnerability
A security weakness that can potentially be exploited.

### Code Smell
A maintainability problem that makes code harder to understand or maintain.

### Code Duplication
Repeated code that can increase maintenance effort.

### Code Coverage
The percentage of code that is covered by automated tests.

## Maven Integration

For Maven projects, SonarQube analysis can be executed using:

```bash
mvn clean verify sonar:sonar
```

## Jenkins + SonarQube

Typical CI/CD flow:

```text
GitHub
   ↓
Jenkins
   ↓
Maven Build
   ↓
SonarQube Analysis
   ↓
Quality Gate
   ↓
Trivy Scan
   ↓
Docker Build
   ↓
Deploy
```

SonarQube can therefore act as a code-quality/security checkpoint in a Jenkins pipeline.

## Docker Installation

For learning purposes, SonarQube can be run using Docker:

```bash
docker run -d   --name sonarqube   -p 9000:9000   sonarqube:lts-community
```

Then access SonarQube through port `9000`.

## SonarQube + DevSecOps

SonarQube is commonly placed early in a CI/CD pipeline so that code-quality and security issues can be detected before production deployment.

A typical DevSecOps flow:

```text
Code
 ↓
Git
 ↓
Build
 ↓
SonarQube
 ↓
Trivy
 ↓
Docker Image
 ↓
Registry
 ↓
Deployment
```

## SonarQube vs Trivy

| Tool | Main Focus |
|---|---|
| SonarQube | Source code quality and code security analysis |
| Trivy | Container, dependency, filesystem, IaC and security scanning |

## Best Practices

- Run SonarQube analysis regularly.
- Use Quality Gates.
- Fix critical issues first.
- Track technical debt.
- Keep Quality Profiles appropriate for the project.
- Integrate SonarQube into CI/CD.
- Combine SonarQube with dependency and container scanning.
- Do not expose SonarQube publicly without proper security controls.

## Interview Questions

1. What is SonarQube?
2. Why is SonarQube used in CI/CD?
3. What is SonarScanner?
4. What is a Quality Gate?
5. What is a Quality Profile?
6. What is a Bug?
7. What is a Vulnerability?
8. What is a Code Smell?
9. What is Code Coverage?
10. How do you integrate SonarQube with Jenkins?
11. How do you integrate SonarQube with Maven?
12. SonarQube vs Trivy?
13. What happens when a Quality Gate fails?
14. How can SonarQube be used in DevSecOps?

## Learning Checklist

- [ ] Install SonarQube
- [ ] Understand SonarQube Projects
- [ ] Understand Quality Profiles
- [ ] Configure Quality Gates
- [ ] Install/use SonarScanner
- [ ] Integrate SonarQube with Maven
- [ ] Integrate SonarQube with Jenkins
- [ ] Integrate SonarQube with GitHub Actions
- [ ] Understand Code Coverage
- [ ] Add SonarQube to a complete CI/CD pipeline

---

## 🎯 DevOps Takeaway

**SonarQube helps DevOps teams continuously inspect source code for quality and security issues and provides an important quality-control stage in modern CI/CD and DevSecOps pipelines.**
