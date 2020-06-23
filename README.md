# PHP style rules for PHP-CS-Fixer

These are the rules applied across all my projects.

## Installation

You can install using [composer](https://getcomposer.org/) from [Packagist](https://packagist.org/packages/ivang11/php-style).

```
composer require ivang11/php-style --dev
```

## Usage

In your `.php_cs.dist` config file

```php
<?php

// specify the paths to fix

$finder = PhpCsFixer\Finder::create()
    ->notPath('bootstrap/*')
    ->notPath('storage/*')
    ->notPath('vendor')
    ->in([
        __DIR__ . '/app',
        __DIR__ . '/tests',
        __DIR__ . '/database',
    ])
    ->name('*.php')
    ->notName('*.blade.php')
    ->ignoreDotFiles(true)
    ->ignoreVCS(true);


// then call and return the following style function

return Ivang11\styles($finder);
```

## Create alias for command

Set the command in composer.json

```json
"scripts": {
    "format": [
        "vendor/bin/php-cs-fixer fix"
    ],
}
```

Execute the command

```sh
composer format
```

Execute on CI

```sh
./vendor/bin/php-cs-fixer fix --dry-run
```

## Resources

- Sharing PHP-CS-Fixer rules across projects and teams. [Laravel News Article](https://laravel-news.com/sharing-php-cs-fixer-rules-across-projects-and-teams)
- Laravel Shift Recommended Coding Ruleset. [Gist](https://gist.github.com/laravel-shift/cab527923ed2a109dda047b97d53c200) - [Shift](https://laravelshift.com/)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
