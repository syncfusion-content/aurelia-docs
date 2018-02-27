---
title: Multi-level Labels
description: multilevellabels
platform: Aurelia
control: PivotChart
documentation: ug
api: /api/js/ejpivotchart
---

# Multi-level labels

Multi-level labels allow you to drill down to access the detailed level of data or drill up to see the summarized data by using the expander present in the OLAP chart. You can enable this option by setting the [`enableMultiLevelLabels`](/api/js/ejchart#members:enableMultiLevelLabels) property to **“true”.**

{% highlight html %}

<template>
  <div>
    <ej-pivot-chart e-enable-multi-level-labels.bind ="true">
    </ej-pivot-chart>
  </div>
</template>

{% endhighlight %}


## Relational

![](multilevellabels_images/relational.png)

## OLAP

![](multilevellabels_images/olap.png)