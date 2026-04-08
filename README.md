# CubeMart Auth Service

![CubeMart](https://img.shields.io/badge/CubeMart-Auth-0f766e)
![Python](https://img.shields.io/badge/Python-Service-3776AB)
![JWT](https://img.shields.io/badge/JWT-Authentication-1f2937)

Authentication microservice for user registration, login, and JWT validation in the CubeMart platform.

## Responsibilities

- Register new users
- Validate login credentials
- Issue and verify JWT tokens
- Connect to the backing PostgreSQL user store

## Required Environment Variables

| Variable | Required | Description | Example |
|---|---|---|---|
| `PORT` | No | HTTP port used by the Flask service. Defaults to `8081` when not set. | `8081` |
| `AWS_ACCESS_KEY_ID` | Depends | AWS access key for reading the database secret when not using an IAM role. | `AKIA...` |
| `AWS_SECRET_ACCESS_KEY` | Depends | AWS secret key for reading the database secret when not using an IAM role. | `********` |
| `AWS_SESSION_TOKEN` | Depends | Temporary session token for short-lived AWS credentials, if used. | `IQoJ...` |

## Runtime Configuration Notes

- The service reads database and JWT configuration from the AWS Secrets Manager secret `authservice/db_credentials`.
- Secrets are fetched from the `ap-northeast-1` region.
- The database TLS certificate is expected at `/certs/global-bundle.pem`.
- If the service is running on AWS with an attached IAM role, explicit AWS credential environment variables may not be needed.
