# Security Policy

Kalaraja Studios treats security issues as confidential until assessed and resolved.

## Reporting a vulnerability

Do not open a public GitHub issue for suspected vulnerabilities, exposed credentials, authentication weaknesses, data exposure or other security-sensitive findings.

Report security concerns privately to the Kalaraja Studios owner through the organisation's published business contact channel. Include:

- The affected repository or service.
- A concise description of the issue.
- Steps to reproduce where safe.
- Potential impact.
- Any suggested remediation.

Do not include live secrets, personal data or unnecessary sensitive information in the report.

## Handling

Kalaraja Studios will:

1. Acknowledge and triage the report.
2. Assess severity and affected systems.
3. Contain or revoke exposed credentials immediately where required.
4. Implement and verify a fix.
5. Document the remediation and any preventive actions.

## Repository requirements

- Secrets and credentials must never be committed to source control.
- Production values must be supplied through approved environment or secret-management mechanisms.
- Dependencies should be kept current and reviewed for known vulnerabilities.
- Security-relevant changes should receive explicit review.
- CI/CD credentials should use least privilege and short-lived credentials where practical.
