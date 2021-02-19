---
title: Custom filter
date: 2019-08-02 21:00:54
date: 2021-02-19 14:24:21
tags:
 - crm
 - suitecrm
---

以在 invoice 底下新增 過濾 擁有該產品的 訂單為例

為 custom filter 命名
custom/Extension/modules/AOS_Invoices/Ext/Language/en_us.php

$mod_strings['LBL_AOS_PRODUCTS_QUOTES'] = "Invoice Part Number";


拷貝 modules 底下的資料放在 custom 底下
custom/modules/AOS_Invoices/metadata/SearchFields.php
在底部增加
    'aos_products_quotes' =>
    array(
        'query_type' => 'format',
        'operator' => 'subquery',
        'checked_only' => true,
        'subquery' => 'SELECT
                           aos_products_quotes.parent_id
                       FROM
                           aos_products_quotes
                           JOIN aos_products ON aos_products_quotes.product_id = aos_products.id
                       WHERE
                           aos_products_quotes.deleted = 0
                           AND aos_products_quotes.parent_type = \'AOS_Invoices\'
                           AND aos_products.part_number = \'{0}\'',
        'db_field' =>
        array(
            0 => 'id',
        ),
    ),



拷貝 modules 底下的資料放在 custom 底下
custom/modules/AOS_Invoices/metadata/searchdefs.php
增加  在 basic_search 底下
        'basic_search' =>
        array(
	...
            'aos_products_quotes' => array(
                'name' => 'aos_products_quotes',
                'label' => 'LBL_AOS_PRODUCTS_QUOTES',
                'width' => '10%'
            ),
