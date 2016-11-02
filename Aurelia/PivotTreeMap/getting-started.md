---
title: Getting Started for Aurelia PivotTreeMap
description: How to create a PivotTreeMap with data source.
platform: Aurelia
control: PivotTreeMap
documentation: ug
keywords: ejpivottreemap, pivottreemap, js pivottreemap
---

# Getting Started

Before we start with the PivotTreeMap, please refer [this page](https://help.syncfusion.com/aurelia/overview#getting-started) page for general information regarding integrating Syncfusion widgets.

For quick start, we already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

    > git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
    > cd syncfusion-template-repository
    > npm install
    > jspm install

{% endhighlight %}

### Control Initialization

The below steps describes to create Syncfusion Aurelia PivotTreeMap component.

    Create `pivottreemap` folder inside `src/samples/` location.
    Create `pivottreemap.html` file inside `src/samples/pivottreemap` folder and use the below code example to render the PivotTreeMap component.

{% highlight html %}

<template>
  <require from="./pivottreemap.css"></require>
  <div>
    <ej-pivot-tree-map id="PivotTreeMap1"></ej-pivot-tree-map>
  </div>
</template>

{% endhighlight %}

* Create `pivottreemap.js` file inside `src/samples/pivottreemap` folder with below code snippet.

{% highlight html %}

export class BasicUse {

  constructor() {}

}

{% endhighlight %}

* Create `pivottreemap.css` file inside `src/samples/pivottreemap` folder with below code snippet.

{% highlight html %}

ej-pivot-tree-map {
    min-height: 275px; 
    min-width: 525px; 
    height: 460px; 
    width: 99%; 
    position:relative !important; 
    display: block;
}

{% endhighlight %}

### Populate PivotTreeMap with Data

Let us now see how to populate the PivotTreeMap control using a sample data as shown below.

{% highlight html %}

<template>
  <require from="./pivottreemap.css"></require>  
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

{% highlight html %}

export class BasicUse {
  constructor() {
    this.pivotData = {
      data: 'http://bi.syncfusion.com/olap/msmdpump.dll', //data
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

The above code will generate a simple PivotTreeMap with internet sales amount over a period of fiscal years across different customer geographic locations.

![](getting-started_images/Olap.png)