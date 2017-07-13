---
layout: post
title: Getting widget instance in view model
description: How to get widget instance in view model
platform: Aurelia
control: Getting started
documentation: ug
keywords: Aurelia,Syncfusion,aurelia-syncfusion-bridge,e-widget
---
# Getting widget instance in view model

The [aurelia-syncfusion-bridge](https://github.com/aurelia-ui-toolkits/aurelia-syncfusion-bridge/) have special property called `e-widget` which will give widget instance in our view model. So, we can access API's and methods of any Syncfusion widget using `e-widget` property.

We can get the widget instance only after the component is created. Since, the Syncfusion component will be created during attached life cycle of Aurelia component. So, widget instance will not be accessible in constructor and attached method. But, setTimeout function used to make widget instance available in attached method.

 To access the widget instance in view model, we recommend the below 3 ways.

 Bind `e-widget` property in view as like the below code snippet which is common for all the 3 methods.

 {% highlight html %}

<template>
    <ej-grid e-widget.bind="grid" e-data-source.two-way="gridData" e-allow-paging=true e-on-record-click.delegate="recordClick($event.detail)">
        <ej-column e-field="OrderID" e-header-text="Order ID" e-text-align="right"></ej-column>
        <ej-column e-field="CustomerID" e-header-text="Customer ID"></ej-column>
    </ej-grid>
</template>

{% endhighlight %}

`Method 1`: **Using TaskQueue**

Inject TaskQueue and get access to the underlying widget instance as like the below code snippet.

{% highlight javascript %}

//attached with TaskQueue 
attached() { 
    this.taskQueue.queueTask(() => {
        setTimeout(() => {
            console.log(this.grid.widget.pluginName); //here we are accessing ejGrid's pluginName.
        }, 1);
    });
}

{% endhighlight %}

`Method 2`: **Using setTimeOut function**

Use the setTimeout function to get the widget instance as like the below code snippet.

{% highlight javascript %}

//attached with setTimeout  
attached() { 
    setTimeout(() => {
        console.log(this.grid.widget.pluginName); // here we are accessing ejGrid's pluginName.
    }, 50)
} 

{% endhighlight %}

`Method 3`: **Using Event handler**

Use any event handler to get the widget instance as like the below code snippet.

{% highlight javascript %}

//Event handler of ejGrid 
recordClick(e) { 
    console.log(this.grid.widget.pluginName); // here we are accessing ejGrid's pluginName.
}

{% endhighlight %}