---
layout: post
title: getting started  
description: getting started  
platform: js
control: ListBox
documentation: ug
---

# Getting Started  

The Aurelia **ListBox** control contains a list of selectable items. It performs exceptionally well with thousands of items and supports checkboxes, template, single and multiple selection, keyboard navigation and virtual scrolling.

This section helps to understand the getting started of the Aurelia ListBox with the step-by-step instructions.

## Create an ListBox 

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started](https://help.syncfusion.com/aurelia/overview) documentation.

We configured a Syncfusion template project in GitHub repository [Syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). The above link is explaining set of commands to run and install the required packages for Syncfusion Aurelia application.

Create a HTML file and include the below code:

{% highlight html %}

<!DOCTYPE html>
<html>
   <head> 
    <link href="//cdn.syncfusion.com/{{site.releaseversion}}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
    <script src="node_modules/core-js/client/shim.min.js"></script>
    <script src="node_modules/zone.js/dist/zone.js"></script>
    <script src="node_modules/reflect-metadata/Reflect.js"></script>
    <script src="node_modules/systemjs/dist/system.src.js"></script>
    <script src="https://code.jquery.com/jquery-3.0.0.min.js"></script>
    <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js" type="text/javascript"></script>
    <script src="https://ajax.aspnetcdn.com/ajax/jquery.validate/1.14.0/jquery.validate.min.js"></script>
    <script src="http://cdn.syncfusion.com/{{site.releaseversion}}/js/web/ej.web.all.min.js" type="text/javascript"></script>
    <script src="systemjs.config.js"></script>
  </head>
  <body>
   <ej-app>Loading...</ej-app>
  </body>


{% endhighlight %}


Create a folder inside “src/samples“ location.

Create a **listbox**.**html** file inside “src/samples/listbox” folder and use the below code example to render the Aurelia ListBox component.    

     Properties can be defined with `e-` prefix and long text properties needs to separate by `-`. E.g. (`e-data-source`, `e-width`).

Create **input** element with in template as below.

{% highlight html %}

<template>
  <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div class="listbox frame">
                    <div class="ctrllabel">Select a car</div>
                    <ul id="selectcar" ej-list-box>
                        <li>Audi A4</li>
                        <li>Audi A5</li>
                        <li>Audi A6</li>
                        <li>Audi A7</li>
                        <li>Audi A8</li>
                        <li>BMW 501</li>
                        <li>BMW 502</li>
                        <li>BMW 503</li>
                        <li>BMW 507</li>
                        <li>BMW 3200</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

{% endhighlight %}

To render the Aurelia ListBox using below code.

{% highlight js %}

export class BasicUse {
    constructor() { }
}

{% endhighlight %}

Run the above code to render the following output.

![](Getting_Started_images\createanlistbox_img1.png)

## Data binding

The data for the suggestion list can be populated using the **dataSource** property. The dataSource binding may be local data binding or remote data binding.

Follow the below code to bind the ListBox dataSource locally.

{% highlight html %}

<template>
    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div class="listbox frame">
                    <div class="ctrllabel">Select a bike</div>
                    <ul id="selectbike" ej-list-box="e-data-source.bind:BikeList; e-fields.bind:fields"></ul>
                </div>
            </div>
        </div>
    </div>

</template>


{% endhighlight %}


{% highlight js %}

export class BasicUse {
  constructor() {
     // declaration
    this.fields = { id: 'empid', value: 'text' };
    this.BikeList = [
                { empid: 'bk1', text: 'Aache RTR' }, { empid: 'bk2', text: 'CBR 150-R' }, { empid: 'bk3', text: 'CBZ Xtreme' },
                { empid: 'bk4', text: 'Discover' }, { empid: 'bk5', text: 'Dazzler' }, { empid: 'bk6', text: 'Flame' },
                { empid: 'bk7', text: 'Fazzer' }, { empid: 'bk8', text: 'FZ-S' }, { empid: 'bk9', text: 'Pulsar' },
                { empid: 'bk10', text: 'Shine' }, { empid: 'bk11', text: 'R15' }, { empid: 'bk12', text: 'Unicorn' }
    ];
  }
}


{% endhighlight %}

Run the above code to render the following output.

![](Getting_Started_images\databinding_img1.png)


Follow the below code to bind the ListBox dataSource using remote.

{% highlight html %}

<template>
    <require from="./data-binding-remote.css"></require>
    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div class="listbox frame">
                    <div class="ctrllabel">Select a customer</div>
                    <ul id="selectcustomer" ej-list-box="e-data-source.bind: dataManger; e-fields.bind: fields; e-query.bind: query;"></ul>
                </div>
            </div>
        </div>
    </div>
</template>

{% endhighlight %}


{% highlight js %}

export class BasicUse {

  constructor() {

     // declaration

    this.fields = { text: 'CustomerID' };

    this.dataManger = ej.DataManager({url: 'http://mvc.syncfusion.com/Services/Northwnd.svc/'}); // eslint-disable-line new-cap

     // Query creation

    this.query = ej.Query().from('Customers').take(10);// eslint-disable-line new-cap

  }

}
{% endhighlight %}

Run the above code to render the following output.

![](Getting_Started_images\databinding_img2.png)


## Selection

The Aurelia **ListBox** widget also supports the item selection.

Use the following code to render the ListBox with selection

{% highlight html %}

<template>
    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div class="listbox frame">
                    <div class="ctrllabel">Select a car</div>
                    <ul id="selectcar" ej-list-box="e-selected-index:2;">
                        <li>Audi A4</li>
                        <li>Audi A5</li>
                        <li>Audi A6</li>
                        <li>Audi A7</li>
                        <li>Audi A8</li>
                        <li>BMW 501</li>
                        <li>BMW 502</li>
                        <li>BMW 503</li>
                        <li>BMW 507</li>
                        <li>BMW 3200</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

{% endhighlight %}

Run the above code to render the following output.

![](Getting_Started_images\selection_img1.png)
