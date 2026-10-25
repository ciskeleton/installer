# Contributing

Thanks for your interest in contributing to CiSkeleton Installer.

## Requirements

- PHP 8.0 or newer
- Git
- Composer

## Local setup

Clone the repository:

```bash
git clone https://github.com/ciskeleton/installer.git
cd installer
```

Run the installer directly:

```bash
php bin/csk new ../demo-project
```

## Code style

Keep the installer simple:

- no runtime dependencies unless absolutely necessary
- readable PHP over clever abstractions
- clear error messages
- safe filesystem operations
- no hardcoded secrets or access tokens

## Checks

Validate Composer metadata:

```bash
composer validate --strict
```

Check PHP syntax:

```bash
composer lint
```

## Pull requests

Before opening a pull request:

1. Run `composer validate --strict`.
2. Run `composer lint`.
3. Test creating a new project locally.
4. Make sure no credentials, tokens, or private paths are committed.
