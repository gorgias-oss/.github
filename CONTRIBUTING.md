# Contributing to Gorgias OSS

Thanks for taking the time to contribute. This document covers the general
process for all repositories under [gorgias-oss](https://github.com/gorgias-oss).
Individual repositories may have a more specific `CONTRIBUTING.md` — if one
exists, follow that alongside this document.

## Code of conduct

Be respectful. Assume good intent. Critique code, not people. We follow the
spirit of the [Contributor Covenant](https://www.contributor-covenant.org/).

## Reporting security issues

**Do not file security issues as public GitHub issues.** Email
**security@gorgias.com** instead. See [SECURITY.md](SECURITY.md) for the full
disclosure process.

## Reporting bugs and requesting features

For non-security issues, open a GitHub issue in the relevant repository.
Include:

- The version of the software affected (tag, release, or commit).
- A minimal, self-contained reproduction — the smallest config, command, or
  code that demonstrates the problem.
- The exact error or unexpected behavior, including relevant log output (with
  secrets redacted).
- For feature requests: describe the use case, not just the proposed solution.
  We often have a different implementation approach in mind.

## Making a change

1. **Open an issue first** for anything beyond a small bugfix or documentation
   change. Agree on the approach before investing time writing code.

2. **Fork the repository** and branch from `main` with a descriptive name:

   ```sh
   git checkout -b fix/short-description-of-change
   ```

3. **Make focused commits.** One logical change per commit. Avoid mixing
   refactors with behavior changes — they're harder to review and bisect.

4. **Add or update tests** for any behavior change. A bug fix should include
   a test that fails without the fix.

5. **Run the full suite** before opening a pull request. See the repository's
   `README.md` or `Makefile` for the exact commands.

6. **Open a pull request** against `main`. In the description:
   - Explain what changed and why.
   - Link the related issue.
   - Describe how the change was tested.
   - Flag anything security-sensitive (secret handling, auth flows, HTTP
     client changes) so maintainers know to apply extra scrutiny.

## What we look for in a pull request

- **Tests that fail without the fix.** Demonstrable coverage is required for
  bug fixes; it's expected for new features.
- **No unrelated changes.** Don't bundle typo fixes with features; don't
  reformat files you didn't touch.
- **Updated documentation.** New resources, commands, attributes, or
  behavior changes should land with updated `README.md`, examples, and
  generated docs (if applicable).
- **A `CHANGELOG.md` entry** (under `## [Unreleased]`) for any user-visible
  change.

## Coding conventions

These apply across all repositories unless a project-level `CONTRIBUTING.md`
overrides them:

- **Comments explain WHY, not WHAT.** Well-named identifiers cover the WHAT.
  Reserve comments for invariants, edge cases, and non-obvious decisions.
- **Errors carry context.** Wrap errors with enough information to locate the
  failure without a debugger.
- **No silent failures.** Every error path either surfaces the error to the
  caller or produces a user-visible diagnostic. Do not swallow errors.
- **Secrets must never reach logs.** If you add a field that carries a
  credential, ensure it is excluded from any logging or error-message path.

## Questions

Open a discussion or issue in the relevant repository. We aim to respond
within a few business days.
