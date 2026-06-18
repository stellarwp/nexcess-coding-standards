# Nexcess Coding Standards

The Nexcess Coding Standard is a set of [PHP_CodeSniffer](https://github.com/PHPCSStandards/PHP_CodeSniffer)
rules for Nexcess PHP and WordPress projects.

## Requirements

- PHP 7.4+

## Installation

This package should be installed as a development dependency for your project:

```sh
$ composer require --dev stellarwp/nexcess-coding-standards
```

After installation, the standard is available to PHPCS as `Nexcess`.

## Project Ruleset

To use this ruleset, create a `phpcs.xml.dist` in the root of the project and add the following content:

```xml
<?xml version="1.0"?>
<ruleset>
	<arg name="basepath" value="." />
	<arg name="extensions" value="php" />
	<arg name="severity" value="4" />
	<arg name="tab-width" value="4" />
	<arg name="parallel" value="80" />
	<arg name="colors" />

	<!-- Update to the PHP version your production/local docker container runs on. -->
    <config name="testVersion" value="8.0" />
	<!-- php -r 'echo PHP_VERSION_ID;' -->
    <config name="php_version" value="80022" />

	<!-- Fix WordPress typing breaking PHPCS. -->
	<config name="minimum_supported_wp_version" value="7.0" />

	<!-- Ignore warnings, show progress of the run and show sniff names. -->
	<arg value="nps" />

	<!-- Directories to be checked. -->
	<file>./wp-content/plugins/core</file>
	<file>./wp-content/themes/core</file>
	<file>./wp-content/mu-plugins</file>

	<!-- Exclude files. -->
	<exclude-pattern>*-config.php</exclude-pattern>
	<exclude-pattern>*vendor/</exclude-pattern>
	<exclude-pattern>*tests/*</exclude-pattern>
	<exclude-pattern>*.twig</exclude-pattern>
	<exclude-pattern>*webpack/</exclude-pattern>

	<!-- Include the Nexcess coding standard. -->
	<rule ref="Nexcess" />
</ruleset>
```

Add `phpcs.xml` to your `.gitignore`.

## Manual Usage

**PHPCS**

```sh
$ ./vendor/bin/phpcs --standard=Nexcess /path/to/files/**.php
```

**PHPCBF**

```sh
$ ./vendor/bin/phpcbf --standard=Nexcess /path/to/files/**.php
```

## License

This library is licensed under the terms of [the MIT license](LICENSE).
