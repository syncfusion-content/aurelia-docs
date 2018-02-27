---
layout: post
title: Number format
description: Number format
platform: js
control: PivotGrid
documentation: ug
api: /api/js/ejpivotgrid
---

# Number Format

I> This feature is applicable for all modes.

Allows you to specify the required number format that should be used in values of the PivotGrid by setting the `format`. Following are supported number formats:

* number
* decimal
* currency
* percentage
* date
* time
* scientific
* accounting
* fraction
* string

## Relational

{% highlight js %}

export class BasicUse {
  constructor() {
    this.pivotData = {
            //..
            values: [
                {
                    fieldName: "Amount",
                    fieldCaption: "Amount",
                    format: "currency" //Specify the format here
                },
                {
                    fieldName: "Quantity",
                    fieldCaption: "Quantity",
                    format: "decimal"
                }
            ]
        }
    }
 }

{% endhighlight %}

![](Number-Format_images/RelationalClient.png)

## OLAP

{% highlight html %}

export class BasicUse {
  constructor() {
    this.pivotData = {
        //..
        values: [{
            measures: [{
                fieldName: "[Measures].[Internet Sales Amount]",
                format: "percent" //Specify the format here
            }],
            axis: "columns"
        }]
    }
  }
}

{% endhighlight %}

![](Number-Format_images/OlapClient.png)
