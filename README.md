# Liatrio Apprenticeship Interview Exercise

This repository contains my work for the Liatrio Apprenticeship Interview Exercise!

The goal of the project is to build a simple Go web application, containerize it w/ Docker, create a CI/CD workflow using GitHub Actions, and deploy the application to a cloud platform.

---

## Application

The application is written in Go using the Fiber web framework.

The application exposes a single endpoint:

```text
GET /

## CI/CD

`.github/workflows/ci.yml` runs on every push to `main`. It builds the Docker image, runs it, checks it with Liatrio's `apprentice-action`, pushing it to Docker Hub if everything has passed.

`.github/workflows/deploy.yml` runs after CI succeeds. It deploys the same SHA-tagged image from Docker Hub to AWS ECS Express Mode. It signs in to AWS with OpenID Connect, so no AWS keys are stored in GitHub.

The AWS service is only kept running for testing and demos.