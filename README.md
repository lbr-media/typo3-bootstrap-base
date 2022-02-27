# typo3-bootstrap-base

Only a composer.json file to run a complete website.

This is mainly for testing.

This package installs Typo3 v11 and after that two further extensions:

1. https://github.com/lbr-media/typo3-extension-bootstrap as `bootstrap` which is a template-extension providing all to run a Bootstrap 5 website.
1. https://github.com/lbr-media/typo3-extension-bootstrap-example as `bootstrap_example` which is a distribution-extension. Here all data and files are included.

## Installation

### 1. Get started

Download all basic typo3 packages.

``` Bash
composer install
```

### 2. Install Typo3 in the ususal way:

1. Create file `public/FIRST_INSTALL`.
2. Call the website: https://your-domain/
3. Do the installation steps.

Stop when you are able to run the Typo3 backend. Do not make records like pages or templates b/c the distribution extension will not import its records.

### 4. Load the template- and distribution-extensions

``` Bash
composer require lbr-media/typo3-extension-bootstrap
composer require lbr-media/typo3-extension-bootstrap-example
```

### 5. Get the extensions running

``` Bash
# Copy some assets to fileadmin.  
php vendor/bin/typo3 bootstrap:updatefileadmin

# Activate the extensions which also imports the data from the distribution-extension:  
php vendor/bin/typo3 extension:setup
```

After that clear the cache (p.e. `php vendor/bin/typo3 cache:flush`) and check if the website is running.

### Adjust settings

The `baseURL` is set to `/`. If you run the website in a subfolder, adjust it in the template of the root page in field `Setup`:

``` TypoScript
config.baseURL = /your-subfolder/
```

Or:

``` TypoScript
config.baseURL = https://your-domain/your-subfolder/
```

### Adjust constants

Because the UIDs of the records may change while importing them you have to set some PIDs.

Go to the backend and open the template on root page. Set this in the `Constants` field and adjust the PIDs:

``` TypoScript
plugin.tx_bootstrapexample {
    pid {
        menu {
            legal = 2
            projects = 10
            portfolio = 7
            brand = 13
            contact = 5
        }
    }
}
```
