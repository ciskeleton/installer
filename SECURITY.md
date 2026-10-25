# Security Policy

## Supported versions

Only the latest released version of CiSkeleton Installer is supported.

## Reporting a vulnerability

Please report security issues privately.

Do not open a public GitHub issue for security vulnerabilities.

Send details to:

```text
security@ianhub.net
```

Include:

* affected version or commit
* operating system
* PHP version
* reproduction steps
* expected behavior
* actual behavior
* any relevant logs

## Credential handling

The installer must never contain hardcoded GitHub tokens, personal access tokens, deploy keys, passwords, or other private credentials.

Repository access is handled by the user's local Git authentication and environment.

Depending on the environment, authentication may be provided through:

* Git credential helpers
* SSH keys
* GitHub CLI authentication
* CI/CD secrets
* deploy keys
* other Git-supported authentication mechanisms

Credentials should never be committed to the project repository, embedded in installer code, or written to generated projects.
