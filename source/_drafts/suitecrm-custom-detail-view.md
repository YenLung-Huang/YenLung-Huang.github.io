---
title: Custom detail view
date: 2021-02-19 14:24:21
tags:
 - crm
 - suitecrm
---

# 基本 detail view 欄位修改

以客戶 Accounts detail view 為例

先部署欄位

Admin -> studio -> Accounts - > Layouts -> Detail View -> Save & Deploy

Deploy 之後會產生檔案 custom/modules/Accounts/metadata/detailviewdefs.php

修改檔案

以隱藏客戶名字為例

在以下陣列為 "name" 的地方新增 參數 'customCode' => '<span class="sugar_field" id="name">{$ssnView}</span>',

解釋：

customCode 會被 sugar engine 替換成 <span class=”sugar_field” id=”name”>{$ssnView}</span> 的 html 格式，其中 $ssnView 為模板參數，模板參數通常就是變數，從別的檔案傳送進來的值

```php
...
          0 =>
          array (
            'name' => 'name',
            'comment' => 'Name of the Company',
            'label' => 'LBL_NAME',
          ),
...
```

至

```php
...
          0 =>
          array (
            'name' => 'name',
            'comment' => 'Name of the Company',
            'label' => 'LBL_NAME',
            'customCode' => '<span class="sugar_field" id="name">{$ssnView}</span>',
          ),
...
```

修改完參數之後，開始繼承原本的 view.detail.php 去改寫其中的功能

這邊先複製把 modules/Accounts/views/view.detail.php 從原本的模組，複製到 custom/modules/Accounts/views/view.detail.php

```shell
$ cp modules/Accounts/views/view.detail.php custom/modules/Accounts/views/view.detail.php
```

修改檔案

```php
<?php
if (!defined('sugarEntry') || !sugarEntry) {
    die('Not A Valid Entry Point');
}

/**
 * SugarCRM is a customer relationship management program developed by
 * SugarCRM, Inc. Copyright (C) 2004-2010 SugarCRM Inc.
 *
 * This program is free software; you can redistribute it and/or modify it under
 * the terms of the GNU General Public License version 3 as published by the
 * Free Software Foundation with the addition of the following permission added
 * to Section 15 as permitted in Section 7(a): FOR ANY PART OF THE COVERED WORK
 * IN WHICH THE COPYRIGHT IS OWNED BY SUGARCRM, SUGARCRM DISCLAIMS THE WARRANTY
 * OF NON INFRINGEMENT OF THIRD PARTY RIGHTS.
 *
 * This program is distributed in the hope that it will be useful, but WITHOUT
 * ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
 * FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more
 * details.
 *
 * You should have received a copy of the GNU General Public License along with
 * this program; if not, see http://www.gnu.org/licenses or write to the Free
 * Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA
 * 02110-1301 USA.
 *
 * You can contact SugarCRM, Inc. headquarters at 10050 North Wolfe Road,
 * SW2-130, Cupertino, CA 95014, USA. or at email address contact@sugarcrm.com.
 *
 * The interactive user interfaces in modified source and object code versions
 * of this program must display Appropriate Legal Notices, as required under
 * Section 5 of the GNU General Public License version 3.
 *
 * In accordance with Section 7(b) of the GNU General Public License version 3,
 * these Appropriate Legal Notices must retain the display of the "Powered by
 * SugarCRM" logo. If the display of the logo is not reasonably feasible for
 * technical reasons, the Appropriate Legal Notices must display the words
 * "Powered by SugarCRM".
 */


class AccountsViewDetail extends ViewDetail
{
    public function __construct()
    {
        parent::__construct();
    }

    /**
     * @deprecated deprecated since version 7.6, PHP4 Style Constructors are deprecated and will be remove in 7.8, please update your code, use __construct instead
     */
    public function AccountsViewDetail()
    {
        $deprecatedMessage = 'PHP4 Style Constructors are deprecated and will be remove in 7.8, please update your code';
        if (isset($GLOBALS['log'])) {
            $GLOBALS['log']->deprecated($deprecatedMessage);
        } else {
            trigger_error($deprecatedMessage, E_USER_DEPRECATED);
        }
        self::__construct();
    }


    /**
     * display
     * Override the display method to support customization for the buttons that display
     * a popup and allow you to copy the account's address into the selected contacts.
     * The custom_code_billing and custom_code_shipping Smarty variables are found in
     * include/SugarFields/Fields/Address/DetailView.tpl (default).  If it's a English U.S.
     * locale then it'll use file include/SugarFields/Fields/Address/en_us.DetailView.tpl.
     */
    public function display()
    {
        if (empty($this->bean->id)) {
            global $app_strings;
            sugar_die($app_strings['ERROR_NO_RECORD']);
        }

        require_once('modules/AOS_PDF_Templates/formLetter.php');
        formLetter::DVPopupHtml('Accounts');

        $this->dv->process();

        if (ACLController::checkAccess('Contacts', 'edit', true)) {
            $push_billing = $this->generatePushCode('billing');
            $push_shipping = $this->generatePushCode('shipping');
        } else {
            $push_billing = '';
            $push_shipping = '';
        }

        $this->ss->assign("custom_code_billing", $push_billing);
        $this->ss->assign("custom_code_shipping", $push_shipping);

        if (empty($this->bean->id)) {
            global $app_strings;
            sugar_die($app_strings['ERROR_NO_RECORD']);
        }
        echo $this->dv->display();
    }

    public function generatePushCode($param)
    {
        global $mod_strings;
        $address_fields = array('street', 'city', 'state', 'postalcode','country');

        $html = '<input class="button" title="' . $mod_strings['LBL_PUSH_CONTACTS_BUTTON_LABEL'] .
             '" type="button" onclick=\'open_contact_popup("Contacts", 600, 600, "&account_name=' .
             $this->bean->name . '&html=change_address';

        foreach ($address_fields as $value) {
            $field_name = $param.'_address_'.$value;
            $html .= '&primary_address_'.$value.'='.str_replace(array("\rn", "\r", "\n"), array('','','<br>'), urlencode($this->bean->$field_name)) ;
        }

        $html .= '", true, false);\' value="' . $mod_strings['LBL_PUSH_CONTACTS_BUTTON_TITLE']. '">';
        return $html;
    }
}
```

To


```php
require_once 'modules/Accounts/views/view.detail.php';

class CustomAccountsViewDetail extends AccountsViewDetail
{
    /**
     * display
     * Override the display method to support customization for the buttons that display
     * a popup and allow you to copy the account's address into the selected contacts.
     * The custom_code_billing and custom_code_shipping Smarty variables are found in
     * include/SugarFields/Fields/Address/DetailView.tpl (default).  If it's a English U.S.
     * locale then it'll use file include/SugarFields/Fields/Address/en_us.DetailView.tpl.
     */
    public function display()
    {
        global $sugar_config;
        global $current_user; //First we need to add global user variable
        $aop_portal_enabled = !empty($sugar_config['aop']['enable_portal']);

        $this->ss->assign("AOP_PORTAL_ENABLED", $aop_portal_enabled);

        require_once('modules/AOS_PDF_Templates/formLetter.php');
        formLetter::DVPopupHtml('Contacts');

        $isEnabledRole = in_array("Privileged", ACLRole::getUserRoleNames($current_user->id)); //Load Role to True or False
        //If user is part of Role Privileged then they may see the full SSN
        if($isEnabledRole){
            //take the curent bean field needed to manipulate
            $numbers_only = preg_replace("/[^\d]/", "", $this->bean->name);
            $ssnformat = preg_replace("/^(\d{3})(\d{2})(\d{4})$/", "$1-$2-$3", $numbers_only);
            //now this part i needed some brain food but basically we are taking a variable (ssnView) defined
            //in the detailviewdefs.php which is the file that defines what is displayed per field and location
            $this->dv->ss->assign('ssnView', $ssnformat);
        } else {

            $numbers_only = preg_replace("/[^\d]/", "", $this->bean->name);
            $ssnlastfour = substr($numbers_only, -4);
            $ssnformat = '***-**-' . $ssnlastfour;
            //alternate view for the remainding roles for the SSN, here we are also updating a variable in detailviewdefs.php
            $this->dv->ss->assign('ssnView', $ssnformat);

        }
        parent::display();
    }

}
```
