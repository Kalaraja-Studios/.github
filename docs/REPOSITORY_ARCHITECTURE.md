# Kalaraja Studios Repository Architecture

## Current product repositories

- `kalaraja-pwa` — public-facing Kalaraja Studios progressive web application.
- `launch-ready` — launch readiness assessment product.
- `digital-audit` — paid digital audit product.
- `.github` — organisation profile, engineering standards, templates and shared workflow guidance.

## Planned shared repositories

Create these when shared code and infrastructure justify independent ownership:

- `design-system` — design tokens, typography, spacing, icons and UI patterns.
- `shared-components` — framework-free reusable Web Components.
- `infrastructure` — deployment configuration, infrastructure-as-code and environment templates.

## Dependency direction

Shared assets should flow one way:

`design-system` → `shared-components` → product repositories

Product repositories must not depend directly on one another. Integrations should use documented URLs, APIs or shared packages rather than cross-repository source imports.

## Standard repository shape

Application repositories should converge on:

```text
src/
tests/
docs/
public/
scripts/
.github/
README.md
.editorconfig
.gitignore
```

Organisation-level community health files live in `.github` and are inherited by repositories that do not provide their own versions.

## Versioning

Repositories version independently using semantic versioning where releases are published. Do not force unrelated products to share a release number.
