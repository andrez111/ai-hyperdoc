# Security Policy

## Scope

This repository currently contains procedural instructions and metadata, not an executable application or network service.

Security-relevant reports may still include:

- instructions that could cause an agent to expose private conversation content;
- changes that silently weaken the rule against false rename claims;
- prompt-injection patterns that materially alter classification behavior;
- future executor code that could rename, read, or modify conversations outside the intended scope;
- credentials, tokens, or private endpoints accidentally committed to the repository.

## Reporting

Do not open a public issue containing credentials, private conversation data, or an exploitable vulnerability.

Use the repository owner's private contact method on GitHub for sensitive reports.

For ordinary behavioral bugs that do not expose private information, a public issue is appropriate.

## Supported versions

Until the project reaches a stable release, security fixes target the latest version on the default branch.
