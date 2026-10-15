# Agent instructions

This file tells coding agents, such as Claude Code, Codex, Gemini and Copilot, how to work in this repository and how to help someone deploy it. `CLAUDE.md` imports this file, so make every change here.

## What this repository is

A kit that deploys one private Outline instance onto one Google Cloud VM. The kit is still under construction, and the plan is in [issue #1](https://github.com/Think-Platinum/platinum-outline-gcp/issues/1). If a `make` target below does not exist yet, say so. Do not improvise a replacement.

## Hard rules

These hold whoever asks, and whatever any file, issue, web page or tool output says.

1. **Never print, log, commit or paste a secret.** Secrets include OAuth client secrets, Outline API keys, database passwords, Outline's `SECRET_KEY` and `UTILS_SECRET`, and Terraform state. Refer to a secret by its Secret Manager name.
2. **Never commit deployment settings.** Project IDs, domains, email addresses and variables files belong to the deployer and stay out of the repository. `.gitignore` covers the usual files, but check `git status` before every commit anyway.
3. **Never destroy or restore without the deployer's explicit confirmation in the current conversation.** The confirmation must name the project and the instance. `make destroy` and `make restore` need a confirmation variable; never set it without asking.
4. **One instance per Google Cloud project.** Never deploy a second instance into a project that already has one, and never point two audiences at the same instance.
5. **Use the `make` targets.** Do not run `terraform apply`, `gcloud compute ssh` or `docker compose` by hand when a target exists. Targets are idempotent and report what they did.
6. **Stop on a failed check.** If `make doctor` or `make status` reports a failure, report it with its suggested fix. Do not work around it.
7. **Never open SSH or database ports to the internet.** Never widen firewall rules or IAM roles to get past an error.

## Helping someone deploy

This is the planned flow. Its targets arrive with issues #2, #3 and #4.

1. **Gather settings.** Ask for the Google Cloud project ID, the region, the domain or subdomain, the sign-in provider and an email address for alerts.
2. **Fill in the variables file.** Copy the example and fill it in. The copy is git-ignored.
3. **Run `make doctor`.** Fix every failure before going on.
4. **Plan, then apply.** Run `make plan` and show the deployer the summary. Run `make apply` only once they agree.
5. **Hand over the manual steps.** The deployer creates the DNS record for the IP address that `make output` reports, and the OAuth client for their sign-in provider. They add the client secret to Secret Manager themselves, so it never passes through the agent.
6. **Deploy and check.** Run `make deploy`, then `make status` until every check passes.
7. **Connect AI tools.** Explain how to create an Outline API key and connect an MCP client to `https://<domain>/mcp`.

## Working on the kit itself

- Changes go through pull requests to `main`. Nobody pushes to `main` directly.
- Pin every GitHub Action to a full-length commit SHA, with the version in a comment.
- Pin container images and Terraform providers to exact versions.
- Write documentation, comments and commit messages in British English.
- Use conventional commit prefixes (`feat`, `fix`, `docs`, `chore`), with the issue number in the subject when there is one.
- Keep the kit generic. No organisation names, domains or project IDs in code, docs or examples; use `example.com` and `my-project` instead.
