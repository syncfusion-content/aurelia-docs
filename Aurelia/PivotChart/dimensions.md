---
title: Dimensions
description: dimensions
platform: Aurelia
control: PivotChart
documentation: ug
api: /api/js/ejpivotchart
---

# Dimensions

## Set size in percentage

You can customize the pivot chart dimension by setting the width and height of the widget in percentage.

{% highlight html %}

<template>
    <div>
    <ej-pivot-chart id="PivotChart1" e-data-source.bind="pivotData" e-load.bind="loadTheme" e-common-series-options.bind="commonSeries" e-legend.bind="legend"
      e-size.bind="size" e-primary-y-axis.bind="primaryYAxis" >
    </ej-pivot-chart>
  </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class BasicUse {
  constructor() {

        ... //datasource

       this.size = {
            height: "80%",
            width: "80%"
        };
    }
}

{% endhighlight %}

## Set size in pixels

You can customize the pivot chart dimension by setting the width and height of the widget in pixels.

{% highlight javascript %}

export class BasicUse {
  constructor() {

        ... //datasource

       this.size = {
            height: "460px",
            width: "950px"
        };
    }
}

{% endhighlight %}

![](dimensions_images/Dimensions.png)

## Responsive

The pivot chart widget supports responsive rendering based on the target device (desktop and tablet) resolution. It supports resolution upto 1024x600. You can enable the responsiveness in the pivot chart by setting the `isResponsive` property to true.

{% highlight html %}

<template>
  <require from="./relational.css"></require>
  <div>
    <ej-pivot-chart e-data-source.bind="pivotData" e-load.bind="loadTheme" e-common-series-options.bind="commonSeries" e-legend.bind="legend"
      e-size.bind="size" e-primary-y-axis.bind="primaryYAxis" e-is-responsive.bind=true>
    </ej-pivot-chart>
  </div>
</template>

{% endhighlight %}

![](dimensions_images/NormalView.png)

_Normal View_

![](dimensions_images/ResponsiveView.png)

_ResponsiveView_