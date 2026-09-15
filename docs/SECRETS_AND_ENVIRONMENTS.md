# Secrets and Environment Strategy

## Environments

Use three logical environments where appropriate:

- `development` — local/non-production work.
- `staging` — production-like verification.
- `production` — live customer-facing services.

Do not represent environments with long-lived Git branches. `main` remains the source branch for releasable code.

## Secret storage

- Never commit secrets, passwords, API keys, private tokens or production credentials.
- Keep example configuration in `.env.example` or equivalent with placeholders only.
- Store CI/CD secrets in GitHub repository or environment secrets as appropriate.
- Prefer environment-scoped secrets for production credentials.
- Use least-privilege credentials and separate production from non-production credentials.
- Prefer short-lived credentials or workload identity/OIDC where deployment providers support it.

## Production controls

- Restrict who can modify production secrets.
- Require stronger deployment approval for production once more maintainers are present.
- Rotate credentials immediately if accidental exposure is suspected.
- Review unused secrets and integrations periodically.

## Naming

Use clear uppercase names such as:

- `DEPLOY_API_TOKEN`
- `DATABASE_URL`
- `EMAIL_API_KEY`

Do not encode secret values in workflow files, source files or documentation.
