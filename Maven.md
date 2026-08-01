# ☕ Maven Zero to Hero

## What is Maven?

Apache Maven is a build automation and dependency management tool for
Java projects.

## Why Maven?

-   Build Automation
-   Dependency Management
-   Standard Project Structure
-   Testing
-   Packaging
-   Deployment

## Components

-   pom.xml
-   Local Repository
-   Central Repository
-   Remote Repository
-   Plugins

## Lifecycle

-   validate
-   compile
-   test
-   package
-   verify
-   install
-   deploy

## Project Structure

project/ - src/main/java - src/main/resources - src/test/java - pom.xml

## Common Commands

``` bash
mvn -version
mvn clean
mvn compile
mvn test
mvn package
mvn install
mvn clean install
mvn dependency:tree
```

## Dependency Scopes

-   compile
-   provided
-   runtime
-   test

## Best Practices

-   Use latest stable dependencies
-   Keep pom.xml clean
-   Use parent POM
-   Use plugins

## Interview Questions

-   What is Maven?
-   What is pom.xml?
-   Maven lifecycle?
-   What is dependency scope?
-   install vs package?
-   Local vs Central repository?

## Checklist

-   [ ] Installation
-   [ ] pom.xml
-   [ ] Lifecycle
-   [ ] Dependencies
-   [ ] Plugins
-   [ ] Jenkins Integration
