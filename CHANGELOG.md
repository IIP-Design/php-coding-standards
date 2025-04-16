# Change Log

**All notable changes to this project will be documented in this file.**

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased](https://github.com/IIP-Design/php-coding-standards/compare/v1.1.0...HEAD)

## [v1.1.0](https://github.com/IIP-Design/php-coding-standards/compare/v1.0.1...v1.1.0) (2025-04-16)

**Changed:**

- Override the core WordPress config which prevent use of our preferred indentation (ie. two spaces) This includes the replacement of the "WordPress.WhiteSpace.PrecisionAlignment" rule exclusion with one for "Universal.WhiteSpace.PrecisionAlignment", as the former has been removed from the core WordPress config.
- Update dependency versions of `php_codesniffer` and `phpcsextra` to the latest versions (3.12.2 and 1.2.1 respectively).

## [v1.0.1](https://github.com/IIP-Design/php-coding-standards/compare/v1.0.0...v1.0.1) (2022-07-05)

**Added:**

- Homepage and support links to the Composer file

**Changed:**

- Correct the contact email in the Composer file
- Bump the version of `php_codesniffer` to `3.7.x` to support PHP 8.1 language features

## [v1.0.0](https://github.com/IIP-Design/php-coding-standards/releases/tag/v1.0.0) (2022-03-31 - Initial Release)

**Added:**

- Base ruleset modelled on the WordPress coding standards but excluding WordPress specific rules
- WordPress ruleset that extends and modifies the default WordPress coding standards
- Documentation on installation and basic usage
