# Contributing to Kalaraja Studios

These standards apply across Kalaraja Studios repositories unless a repository documents a stricter rule.

## Engineering principles

- Prefer native HTML5, CSS and JavaScript.
- Use standards-based Web Components for reusable UI.
- Build with progressive enhancement.
- Target WCAG 2.2 AA accessibility.
- Prefer semantic HTML before ARIA.
- Do not use deprecated browser APIs.
- Never commit secrets, credentials or environment-specific private values.
- Keep code explicit, readable and single-purpose.
- Add or update tests when behaviour changes.
- Treat accessibility, security and performance regressions as defects.

## Branches

Use short-lived branches from `main`:

- `feature/<short-description>`
- `fix/<short-description>`
- `chore/<short-description>`

`main` should remain deployable. Do not use long-lived `develop`, `staging` or release branches unless a repository explicitly needs them.

## Commits

Use Conventional Commits:

`<type>[optional scope]: <description>`

Supported types:

- `feat` — new functionality
- `fix` — bug fix
- `docs` — documentation only
- `style` — formatting only
- `refactor` — restructuring without behaviour change
- `perf` — performance improvement
- `test` — test changes
- `build` — build/dependency changes
- `ci` — CI/CD changes
- `chore` — maintenance
- `revert` — revert an earlier change

Examples:

- `feat(readiness): add RAG scoring calculation`
- `fix(a11y): restore keyboard focus after modal closes`
- `test(pwa): add offline navigation coverage`
- `ci(playwright): run end-to-end tests on pull requests`

Use `!` or a `BREAKING CHANGE:` footer for breaking changes.

## Pull requests

PR titles should follow Conventional Commits. Every PR should explain:

1. What changed?
2. Why was it changed?
3. How was it tested?
4. Are there accessibility implications?
5. Are there security implications?
6. Are there deployment or configuration changes?

The default merge strategy is squash merge so the final commit history remains clean.

## Definition of Done

A change is complete when:

- The requirement is implemented.
- Relevant automated tests pass.
- No known console errors are introduced.
- Accessibility has been considered and tested.
- Security implications have been reviewed.
- Responsive behaviour has been tested where relevant.
- Browser support requirements are maintained.
- Documentation is updated where necessary.
- CI has passed.
- Required review has been completed.
- The change can be safely deployed from `main`.
