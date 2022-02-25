# typo3-bootstrap-base

Only a composer.json file to run a complete website.

This is mainly for testing.

This package installs Typo3 v11 and two further extensions:

1. https://github.com/lbr-media/typo3-extension-bootstrap as `bootstrap` which is a template-extension providing all to run a Bootstrap 5 website.
1. https://github.com/lbr-media/typo3-extension-bootstrap-example as `bootstrap_example` which is a distribution-extension. Here all data and files are included.

## Installation

### 1. Rrun `composer install`

All used packages are downloaded and installed.

### 2. Install Typo3 in the ususal way:

1. Create file `public/FIRST_INSTALL`.
2. Call the website: https://your-domain/
3. Do the installation steps.

### 3. Setup all extensions

`php vendor/bin/typo3 extension:setup`

This command will also activate the two extensions. The files and data will be imported.

After that clear the cache (p.e. `php vendor/bin/typo3 cache:flush`) and check if the website is running.