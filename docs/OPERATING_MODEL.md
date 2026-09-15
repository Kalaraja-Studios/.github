# Kalaraja Studios GitHub Operating Model

## Ownership and access

- Organisation owners are limited to people who require organisation-wide administration.
- Day-to-day repository access should use the least privilege needed.
- Developers normally receive `Write`; technical leads may receive `Maintain`; `Admin` is restricted.
- Contractors should be granted access only to the repositories they need.
- Shared human accounts are not permitted.
- Two-factor authentication should be required for all organisation members.

## Branching and reviews

- `main` is the default branch and should remain deployable.
- Work is performed on short-lived `feature/`, `fix/` or `chore/` branches.
- Changes merge through pull requests.
- Squash merge is the preferred merge strategy.
- PR titles and final commits follow Conventional Commits.
- Security-sensitive and production-impacting changes require explicit review.

## Repository standards

- Native web standards are preferred: HTML5, CSS and JavaScript.
- Reusable UI is implemented with standards-based Web Components.
- Progressive enhancement is the default approach.
- WCAG 2.2 AA is the accessibility baseline.
- Tests accompany behaviour changes.
- Secrets are never committed.

## Environments and secrets

Use logical environments such as `development`, `staging` and `production` without representing them as long-lived Git branches.

- Local development uses documented example environment files with non-secret placeholders.
- Repository or environment secrets hold deploy-time credentials.
- Production credentials use least privilege and should be rotated when exposure is suspected.
- Production deployments should require stronger controls than development or staging.

## CI/CD

Every production repository should progressively adopt checks for:

1. Build/install integrity.
2. Unit/integration tests.
3. End-to-end tests where relevant.
4. Accessibility checks.
5. Dependency/security checks.
6. Deployment verification.

Only successful reviewed changes from `main` should progress to production.

## Dependency management

- Automated dependency update tooling should be enabled.
- Dependency updates must pass CI before merging.
- High-severity vulnerabilities take priority over routine feature work.

## Reviews

Review organisation access, repository visibility, branch rules, Actions permissions, secrets, integrations and dependency alerts periodically and after significant staffing or platform changes.
