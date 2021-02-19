---
title: Custom list view
date: 2021-02-19 14:24:21
tags:
 - crm
 - suitecrm
---

基本清單修改：
建立 Hooks 名稱

# shell
$ mkdir Extension/modules/Accounts/Ext/LogicHooks
$ touch Extenstion/modules/Accounts/Ext/LogicHooks/ListViewHightlight.php


<?php
# Extenstion/modules/Accounts/Ext/LogicHooks/ListViewHightlight.php
$hook_array['process_record'][] = Array(
    1,
    'Highlight account industry',
    'custom/modules/Accounts/HighlightIndustryLogicHook.php',
    'HighlightIndustryLogicHook',
    'highlightIndustry'
);

建立 hooks 修改內容

$ touch custom/modules/Accounts/HighlightIndustryLogicHook.php


<?php
#custom/modules/Accounts/HighlightIndustryLogicHook.php
class HighlightIndustryLogicHook{

    public function highlightIndustry(SugarBean $bean, $event, $arguments){
        $colour = substr(md5($bean->name),0,6);
        $bean->name = "<div style='border: solid 5px #$colour;'>".$bean->name."</div>";
    }

}







Reference:

https://support.sugarcrm.com/Documentation/Sugar_Developer/Sugar_Developer_Guide_10.2/Architecture/Logic_Hooks/

http://www.jsmackin.co.uk/suitecrm/suitecrm-list-view-conditional-formatting/
