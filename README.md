# platinum-outline-gcp

Deploy a private, single-instance [Outline](https://www.getoutline.com) knowledge base on Google Cloud. You get one VM, your own domain, single sign-on, backups, and Outline's MCP endpoint, so your AI tools can read and write your knowledge base. You can run the setup yourself or hand the repository to a coding agent.

> **Status: under construction.** The kit is being built in the open and is not ready to deploy yet. Follow [the Epic](https://github.com/Think-Platinum/platinum-outline-gcp/issues/1) for progress.

## Design in brief

- One instance per audience, and one Google Cloud project per instance.
- One Compute Engine VM running Outline, PostgreSQL, Redis and Caddy in Docker Compose.
- Only ports 80 and 443 are open; SSH goes through Identity-Aware Proxy; secrets live in Secret Manager.
- The data disk is snapshotted daily and the database is dumped nightly.
- Every step is a `make` target that a person or an agent can run.

## Licence

The code in this repository is licensed under [Apache-2.0](LICENSE).

Outline is a separate product by General Outline, Inc., licensed under the Business Source License 1.1. That licence lets you self-host Outline for your own organisation. It does not let you offer Outline to others as a hosted document service. Read [Outline's licence](https://github.com/outline/outline/blob/main/LICENSE) before you deploy. This project is not affiliated with or endorsed by General Outline, Inc.

## Reporting issues

- **Bugs and feature requests:** [open an issue](https://github.com/Think-Platinum/platinum-outline-gcp/issues/new/choose).
- **Security vulnerabilities:** report them privately, never in a public issue. See [SECURITY.md](SECURITY.md).
