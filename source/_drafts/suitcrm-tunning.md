---
title: suitcrm-tunning
tags:
---

# Performance Tweaks
In most cases the performance of SuiteCRM should not be an issue. However in the case of large datasets or systems with many users you may notice some performance degradation. These changes can help improve performance.

## Server
The server that SuiteCRM runs on is, of course, very important when it comes to the kind of performance you can expect. A full guide on server setup is outside the scope of this book. However there are some things you can do to ensure that you get the best performance out of SuiteCRM.

### PHP
Installing a PHP opcode cache will increase the performance of all PHP files. These work by caching the compilation of PHP files resulting in less work on each request. Furthermore SuiteCRM will use the caching API of some PHP accelerators which will further increase performance. If you are using Linux then APC is the usual choice. Windows users should check out WinCache.

### MySQL
MySQL is notorious for having small default settings. Fully optimising MySQL is outside the scope of this book (however checkout mysqltuner.pl for a helpful Perl script which will provide setting recommendations - note that you should be careful when running files from an unknown source). One small change that can make a big difference is increasing the innodb_buffer_pool_size.

If you have migrated or imported a significant amount of data it is possible that some tables will be fragmented. Running OPTIMIZE TABLE tablename can increase performance.

## Indexes
Adding indexes on the fields of modules can improve database performance. The core modules usually have important fields indexed. However if you have created a new module or added new, often searched fields to a module then these fields may benefit from being indexed. See the Vardef chapter for adding indexes.

Config Changes
The following are some config settings that can be used to improve performance. Please note that in most cases you will have better performance gains by first following the steps in previous sections. These settings should be set in the config_override.php file. See the chapter on the Config files for more information.

```php
$sugar_config['developerMode'] = false;
```
Unless you are actively developing on an instance developerMode should be off. Otherwise each page request will cause cached files to be reloaded.

```php
$sugar_config['disable_count_query'] = true;
`````
For systems with large amounts of data the count queries on subpanels used for the pagination controls can become slow thereby causing the page to be sluggish or outright slow to load. Disabling these queries can improve performance dramatically on some pages.

```php
$sugar_config['disable_vcr'] = true;
```
By default opening the detail view of a record from the list view will also load the other records in the list to allow for easy moving through records. If you do not use this feature, or, if loading the detail view for some records has become slow, you can disable this feature.

```php
$sugar_config['list_max_entries_per_page'] = '10';
````
The number of records shown in each page of the list view can be decreased. This will result in a slight increase in performance on list view pages.

```php
$sugar_config['logger']['level'] = 'fatal';
```
Lowering the log level means that there will be less log messages to write to disk on each request. This will slightly (very slightly) increase performance

## Test
```php``
$sugar_config['admin_export_only'] = true;
```
https://docs.suitecrm.com/developer/performance-tweaks/
