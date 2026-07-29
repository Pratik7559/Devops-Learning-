# Jenkins Zero to Hero

## What is Jenkins?

Jenkins is an open-source automation server for CI/CD.

## Features

-   Continuous Integration
-   Continuous Delivery
-   Automation
-   Pipelines
-   Plugins

## Architecture

-   Controller
-   Agent
-   Executor
-   Workspace

## Installation

``` bash
sudo apt update
sudo apt install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

## Jenkinsfile Example

``` groovy
pipeline {
  agent any
  stages {
    stage('Build'){ steps{ echo 'Build'} }
    stage('Test'){ steps{ echo 'Test'} }
    stage('Deploy'){ steps{ echo 'Deploy'} }
  }
}
```

## Common Commands

``` bash
systemctl status jenkins
journalctl -u jenkins
cat /var/lib/jenkins/secrets/initialAdminPassword
```

## Workflow

Developer -\> GitHub -\> Jenkins -\> Build -\> Test -\> Deploy

## Interview Questions

-   What is Jenkins?
-   What is CI/CD?
-   Pipeline vs Freestyle?
-   Agent vs Controller?
-   Jenkinsfile?
-   Plugins?
-   Shared Library?

## Checklist

-   [ ] Install Jenkins
-   [ ] Create Job
-   [ ] Pipeline
-   [ ] GitHub Integration
-   [ ] Docker
-   [ ] Kubernetes
