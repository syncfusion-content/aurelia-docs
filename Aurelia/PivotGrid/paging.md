---
layout: post
title: Paging
description: paging
platform: js
control: PivotGrid
documentation: ug
api: /api/js/ejpivotgrid
---

# Paging

## Pager

Paging helps you to improve the rendering performance of the pivot grid control by dividing large amount of data into sections and displaying one section at a time. You can enable the paging option in the pivot grid by setting the [`enablePaging`](/api/js/ejpivotgrid#members:enablepaging) property to true. You can provide the page size and current page details for each axis in the [`pagerOptions`](/api/js/ejpivotgrid#members:datasource-pageroptions) property.

To initialize a **Pager**, first you should define a **div** tag with an appropriate **id** attribute which acts as a container for the widget. Then, you can initialize the widget using the **ejPivotPager** method.

Inside the **ejPivotPager** method, the enumeration property mode should be set to **ej.PivotPager.Mode.Both** to display both categorical pager and series pager. The other enumerations such as **ej.PivotPager.Mode.Categorical** and **ej.PivotPager.Mode.Series** will display only the categorical pager and the series pager respectively.

{% highlight html %}

<ej-pivot-pager id="paging" e-target-control-id="PivotGrid1" e-mode="mode"></ej-pivot-pager>
<ej-pivot-grid id="PivotGrid1" e-enable-paging="true"></ej-pivot-grid>

{% endhighlight %}

{% highlight js %}

export class BasicUse {
  constructor() {
    this.pivotData = {
            //...
            pagerOptions: {
                categoricalPageSize: 3,
                seriesPageSize: 3,
                categoricalCurrentPage: 1,
                seriesCurrentPage: 1
            }
        }
        this.mode=ej.PivotPager.Mode.Both;
    }
}

{% endhighlight %}


Following are the navigation options available in the pager:

* Move first: Navigates to the first page.
* Move last: Navigates to the last page.
* Move previous: Navigates to the previous page from the current page.
* Move next: Navigates to the next page from the current page.
* Numeric box: Navigates to the desired page by entering an appropriate page number in the numeric value.

![](Paging_images/paging.png)


## Virtual scrolling

Virtual scrolling is a technique that allows you to view the pivot grid information page by page with the use of vertical and horizontal scrollbar. You can enable the virtual scrolling option in the pivot grid by setting the [`enableVirtualScrolling`](/api/js/ejpivotgrid#members:enablevirtualscrolling) property to true. You can provide the page size and current page details for each axis in the [`pagerOptions`](/api/js/ejpivotgrid#members:pageroptions) property.

{% highlight html %}

<ej-pivot-grid id="PivotGrid1" e-enable-virtual-scrolling="true"></ej-pivot-grid>

{% endhighlight %}

![](Paging_images/virtual-scrolling.png)

## Page settings
The page setting for categorical and series axes are needed to be set in the data source property by using the following properties:

[`categoricalPageSize`](/api/js/ejpivotgrid#members:datasource-pageroptions-categoricalpagesize) - Allows to set the number of categorical columns to be displayed in each page on applying the paging.

[`seriesPageSize`](/api/js/ejpivotgrid#members:datasource-pageroptions-seriespagesize) - Allows to set the number of series rows to be displayed in each page on applying the paging.

[`categoricalCurrentPage`](/api/js/ejpivotgrid#members:datasource-pageroptions-categoricalcurrentpage) - Allows to set the page number to be loaded in the categorical axis by default.

[`seriesCurrentPage`](/api/js/ejpivotgrid#members:datasource-pageroptions-seriescurrentpage) - Allows to set the page number to be loaded in the series axis by default.

