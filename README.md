# Config-Repository

Centralized, environment-neutral configuration consumed by the Cloud Health Config Server.

## About

This repository is part of the Cloud Health Project for ITS 2130 Enterprise Cloud Architecture. The production Config Server clones this repository from GitHub, while runtime addresses and credentials remain external environment variables.

## Tech Stack

| Technology | Details |
|---|---|
| YAML | Spring application configuration |
| Git / GitHub | Versioned configuration source |
| Spring Cloud Config | Configuration consumer |
| Environment variables | Runtime-specific values and secret references |

## Configuration Files

| File | Purpose |
|---|---|
| `application.yml` | Shared Eureka, Actuator, liveness, and readiness settings |
| `discovery-server.yml` | Eureka Server behavior |
| `api-gateway.yml` | Routes for the three domain services |
| `patient-service.yml` | PostgreSQL, JPA, Flyway, and graceful shutdown |
| `diagnostics-service.yml` | MongoDB, automatic indexes, and graceful shutdown |
| `file-service.yml` | Cloud Storage, Firestore, upload limits, and signed URLs |

## Repository Details

| Property | Value |
|---|---|
| Repository | `Cloud-Health-Project-Platform-Config-Repository` |
| Default branch | `main` |
| Configuration format | YAML |
| Secret storage | Environment variables / Google Secret Manager |

## Security

Never commit database passwords, MongoDB connection strings, service-account keys, access tokens, or patient data. Values such as `${PATIENT_DB_PASSWORD}` and `${DIAGNOSTICS_MONGODB_URI}` are placeholders resolved only at runtime.

## Getting Started

Publish these files at the root of the GitHub repository. Then configure the Config Server:

```bash
export SPRING_PROFILES_ACTIVE=git
export CONFIG_GIT_URI=https://github.com/YOUR_USERNAME/Cloud-Health-Project-Platform-Config-Repository.git
export CONFIG_GIT_BRANCH=main
```

Verify through Config Server:

```text
http://localhost:8888/patient-service/default
```

## Project Details

| Property | Value |
|---|---|
| Student | Hiruna Dissanayake |
| Student number | `24171104` |
| GCP project | `cloud-health-506015-hiruna` |
