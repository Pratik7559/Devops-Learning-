# ⎈ Helm Zero to Hero

## What is Helm?

Helm is a package manager for Kubernetes. It helps you define, install, upgrade, and manage Kubernetes applications using reusable packages called **Charts**.

## Why Helm?

- Kubernetes package management
- Reusable configurations
- Templating
- Versioning
- Easy installation and upgrades
- Rollbacks
- Environment-specific configuration

## Helm Architecture

```text
Developer → Helm CLI → Helm Chart → Kubernetes API → Kubernetes Cluster
```

## Important Concepts

### Chart
A Chart is a package containing Kubernetes resource definitions and configuration.

```text
myapp/
├── Chart.yaml
├── values.yaml
├── charts/
└── templates/
```

### Release
A Release is a deployed instance of a Helm Chart in a Kubernetes cluster.

### Repository
A Helm Repository stores and distributes Helm Charts.

## Chart Structure

```text
myapp/
├── Chart.yaml
├── values.yaml
├── charts/
├── templates/
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── ingress.yaml
│   └── _helpers.tpl
└── .helmignore
```

## Chart.yaml

Contains chart metadata:

```yaml
apiVersion: v2
name: myapp
description: My Kubernetes Application
type: application
version: 0.1.0
appVersion: "1.0"
```

## values.yaml

Stores default configuration:

```yaml
replicaCount: 2

image:
  repository: nginx
  tag: latest

service:
  type: ClusterIP
  port: 80
```

## Templates

Helm uses templates to make Kubernetes YAML dynamic:

```yaml
replicas: {{ .Values.replicaCount }}
```

Example:

```yaml
image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
```

## Install Helm

Check installation:

```bash
helm version
helm help
```

Use the official Helm installation method for your operating system and current release.

## Create a Chart

```bash
helm create myapp
```

## Common Commands

```bash
helm list
helm list -A
helm search repo nginx
helm repo add <name> <repository-url>
helm repo update
helm install myapp ./myapp
helm install myapp ./myapp -n dev --create-namespace
helm upgrade myapp ./myapp
helm uninstall myapp
helm show values ./myapp
helm template myapp ./myapp
helm lint ./myapp
helm package ./myapp
```

## Custom Values

Using `--set`:

```bash
helm install myapp ./myapp --set replicaCount=3
```

Using a values file:

```bash
helm install myapp ./myapp -f values-prod.yaml
```

## Multiple Environments

```text
myapp/
├── Chart.yaml
├── values.yaml
├── values-dev.yaml
├── values-stage.yaml
└── values-prod.yaml
```

Deploy:

```bash
helm install myapp ./myapp -f values-dev.yaml
helm install myapp ./myapp -f values-prod.yaml
```

## Upgrade and Rollback

```bash
helm upgrade myapp ./myapp
helm history myapp
helm rollback myapp 1
```

## Dry Run and Rendering

```bash
helm install myapp ./myapp --dry-run
helm template myapp ./myapp
```

## Dependencies

Dependencies can be defined in `Chart.yaml`.

```yaml
dependencies:
  - name: redis
    version: "20.x.x"
    repository: "https://charts.example.com"
```

Update dependencies:

```bash
helm dependency update
```

## Helm Hooks

Hooks can run at lifecycle events such as:

- pre-install
- post-install
- pre-upgrade
- post-upgrade
- pre-delete
- post-delete

Example:

```yaml
metadata:
  annotations:
    "helm.sh/hook": pre-install
```

## Helm in CI/CD

```text
Developer
   ↓
GitHub
   ↓
Jenkins / GitHub Actions
   ↓
Build
   ↓
Test
   ↓
SonarQube
   ↓
Trivy
   ↓
Docker Image
   ↓
Container Registry
   ↓
Helm
   ↓
Kubernetes / EKS
```

## Helm + Jenkins

Example:

```groovy
stage('Deploy') {
    steps {
        sh 'helm upgrade --install myapp ./helm/myapp'
    }
}
```

## Helm + GitHub Actions

```bash
helm lint ./helm/myapp
helm upgrade --install myapp ./helm/myapp
```

## Helm vs kubectl

| Helm | kubectl |
|---|---|
| Kubernetes package manager | Kubernetes CLI |
| Uses Charts | Works directly with Kubernetes resources |
| Templating | No Helm templating |
| Release management | Resource management |

## Helm vs Kustomize

| Helm | Kustomize |
|---|---|
| Package manager | Configuration customization tool |
| Uses templates | Uses overlays/patches |
| Charts | Base + overlays |
| Releases | No Helm-style releases |

## Best Practices

- Keep charts small and reusable.
- Use meaningful chart versions.
- Keep environment-specific values separate.
- Never hardcode secrets in charts.
- Validate charts with `helm lint`.
- Render templates before deployment.
- Test upgrades and rollbacks.
- Store charts in Git.
- Use CI/CD for consistent deployments.

## Interview Questions

1. What is Helm?
2. Why is Helm used with Kubernetes?
3. What is a Helm Chart?
4. What is a Helm Release?
5. What is `values.yaml`?
6. What is `Chart.yaml`?
7. What is Helm templating?
8. Helm vs kubectl?
9. How do you install a Helm chart?
10. How do you upgrade a Helm release?
11. How do you rollback a Helm release?
12. What is `helm template`?
13. What is `helm lint`?
14. What are Helm repositories?
15. What are Helm hooks?
16. How do you manage Dev, Stage, and Production with Helm?
17. How do you integrate Helm with Jenkins?
18. How do you integrate Helm with GitHub Actions?
19. Helm vs Kustomize?
20. How do you handle secrets in Helm?

## Learning Checklist

- [ ] Install Helm
- [ ] Charts
- [ ] Releases
- [ ] Repositories
- [ ] Create a Chart
- [ ] Chart.yaml
- [ ] values.yaml
- [ ] Templates
- [ ] helm install
- [ ] helm upgrade
- [ ] helm rollback
- [ ] helm template
- [ ] helm lint
- [ ] Multiple environments
- [ ] Dependencies
- [ ] Hooks
- [ ] Jenkins Integration
- [ ] GitHub Actions Integration
- [ ] Real Kubernetes Project

---

## 🎯 DevOps Takeaway

**Kubernetes manages containerized workloads, while Helm makes Kubernetes applications easier to package, configure, version, install, upgrade, and rollback.**
