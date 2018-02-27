---
layout: post
title: Named Set
description: named set
platform: js
control: PivotTreeMap
documentation: ug
api: /api/js/ejpivottreemap
---

# Named sets

Named sets is a multidimensional expression (MDX) that returns a set of dimension members which can be created by combining the cube data, arithmetic operators, numbers, and functions.

You can bind the named sets in the pivot tree map by setting it's unique name in the `fieldName` property either in the row or column axis and setting the `isNamedSets` Boolean property to true.

{% highlight html %}

<template>
  <div>
   <ej-pivot-tree-map id="PivotTreeMap1" e-data-source.bind="pivotData">
    </ej-pivot-tree-map>
  </div>

  <!--Tooltip labels can be localized here-->
  <script id="tooltipTemplate" type="application/jsrender">
    <div style="background:White; color:black; font-size:12px; font-weight:normal; border: 1px solid #4D4D4D; white-space: nowrap;border-radius: 2px; margin-right: 25px; min-width: 110px;padding-right: 5px; padding-left: 5px; padding-bottom: 2px ;width: auto; height: auto;">
      <div>Measure(s) : {{:~Measures(#data)}}</div><div>Row : {{:~Row(#data)}}</div><div>Column : {{:~Column(#data)}}</div><div>Value : {{:~Value(#data)}}</div>
    </div>
  </script>
</template>

{% endhighlight %}

{% highlight js %}

export class BasicUse {
  constructor() {
    this.pivotData = {
            data: "http://bi.syncfusion.com/olap/msmdpump.dll", //data
            catalog: "Adventure Works DW 2008 SE",
            cube: "Adventure Works",
            columns: [{
               fieldName: "[Customer].[Customer Geography]"
            }],
            rows: [{
               fieldName: "[Core Product Group]",
               isNamedSets: true
            }],
            values: [{
               measures: [{
               fieldName: "[Measures].[Internet Sales Amount]",
            }],
            axis: "columns"
        }]
    };
  }
}

{% endhighlight %}

![](NamedSets_images/namedset.png)
