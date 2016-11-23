---
layout: post
title: getting started
description: getting started
platform: js
control: ListView
documentation: ug
---

# Getting Started

The Aurelia **ListView** control allows you to select an item from a list-like interface and provides the infrastructure to display a set of data items in different layouts or views. Lists display data, data navigation, result lists, and data entry. 

This section helps to understand the getting started of the Aurelia ListView with the step-by-step instructions.

## Create an ListView 


You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started](https://help.syncfusion.com/aurelia/overview) Documentation.

We configured a Syncfusion template project in GitHub repository [Syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). The above link is explain set of commands to run and install the required packages for Syncfusion Aurelia application. 

Create a new HTML file and include the below code:

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

Create a **listview**.**html** file inside “src/samples/listview” folder and use the below code example to render the Aurelia ListView component.    

    Properties can be defined with `e-` prefix and long text properties needs to separate by `-`. E.g. (`e-show-header`, `e-width`).

Create **input** element with in template as below.

{% highlight html %}

<template>
    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <ej-list-view id="defaultlistbox" e-width="400">
                    <ul>
                        <li data-ej-text="Artwork"></li>
                        <li data-ej-text="Abstract"></li>
                        <li data-ej-text="2 Acrylic Mediums"></li>
                        <li data-ej-text="Creative Acrylic"></li>
                        <li data-ej-text="Modern Painting"></li>
                        <li data-ej-text="Canvas Art"></li>
                        <li data-ej-text="Black white"></li>
                        <li data-ej-text="Children"></li>
                    </ul>
                </ej-list-view>
            </div>
        </div>
    </div>
</template>

{% endhighlight %}

To render the Aurelia ListView using below code.

{% highlight js %}

export class BasicUse {
    constructor() { }
}

{% endhighlight %}


Run the above code to render the following output.

![](Getting_Started_images\createanlistview_img1.png)

## Data binding

The data for the suggestion list can be populated using the **dataSource** property.

Follow the below code to bind the ListView datasource locally.

{% highlight html %}

<template>
    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <ej-list-view id="defaultlistbox" e-data-source.bind="dbitem" e-field-settings.bind="musicFields" e-width="400">
                </ej-list-view>
            </div>
        </div>
    </div>
</template>

{% endhighlight %}



{% highlight js %}

export class BasicUse {
  constructor() {
    this.dbitem = [{ 'Texts': 'Discover Music' },
            { 'Texts': 'Sales and Events' },
            { 'Texts': 'Categories' },
            { 'Texts': 'MP3 Albums' },
            { 'Texts': 'More in Music' }];
    this.musicFields = {'text': 'Texts'};
  }
}


{% endhighlight %}

Run the above code to render the following output.

![](Getting_Started_images\databinding_img1.png)

## Add Header

We can add a header for Aurelia **ListView**. Refer to the following script.

{% highlight html %}

<template>
    <require from="./basic-use.css"></require>
    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <ej-list-view id="defaultlistbox" e-show-header="true" e-header-title="Favorite" e-width="400">
                    <ul>
                        <li data-ej-text="Discover Music"></li>
                        <li data-ej-text="Sales and Events"></li>
                        <li data-ej-text="Categories"></li>
                        <li data-ej-text="MP3 Albums"></li>
                        <li data-ej-text="More in Music"></li>
                    </ul>
                </ej-list-view>
            </div>
        </div>
    </div>
</template>


{% endhighlight %}

Run the above code to render the following output.

![](Getting_Started_images\addheader_img1.png)
