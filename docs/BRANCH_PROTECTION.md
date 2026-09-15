# Branch and Pull Request Protection Standard

Apply these rules to `main` on production repositories.

## Required controls

- Require a pull request before merging.
- Require at least one approving review once another trusted maintainer is available.
- Dismiss stale approvals when new commits materially change the PR.
- Require review of CODEOWNERS-owned files where practical.
- Require conversation resolution before merge.
- Require status checks to pass before merge once CI checks are active.
- Require branches to be up to date before merge when this does not create excessive friction.
- Block force pushes to `main`.
- Block deletion of `main`.
- Restrict direct pushes to `main`.
- Allow squash merging as the default merge method.

## Administrator behaviour

Owners and administrators should follow the same PR workflow for normal development. Emergency bypass should be rare, documented and followed by retrospective review.

## Initial status checks

When active, protect `main` using the stable CI checks produced by each repository. Do not mark a check as required until it is reliable and consistently available on pull requests.

## Branch naming

Use short-lived branches:

- `feature/<description>`
- `fix/<description>`
- `chore/<description>`
