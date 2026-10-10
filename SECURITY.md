# Security and privacy

AHSIN is a personal research lab. Test only on systems and in spaces where you have authorization and participant consent.

## Public repository rules

Do not commit credentials, tokens, private keys, populated environment files, IP or MAC addresses, SSIDs, private hostnames, personal contact details, raw packet captures, databases, or unreviewed logs and screenshots.

Use logical service and node names. Keep the mapping to real devices private. The `.gitignore` file reduces accidental inclusion; it is not a substitute for reviewing staged content and images.

If a credential has appeared in a screenshot or a commit, rotate it. Removing a file from the current branch does not erase its prior Git history or cached copies. Avoid posting the sensitive value in an issue.

## Runtime principles

- Restrict development services to the intended lab environment.
- Configure authentication and topic permissions for broker deployments that require them.
- Keep agent planning separate from permission to execute tools.
- Require explicit authorization for consequential external actions.
- Retain useful diagnostics without collecting unnecessary personal data.

Sensing outputs are experimental. They are not medical measurements or a basis for safety-critical decisions.

## Reporting

For a public issue, describe the affected component and general concern without private details or exploit material. If a private reporting channel is available on the repository, use it for sensitive information. Do not attach live credentials or raw personal data.
