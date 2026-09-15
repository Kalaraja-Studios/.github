# Kalaraja Studios Rollback Runbook

This runbook applies to Kalaraja Studios applications deployed from GitHub to Cloudflare Pages.

## When to roll back

Roll back when a production deployment introduces a critical defect, security issue, broken customer journey, failed payment flow, inaccessible experience, major performance regression, or another issue that cannot be safely fixed forward immediately.

## Immediate response

1. Stop further production changes.
2. Confirm the affected repository and production deployment.
3. Record the incident time, affected URL, symptoms and latest production commit SHA.
4. Decide whether the fastest safe recovery is:
   - redeploying a previously known-good Cloudflare Pages deployment, or
   - reverting the offending Git commit and allowing the normal production pipeline to redeploy.

## Preferred rollback: redeploy a known-good Cloudflare Pages deployment

Use this when the previous deployment was known to be healthy and immediate service restoration is the priority.

1. Open Cloudflare Dashboard.
2. Go to Workers & Pages → the affected Pages project.
3. Open Deployments.
4. Identify the most recent known-good production deployment.
5. Verify its source branch and commit SHA against GitHub.
6. Promote or redeploy that known-good deployment to production using the Cloudflare Pages deployment controls available for the project.
7. Confirm the production custom domain now serves the known-good version.
8. Run the production smoke checks below.
9. Keep the incident open until the Git branch state is reconciled so the next deployment does not reintroduce the defect.

## Code-level rollback: revert the offending Git change

Use this when production should be brought back in line with the repository history.

1. Identify the offending commit or merged pull request.
2. Create a short-lived branch from `main`, for example `fix/rollback-production-issue`.
3. Revert the offending commit rather than rewriting shared history.
4. Use a Conventional Commit message, for example:

   `revert: remove production regression introduced by <short-sha>`

5. Open a pull request to `main`.
6. Run required CI and focused regression checks.
7. Merge using the normal squash/review policy unless the incident requires an emergency path.
8. Confirm Cloudflare Pages creates and completes the production deployment from the corrected `main` branch.
9. Run the production smoke checks below.

## Production smoke checks after rollback

At minimum verify:

- `https://kalarajastudios.co.uk` loads successfully.
- HTTPS certificate is valid.
- `www` and HTTP redirects behave as configured.
- Homepage and primary navigation work.
- Launch Readiness entry path works when deployed.
- Digital Audit entry path works when deployed.
- Forms and critical calls to action work.
- Payment or checkout journeys work where enabled.
- Authentication works where enabled.
- No new JavaScript console errors block core journeys.
- No obvious accessibility regression affects keyboard or screen-reader use.
- PWA shell/offline behaviour still works where applicable.

## Data and schema changes

A code rollback does not automatically reverse database, KV, Durable Object, R2, D1 or third-party data changes.

Before rolling back a release that changes persistent data:

1. Check whether the earlier application version is compatible with the current data/schema.
2. Do not run destructive reverse migrations without a reviewed recovery plan.
3. Prefer backward-compatible migrations and forward fixes where possible.
4. Restore from a verified backup only when necessary and authorised.

## Secrets and configuration

If an incident was caused by configuration rather than code:

1. Restore the last known-good environment variable, secret, binding or Cloudflare setting.
2. Never copy secret values into GitHub issues, Asana, logs or chat.
3. Rotate a secret immediately if exposure is suspected.
4. Redeploy if Cloudflare requires a new deployment for the configuration change to take effect.

## After recovery

1. Record the failed deployment and recovered deployment/commit SHAs.
2. Document the root cause.
3. Add or improve an automated test that would have caught the regression where practical.
4. Review whether monitoring, preview testing, accessibility checks, security checks or release controls need improvement.
5. Confirm `main` matches the intended production state.
6. Close the incident only after production is stable.

## Rule

Do not use force-push or rewrite `main` history as a normal rollback mechanism. Prefer Cloudflare redeployment of a known-good build for immediate recovery and a Git revert for durable repository correction.
