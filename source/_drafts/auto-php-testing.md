---
title: auto-php-testing
tags:
---
TDD pre env setting

This artile share how to listen to the files change and auto ecute phpunit

https://www.sitepoint.com/write-javascript-style-test-watchers-php/

And I also found spatie require this lib to complete the application.

https://github.com/spatie/phpunit-watcher

```
{
    "scripts": {
        "test:watch": [
            "Composer\\Config::disableProcessTimeout",
            "phpunit-watcher watch < /dev/tty"
        ]
    }
}
```

```
$ composer run test:watch
> Composer\Config::disableProcessTimeout
> ./vendor/bin/phpunit-watcher watch < /dev/tty


PHPUnit Watcher
===============

 PHPUnit Watcher 1.12.1 by Spatie and contributors.

 Using options from configfile at `/var/www/html/phpunit-watcher.yml`

 Tests will be rerun when *.php files are modified in
 * /var/www/html/app
 * /var/www/html/tests


PHPUnit 8.5.8 by Sebastian Bergmann and contributors.

................................................................. 65 / 77 ( 84%)
............                                                      77 / 77 (100%)

Time: 1.39 minutes, Memory: 56.50 MB

OK (77 tests, 121 assertions)
Starting PHPUnit with arguments: `--stop-on-failure`


Press a to run all tests.
Press t to filter by test name.
Press p to filter by file name.
Press g to filter by group name.
Press s to filter by test suite name.
Press r to run tests with a random seed.
Press q to quit the watcher.
```

It's easy to choose test all or choose for single test
