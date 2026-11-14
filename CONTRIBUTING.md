# Contributing to blueprint-extension

blueprint-extension contains prompt and configuration workflows for engineering and investigation tasks. Read the [README](README.md) and [AGENTS.md](AGENTS.md) for the existing workflow structure, naming conventions, and safety boundaries.

## Before you start

Search existing issues and pull requests before starting, and discuss substantial changes or new dependencies in an issue. Use an issue template when one is offered. For a bug, include the affected commit or version, environment, a minimal reproduction, and expected versus observed behavior; remove sensitive information from logs and screenshots.

## Development and validation

The project is prompt/configuration driven. Follow the manual smoke-test guidance in `AGENTS.md` using a scratch workspace and the workflow names present in the current checkout. Verify expected state files and transitions, including the existing confirmation points. Keep legacy Gemini extension checks separate from the Antigravity workflow.

The [CI workflow](.github/workflows/ci.yml) checks essential structure; it is not an end-to-end test of agent behavior. For a changed prompt, provide representative synthetic input, expected behavior, observed output, and edge cases. Preserve workflow filenames and state-file names as interfaces, and respect the existing rule-file size limit.

Keep investigation workflows read-only by default and preserve confirmation for destructive operations. Update user-facing command documentation when behavior changes, and distinguish simulated reviews from independent human review or executed test evidence.

## Pull requests

Work on a focused branch from the current default branch. Open a pull request explaining the problem, the resulting behavior, and any compatibility or data-format changes. Link the relevant issue and complete any existing PR template.

Add focused regression coverage for changed behavior and update affected examples or documentation. Describe the checks actually run, their results, and any checks you could not run. For documentation-only changes, verify links, examples, and rendered formatting. Use the repository's existing checks and review/merge process; preserve required checks and resolve actionable feedback without weakening the checks.

## Security and sensitive information

Follow the [account security policy](https://github.com/edithatogo/.github/blob/main/SECURITY.md). Report vulnerabilities privately through the repository's **Report a vulnerability** option if available; otherwise request a private reporting contact without posting exploit details. Never include credentials, personal information, restricted datasets, or confidential records in issues, commits, fixtures, or diagnostic output.

## Licensing and conduct

The repository's [license](LICENSE) continues to apply. Be respectful and constructive, and follow the [account code of conduct](https://github.com/edithatogo/.github/blob/main/CODE_OF_CONDUCT.md). Preserve attribution and third-party notices. Contribute only material you are entitled to share; resolve unclear permissions before adding third-party content. This guide does not change licensing terms or introduce a CLA or DCO requirement.

## References

- [GitHub contribution guideline conventions](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/setting-guidelines-for-repository-contributors)
- [OpenSSF contribution and quality criteria](https://www.bestpractices.dev/en/criteria)
