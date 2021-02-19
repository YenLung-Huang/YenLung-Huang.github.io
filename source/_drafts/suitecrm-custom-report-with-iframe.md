---
title: Custom report with iframe
date: 2021-02-19 14:24:21
tags:
 - crm
 - suitecrm
---

基本報表製圖
前置作業：

```shell
$ mkdir custom/Extension/application/Ext/EntryPointRegistry &
```

```shell
$ touch custom/Extension/application/Ext/EntryPointRegistry/entry_point_registry.ext.php
```

```php
<?php
# custom/Extension/application/Ext/EntryPointRegistry/entry_point_registry.ext.php

$entry_point_registry['customEntryPoint'] = array(
    'file' => 'path/to/customEntryPoint.php',
    'auth' => true
);
```

```shell
$ touch custom/customEntryPoint.php
```

Admin->Repair->Quick Repair and Rebuild

開始寫扣：

Basic

```php
<?php
#custom/customEntryPoint.php
if(!defined('sugarEntry') || !sugarEntry) die('Not A Valid Entry Point');

echo "Hello World!";
```

http:/127.0.0.1:5000/index.php?entryPoint=customEntryPoint



Advanced

```php
<?php
# custom/customEntryPoint.phpcustom/customEntryPoint.php
If (!defined('sugarEntry') || !sugarEntry) die('Not A Valid Entry Point');
?>

<html>
  <head>
    <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
    <script type="text/javascript">
      google.charts.load('current', {'packages':['corechart', 'bar']});
      google.charts.setOnLoadCallback(drawStuff);

      function drawStuff() {

        var button = document.getElementById('change-chart');
        var chartDiv = document.getElementById('chart_div');

        var data = google.visualization.arrayToDataTable([
          ['Galaxy', 'Distance', 'Brightness'],
          ['Canis Major Dwarf', 8000, 23.3],
          ['Sagittarius Dwarf', 24000, 4.5],
          ['Ursa Major II Dwarf', 30000, 14.3],
          ['Lg. Magellanic Cloud', 50000, 0.9],
          ['Bootes I', 60000, 13.1]
        ]);

        var materialOptions = {
          width: 900,
          chart: {
            title: 'Nearby galaxies',
            subtitle: 'distance on the left, brightness on the right'
          },
          series: {
            0: { axis: 'distance' }, // Bind series 0 to an axis named 'distance'.
            1: { axis: 'brightness' } // Bind series 1 to an axis named 'brightness'.
          },
          axes: {
            y: {
              distance: {label: 'parsecs'}, // Left y-axis.
              brightness: {side: 'right', label: 'apparent magnitude'} // Right y-axis.
            }
          }
        };

        var classicOptions = {
          width: 900,
          series: {
            0: {targetAxisIndex: 0},
            1: {targetAxisIndex: 1}
          },
          title: 'Nearby galaxies - distance on the left, brightness on the right',
          vAxes: {
            // Adds titles to each axis.
            0: {title: 'parsecs'},
            1: {title: 'apparent magnitude'}
          }
        };

        function drawMaterialChart() {
          var materialChart = new google.charts.Bar(chartDiv);
          materialChart.draw(data, google.charts.Bar.convertOptions(materialOptions));
          button.innerText = 'Change to Classic';
          button.onclick = drawClassicChart;
        }

        function drawClassicChart() {
          var classicChart = new google.visualization.ColumnChart(chartDiv);
          classicChart.draw(data, classicOptions);
          button.innerText = 'Change to Material';
          button.onclick = drawMaterialChart;
        }

        drawMaterialChart();
    };
    </script>
  </head>
  <body>
    <button id="change-chart">Change to Classic</button>
    <br><br>
    <div id="chart_div" style="width: 800px; height: 500px;"></div>
  </body>
</html>
```


http:/127.0.0.1:5000/index.php?entryPoint=customEntryPoint

Advanced with db


```php
<?php
#custom/customEntryPoint.phpcustom/customEntryPoint.php
if (!defined('sugarEntry') || !sugarEntry) die('Not A Valid Entry Point');

// comanys
$result = $db->query("select distinct user from report_day_by_day_invoice where user != '';");
$companies = [];
array_push($companies, "year");
while ($val = $db->fetchByAssoc($result, -1, false)) {
    array_push($companies, $val['user']);
}

// years
$result = $db->query("select distinct left(invoice_date, 4) as 'year' from report_day_by_day_invoice order by year asc");
$years = [];
while ($val = $db->fetchByAssoc($result, -1, false)) {
    if ($val['year'] != null)
        array_push($years, $val['year']);
}

// data
$result = $db->query(
    "select year,
    ((select sum(total_amt) from report_day_by_day_invoice where year = a.year and user = 'Owlting')) as `Owlting`,
    ((select sum(total_amt) from report_day_by_day_invoice where year = a.year and user = 'EC_MARKET')) as `EC_MARKET`,
    ((select sum(total_amt) from report_day_by_day_invoice where year = a.year and user = 'owljourney')) as `owljourney`
    from report_day_by_day_invoice as `a`
    where year is not null
    group by year");
$data = [];
while ($val = $db->fetchByAssoc($result, -1, false)) {
    array_push($data,
        $val['year'],
        (int)$val['Owlting'],
        (int)$val['EC_MARKET'],
        (int)$val['owljourney']
    );
}

$companies = json_encode($companies);
$years = json_encode($years);
$data = json_encode($data);

?>

<html>
  <head>
    <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
<script type="text/javascript">
google.charts.load('current', {'packages':['corechart', 'bar']});
google.charts.setOnLoadCallback(drawStuff);

function drawStuff() {
    const header = JSON.parse(<?=$companies?>);
    const years = JSON.parse(<?=$years?>);
    const source = JSON.parse(<?=$data?>);

    var data = new google.visualization.DataTable();

    data.addColumn('string', 'Categories');
    data.addColumn('number', 'Experience');
    data.addColumn('number', 'EC_MARKET');
    data.addColumn('number', 'Journey');

    data.addRows(source);

    let options = {
        chart: {
            title: 'Company Performance',
            subtitle: `Sales, Expenses, and Profit: ${years[0]} - ${years[years.length - 1]}`
        },
        colors: [
            '#ffadad', '#ffd6a5', '#83C5BE'
        ]
    };

    const chart = new google.charts.Bar(document.getElementById('char_div'));
    chart.draw(data, google.charts.Bar.convertOptions(options));
};
</script>
</head>
<body>

  <div id="char_div" style="width: 100%; height: 500px;"></div>
</body>
</html>
```

http:/127.0.0.1:5000/index.php?entryPoint=customEntryPoint



## Reference:

https://support.sugarcrm.com/Documentation/Sugar_Developer/Sugar_Developer_Guide_10.2/Architecture/Entry_Points/Creating_Custom_Entry_Points/
