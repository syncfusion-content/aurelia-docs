---
layout: post
title: Key-Performance-Indicator-KPI
description: key performance indicator (KPI)
platform: js
control: PivotGrid
documentation: ug
api: /api/js/ejpivotgrid
---

# KPI

Key Performance Indicators (KPI) are business metrics that help you to figure out the progress of an enterprise when meeting its business goals.

The different indicators available in the KPI are:

* KPI value: A physical measure or a calculated measure.
* KPI goal: Defines the target for the measure.
* KPI status: Evaluates the current status of the value compared to the goal.
* KPI trend: Evaluates the current trend of the value compared to the goal.

The **“KpiElements”** class in the OLAP base library holds the KPI name, and when its object is added to an OlapReport, you can view the resultant information in the PivotGrid.

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
              fieldName: '[Measures].[Growth in Customer Base Trend]'
            }
          ],
          axis: 'columns'
        }
      ]
    };
  }
}
{% endhighlight %}


![](KPI_images/ClientSideKPI.png)