# CiSkeleton Installer

The official command-line installer for creating new [CiSkeleton](https://github.com/ciskeleton) projects.

CiSkeleton Installer creates a new project, retrieves the required CiSkeleton packages, and assembles them into the standard CiSkeleton project structure.

## Requirements

* PHP 8.0 or newer
* Git
* Composer

## Installation

Install the installer globally with Composer:

```bash
composer global require ciskeleton/installer
```

Make sure your Composer global `bin` directory is available in your system `PATH`.

You can find the directory with:

```bash
composer global config bin-dir --absolute
```

Verify the installation:

```bash
csk --help
```

## Usage

Create a new project:

```bash
csk new my-project
```

Or provide an absolute path:

```bash
csk new /path/to/my-project
```

After creating the project:

```bash
cd my-project
php -S localhost:8000 index.php
```

The PHP development server is intended for local development and testing. For production deployments, use a suitable web server and PHP configuration.

## What it installs

A new project is assembled from the required CiSkeleton repositories.

| Package          | Repository                | Destination                |
| ---------------- | ------------------------- | -------------------------- |
| Core             | `ciskeleton/core`         | `system/`                  |
| Application      | `ciskeleton/app-default`  | `application/`             |
| English language | `ciskeleton/lang-english` | `system/language/english/` |
| Common           | `ciskeleton/common`       | `content/common/`          |

The installer also publishes the contents of `application/public/` into the project root.

This provides the standard public entry point and web-accessible files, such as:

```text
index.php
.htaccess
content/
```

## Generated project structure

A newly created project will look roughly like this:

```text
my-project/
├── application/
├── system/
│   └── language/
│       └── english/
├── content/
│   └── common/
├── index.php
└── .htaccess
```

The exact structure may evolve as the CiSkeleton project develops.

## Project creation

The installer performs the work required to assemble a functional CiSkeleton project, including:

1. Creating the destination directory.
2. Retrieving the required CiSkeleton repositories.
3. Installing each package into its designated directory.
4. Publishing the application's public files to the project root.
5. Validating the resulting project structure.

The installer does not modify your existing projects.

## Local development

Clone this repository:

```bash
git clone https://github.com/ciskeleton/installer.git
cd installer
```

Run the installer directly:

```bash
php bin/csk new ../demo-project
```

On Unix-like systems, you can also make the script executable:

```bash
chmod +x bin/csk
./bin/csk new ../demo-project
```

## Testing locally with Composer

To test a local checkout as a global Composer package, register it as a path repository:

```bash
composer global config repositories.installer '{"type":"path","url":"/absolute/path/to/installer","options":{"symlink":true}}'
composer global require ciskeleton/installer:@dev
```

Then:

```bash
csk new demo-project
```

When finished, remove the local installation and repository configuration:

```bash
composer global remove ciskeleton/installer
composer global config --unset repositories.installer
```

## Development checks

Validate the Composer package metadata:

```bash
composer validate --strict
```

Check PHP syntax:

```bash
composer lint
```

Before submitting changes, create a test project and verify that the generated project can be started successfully.

## Contributing

Contributions are welcome.

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for development requirements and contribution guidelines.

## Security

If you discover a security vulnerability, please report it privately rather than opening a public issue.

See [`SECURITY.md`](SECURITY.md) for reporting instructions.

## License

CiSkeleton Installer is licensed under the MIT License.

See [`LICENSE.md`](LICENSE.md) for the complete license text.
