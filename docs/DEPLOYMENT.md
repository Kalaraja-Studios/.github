# Deployment Workflow Standard

Kalaraja Studios repositories should use automated, repeatable deployments rather than manual file copying.

## Recommended flow

1. Create a short-lived branch from `main`.
2. Open a pull request.
3. Run CI and quality checks.
4. Review and squash merge to `main`.
5. Deploy the merged commit to staging where applicable.
6. Promote the same tested commit/artifact to production.
7. Run post-deployment smoke checks.

## Principles

- Production deploys originate from reviewed code on `main`.
- Build once and promote the same artifact where the platform supports it.
- Keep deployment credentials in environment-scoped secrets.
- Prefer provider integrations or OIDC over long-lived tokens.
- Production should have stronger controls than development/staging.
- Rollback procedures must be documented before a critical production launch.

## Repository-specific configuration

Each product repository should document its hosting provider, build command, output directory, environment variables, deployment trigger and rollback path once those choices are finalised.
