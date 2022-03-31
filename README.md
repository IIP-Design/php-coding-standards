# GPA Lab PHP Code Standards

This collection of PHP CodeSniffer rules helps ensure consistency across PHP projects developed and managed by the GPA Lab. It helps to maintain a high level of code quality and standardizes the team's approach to PHP projects.

The repository contains two ruleset:

- [GPA Lab Standard](#general-projects) - Base rules applicable to any PHP project
- [GPA Lab WordPress](#wordpress-projects) - An extension of the WordPress Coding Standards ruleset for use when developing WordPress plugins/themes

## Rulesets

### General Projects

The GPA Lab Standard ruleset is a general set of rule applicable to any PHP project. In order to utilize these standards, you will need to install the following dependencies into your project:

- `gpalab/coding-standards` - The ruleset defined in this repository.
- `squizlabs/php_codesniffer` - A tool that conducts static code analysis in order to identify and fix problems.
- `dealerdirect/phpcodesniffer-composer-installer` - A Composer plugin that handles the registration of standards with PHP CodeSniffer.

The recommended way to install these dependencies is to add them to the development requirements listed in your project's `composer.json` file. The result will look something like this:

```json
{
  "name": "my-project",
  "require-dev": {
    "gpalab/coding-standards": "v1.0.0",
    "squizlabs/php_codesniffer": "^3.6.2",
    "dealerdirect/phpcodesniffer-composer-installer": "^v0.7.1"
  }
}
```

With this done, run `composer install` to install the dependencies to your project.

Once installed, you will need to identify which ruleset PHP Code Sniffer should utilize. The easiest way to do so is by adding a PHP Code Sniffer configuration file such as `.phpcs.xml` to the root of your project. In this file, use the `rule` tag to reference the GPA Lab standard ruleset using the key `GPA-Lab`. The result will look something like this:

```xml
<?xml version="1.0"?>
<ruleset name="My Project">

  <!-- List of files/directories to check. -->
  <file>*.php</file>

  <!-- Exclude vendor files from testing. -->
  <exclude-pattern>*/vendor</exclude-pattern>

  <!-- Load the Standard GPA Lab ruleset -->
  <rule ref="GPA-Lab" />

</ruleset>
```

### WordPress Projects

This repository also contains a ruleset for use with WordPress projects (such as plugins and themes). In addition to the PHP best practice and style rules in the standard ruleset, this ruleset includes Wordpress-specific rules and best practices.

The process for installing the WordPress ruleset is largely the same. However, since we are extending the WordPress ruleset, you will also need to install the following peer dependencies: `php-compatibility`, `phpcompatibility-wp`, and `wp-coding-standards/wpcs`. The resulting composer.json file will look like this:

```json
{
  "name": "my-wordpress-project",
  "require-dev": {
    "gpalab/coding-standards": "v1.0.0",
    "squizlabs/php_codesniffer": "^3.6.2",
    "dealerdirect/phpcodesniffer-composer-installer": "^v0.7.1",
    "phpcompatibility/php-compatibility": "*",
    "phpcompatibility/phpcompatibility-wp": "^2.1.3",
    "wp-coding-standards/wpcs": "^2.3.0"
  }
}
```

Your PHP Code Sniffer configuration file will look the same, except that you should use the `GPA-Lab-WordPress` reference key rather than the `GPA-Lab` key.

```xml
<?xml version="1.0"?>
<ruleset name="My WordPress Project">

  <!-- List of files/directories to check. -->
  <file>*.php</file>

  <!-- Exclude vendor files from testing. -->
  <exclude-pattern>*/vendor</exclude-pattern>

  <!-- Load the Standard GPA Lab ruleset -->
  <rule ref="GPA-Lab-WordPress" />

</ruleset>
```

## Usage

### CI

Often times, the easiest way to run PHP Code Sniffer in a continuous integration context is by adding an NPM script to execute the test. For example:

```json
"lint:PHP": "./vendor/bin/phpcs -n",
```

This script requires that PHP Code Sniffer is installed into the project's vendor directory, so make sure that you run `composer install` or `composer update` before executing this command.

_Note:_ The `-n` flag indicates that warnings should be omitted.

### VSCode

There are a number of ways to integrate PHP Code Sniffer into your local IDE. For VSCode, we have found that the combination of these two extensions works best:

- [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client)
- [PHP Sniffer & Beautifier](https://marketplace.visualstudio.com/items?itemName=ValeryanM.vscode-phpsab)

## Thanks

This project owes a huge debt to the [WordPress Coding Standards](https://github.com/WordPress/WordPress-Coding-Standards) project, which provided both inspiration and a sane set of defaults on which we were able to build.
