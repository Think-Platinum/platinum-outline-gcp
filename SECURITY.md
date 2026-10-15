# Security policy

## Reporting a vulnerability

Report security vulnerabilities privately through GitHub's [private vulnerability reporting](https://github.com/Think-Platinum/platinum-outline-gcp/security/advisories/new). Do not open a public issue, pull request or discussion about a suspected vulnerability.

Please include:

- what is affected: a file, a `make` target or a default setting
- how to reproduce it
- the impact you expect

We will acknowledge your report and keep you informed while we investigate. If you would like, we will credit you in the advisory.

## Scope

**In scope:** the code and default configuration in this repository. That covers the Terraform, Compose files, scripts and workflows, and any documented default that would leave a deployment exposed.

**Out of scope:**

- Vulnerabilities in Outline itself. Report those to the Outline project through [its security policy](https://github.com/outline/outline/security/policy).
- Vulnerabilities in Google Cloud, Docker, PostgreSQL, Redis or Caddy. Report those to their maintainers.
- Problems in a deployment whose operator has changed the defaults.

## Supported versions

Only the latest commit on `main` is supported. Fixes are not backported.

## Never share secrets

Do not paste API keys, OAuth client secrets, database passwords or Terraform state into an issue or a report. If you have exposed a secret, rotate it first.
