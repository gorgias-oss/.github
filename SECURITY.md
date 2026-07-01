# Security Policy

## Reporting a vulnerability

If you believe you have found a security issue in any repository under this organization,
**please do not open a public GitHub issue.** Instead, email a description to:

**security@gorgias.com**

Include:

- The repository name and version (tag, commit, or release) affected.
- A description of the vulnerability and its potential impact.
- Steps to reproduce — a minimal config, code sample, or proof-of-concept.
- Any relevant logs or stack traces, **with secrets redacted**.

We aim to acknowledge reports within **2 business days** and to provide a fix
or mitigation timeline within **10 business days** for confirmed issues.
Issues affecting credential confidentiality or unauthorized resource access
are triaged immediately.

You will receive credit in the release notes for any accepted report, unless
you prefer to remain anonymous.

## Scope

In scope:

- Any code, configuration, or documentation that ships in a repository under
  the [gorgias-oss](https://github.com/gorgias-oss) organization.

Out of scope:

- Vulnerabilities in upstream services or APIs that a tool wraps — report
  those to the respective vendor.
- Vulnerabilities in third-party dependencies — report to the upstream
  maintainer. We will pick up fixes via dependency updates.
- Vulnerabilities in platforms or frameworks (Terraform, HashiCorp Vault,
  etc.) — report to the respective project.

## What we treat as a security issue

- **Credential disclosure** — any path by which secrets (API tokens,
  passwords, private keys, cloud-provider credentials) can be written to
  logs, persisted in plaintext where unexpected, sent in cleartext over the
  wire, or leaked in error messages.
- **Injection** — command injection, path traversal, header injection, or
  any flow where user-controlled input reshapes an API call in an
  unintended way.
- **Authentication or authorization bypass** — operations that take
  destructive or privileged actions against resources the operator did not
  explicitly declare or own.
- **Race conditions** — concurrent-execution scenarios that produce
  orphaned resources, lost state, or cross-tenant interference.
- **Cryptographic misuse** — improper TLS configuration, skipped certificate
  validation, weak random sources for generated credentials, etc.

## Supported versions

Each repository documents its own supported version range. As a general
policy, only the latest release of a repository receives security fixes until
it reaches a stable `1.0.0`. After `1.0.0`, the current and previous minor
releases are supported.

Check the individual repository's `SECURITY.md` or `README.md` for the
version support table specific to that project.
