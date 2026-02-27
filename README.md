# TP DevSecOps avec Docker

![Build and Scan](https://github.com/Oscar45160/devops-tp-docker-oscar/actions/workflows/docker-deploy.yml/badge.svg)
![CodeQL](https://github.com/Oscar45160/devops-tp-docker-oscar/actions/workflows/codeql-analysis.yml/badge.svg)

## Pipeline DevSecOps

Ce projet implémente un pipeline CI/CD sécurisé pour Docker avec :

- Analyse statique du code (CodeQL)
- Lint du Dockerfile (Hadolint)
- Scan de l'image Docker (Trivy)
- Scan des dépendances (Dependabot)
- Secret Scanning
- Security Gates (blocage sur vulnérabilités critiques)
- SBOM (Software Bill of Materials)

## Architecture de Sécurité

```
Code → SAST → Hadolint → Build → Trivy → Security Gates → GHCR
```

## Sécurité de l'Image

- Image de base : nginx:alpine (version spécifique)
- Utilisateur non-root
- Headers de sécurité renforcés
- Health checks
- Pas de secrets dans l'image

## Exécution Locale

```bash
docker pull ghcr.io/oscar45160/devops-tp-docker-oscar:main
docker run -p 8080:8080 ghcr.io/oscar45160/devops-tp-docker-oscar:main
```

Accéder à : http://localhost:8080

## Scan de Sécurité Local

```bash
trivy image ghcr.io/oscar45160/devops-tp-docker-oscar:main
```