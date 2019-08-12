---
title: git-hook-unit-test
date: 2019-08-02 22:21:11
tags:
---

Set up Vim for PHP development
For text editing, Vim is more productive than the premier PHP IDE, PHPStorm, but by default it lacks PHP-specific intelligence. We can remediate that by using the right plugins and configuration.

Syntax checking, completion and go-to-definition with ALE
Install the Asynchronous Lint Engine.

In your .vimrc, you can select specific linters:

let g:ale_linters = {'php': ['php', 'langserver', 'phan']}
php gives us basic syntax checking. langserver provides completion and go-to-definition functionality. phan checks types and warns for undefined symbols.

ALE will prefer to use project-specific executables for the language server and Phan, if they are available in your project's vendor directory.

Configure PHP language server
We need to install the PHP language server in order to get completion and go-to-definition functionality.

This can be done globally (that is, for your user account):

composer global require felixfbecker/language-server jetbrains/phpstorm-stubs:@dev
composer global run-script --working-dir ~/.config/composer/vendor/felixfbecker/language-server parse-stubs
Then tell ALE to use this language server:

let g:ale_php_langserver_executable = expand('~/.config/composer/vendor/bin/php-language-server.php')
Configure Phan
If you wish to use Phan, install it as follows:

composer global require phan/phan
And configure ALE to use it:

let g:ale_php_phan_executable = expand('~/bin/phan_client_auto')
let g:ale_php_phan_use_client = 1
phan_client_auto is a script that starts the Phan deamon in the background. At the moment, this requires that you create a .phan/config.php file in each of the projects you want to check using Phan.

The most basic Phan configuration that gets useful results would be:

<?php
return [
    'directory_list' => ['.'],
];
Should it not work, you can test phan_client_auto as follows:

phan_client_auto -l ./path/to/php_file.php
Return to albert.cx
Address comments to hi at albert dot cx


(https://albert.cx/20190104-vim-for-php-development)[https://albert.cx/20190104-vim-for-php-development]
