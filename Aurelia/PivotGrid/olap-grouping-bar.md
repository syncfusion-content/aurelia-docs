---
layout: post
title: Grouping-Bar
description: grouping bar
platform: js
control: PivotGrid
documentation: ug
api: /api/js/ejpivotgrid
---

# Grouping Bar

## Initialization
Grouping bar allows you to dynamically alter the report by filter and remove operations in the PivotGrid control. Based on the OLAP datasource and report bound to the PivotGrid control, the grouping bar will be automatically populated. You can enable the grouping bar option in the PivotGrid by setting the [`enableGroupingBar`](/api/js/ejpivotgrid#members:enablegroupingbar) property to true.

{% highlight html %}

<template>
  <div>
    <ej-pivot-grid id="groupingBar" e-enable-grouping-bar="true">
    </ej-pivot-grid>
  </div>
</template>

{% endhighlight %}

{% highlight js %}

export class BasicUse {
  constructor() {
    this.pivotData = {
      data: 'https://bi.syncfusion.com/olap/msmdpump.dll', //data
      catalog: 'Adventure Works DW 2008 SE',
      cube: 'Adventure Works',
      rows: [
        {
          fieldName: '[Date].[Fiscal]'
        }
      ],
      columns: [
        {
          fieldName: '[Customer].[Customer Geography]'
        }
      ],
      values: [
        {
          measures: [
            {
              fieldName: '[Measures].[Internet Sales Amount]'
            }
          ],
          axis: 'columns'
        }
      ]
    };
  }
}

{% endhighlight %}

![](Grouping-Bar_images/olapclientgroupingbar.png)

## Drag and drop

You can alter the report on fly through the drag-and-drop operation.

![](Grouping-Bar_images/GBar_Olap.png)

## Context menu

You can also alter the report by using the context menu.

![](Grouping-Bar_images/CMenu_Olap.png)

## Searching values
Search option in the grouping bar allows you to search a specific value that needs to be filtered from the list of values in the filter pop-up window.

![](Grouping-Bar_images/OlapClntFiltering.png)

![](Grouping-Bar_images/olapclientsearching.png)

## Filtering values
Filtering option in the grouping bar allows you to select a specific set of values that needs to be displayed in the PivotGrid control. At least, one value should be present in the checked state while filtering. Otherwise “Ok” will be disabled.

![](Grouping-Bar_images/OlapClntFiltering.png)

![](Grouping-Bar_images/olapclientfiltering.png)

## Removing field
Remove option in the grouping bar allows you to completely remove a specific field from the PivotGrid control. Remove operation can be achieved either by clicking remove icon available in each field or by dragging and dropping the field out of the grouping bar region.

![](Grouping-Bar_images/Olapclientremove.png)

![](Grouping-Bar_images/OlapAFRemoving.png)


