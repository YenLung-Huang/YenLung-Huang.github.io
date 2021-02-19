---
title: Custom subpanel
date: 2021-02-19 14:24:21
tags:
 - crm
 - suitecrm
---

客製化 Subpanel

以 客戶 Account 與 Product 為例 需修改以下幾個地方

custom/Extension/modules/Accounts/Ext/Language/en_us.php

<?php
$mod_strings['LBL_OPPORTUNITIES_WITH_CLOSED_LOST'] = "Opportunities With Closed Lost";
$mod_strings['LBL_OPPORTUNITIES_WITH_CLOSED_WON'] = "Opportunities With Closed Won";
$mod_strings['LBL_ACCOUNT_PRODUCTS'] = "Account Products";



custom/Extension/modules/Accounts/Ext/Layoutdefs/cusotmSubpanel.php

<?php

$layout_defs['AOS_Invoices']['subpanel_setup']['invoice_return'] =
    array(
        'order' => 50,
        'module' => 'AOS_Products',
        'subpanel_name' => 'default',
        'get_subpanel_data' => 'function:get_account_products',
        'generate_select' => true,
        'title_key' => 'LBL_ACCOUNT_PRODUCTS',
        'top_buttons' => array(),
        'function_parameters' => array(
            'import_function_file' => 'custom/modules/AOS_Invoices/customProductsSubpanel.php',
            'status' => 'Return',
            'invoice_id' => $this->_focus->id,
            'return_as_array' => 'true'
        ),
    );


custom/modules/Accounts/customOpportunitiesSubpanel.php

<?php

function get_closed_lost_closed_won_opportunities($params) {
    $args = func_get_args();
    $opportunitiesSalesStage = $args[0]['sales_stage'];
    $accountId = $args[0]['account_id'];
    $return_array['select'] = " SELECT opportunities.*";
    $return_array['from'] = " FROM opportunities ";
    $return_array['where'] = " WHERE opportunities.deleted = '0' AND opportunities.sales_stage = '" . $opportunitiesSalesStage . "'";
    $return_array['join'] = " INNER JOIN accounts_opportunities ON accounts_opportunities.opportunity_id = opportunities.id AND accounts_opportunities.deleted = '0' INNER JOIN accounts ON accounts.id = accounts_opportunities.account_id AND accounts.deleted = '0' AND accounts.id = '" . $accountId . "'";
    $return_array['join_tables'] = '';
    return $return_array;
}



custom/modules/Accounts/customProductsSubpanel.php

<?php

function get_account_products($params) {
    $args = func_get_args();
    $accountId = $args[0]['account_id'];
    $return_array['select'] = " SELECT aos_products.*";
    $return_array['from'] = " FROM aos_products ";
    $return_array['where'] = " WHERE aos_products_cstm.account_id_c = '" . $accountId . "'";
    $return_array['join'] = "";
    $return_array['join_tables'] = '';
    return $return_array;
}


custom/modules/Accounts/language/en_us.lang.php

<?php
// created: 2020-12-14 07:38:37
$mod_strings = array (
  …

  'LBL_ACCOUNT_SELL_PRODUCTS_TITLE' => 'Products' // ← 增加這行
);

