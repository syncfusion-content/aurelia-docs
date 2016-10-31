---
layout: post
title: Getting started with Syncfusion Essential HeatMap for Aurelia
description: Getting started walk through to create your first Heat map.
platform: Aurelia
control: ejHeatMap
keywords: HeatMap, js heatmap, Populating data
---

# Getting Started

This section helps to get started of the HeatMap component for Aurelia. 

## Initialize HeatMap
* To create Syncfusion Aurelia application refer [Aurelia Getting Started documentation](https://help.syncfusion.com/aurelia/overview#getting-started "").
* Create `heatmap` folder inside `src/samples` location.
* Create `heatmap.html` file inside  `src/samples/heatmap` folder and use the below code for rendering HeatMap component 

The HeatMap can be created from a HTML ‘div’ element. To create the HeatMap, you should call the 'ejHeatMap' jQuery plug-in function.

{% highlight html %}

<template>
    <div>
        <ej-heat-map e-width="100%" id="heatmap"
                     e-color-mapping-collection.bind="colorMappingCollection"
                     e-is-responsive="true"
                     e-items-source.bind="itemsSource"
                     e-items-mapping.bind="itemsMapping">
        </ej-heat-map>
    </div>
			
{% endhighlight %}

### Prepare and Populate data

Populate product information in a collection called `ItemsSource`.

### Map data into HeatMap

Now data is ready, next we need to configure data source and map rows and columns to visualize. For that, need to prepare `ItemsMapping` add it in resource and set items source and mapping.
Next we can configure color range for these values using color mapping and also configure items mapping based on items source.

* Create `heatmap.js` file inside `src/samples/heatmap` folder with below code snippet.

{% highlight javascript %}

export class BasicUse {
    constructor() {
        let itemSource = [];
        let columns = ["Vegie-spread", "Tofuaa", "Alice Mutton", "Konbu", "Fltemysost", "Perth Pasties", "Boston Crab Meat", "Raclette Courdavault"]
        for (var i = 0; i < columns.length; i++) {
            for (var j = 0; j < 8; j++) {
                var value = Math.floor((Math.random() * 100) + 1);
                itemSource.push({ ProductName: columns[i], Year: "Y"+(2011 + j), Value: value })
            }
        }; 
        let colorMappingCollection = [
          { value: 0, color: '#8ec8f8', label: { text: '0' } },
          { value: 100, color: '#0d47a1', label: { text: '100' } }
        ];
        this.colorMappingCollection = colorMappingCollection;
        this.itemsMapping = {
            column: { 'propertyName': 'ProductName', 'displayName': 'Product Name' },
            row: { 'propertyName': 'Year', 'displayName': 'Year' },
            value: { 'propertyName': 'Value' },
            columnMapping: [
                { 'propertyName': columns[0], 'displayName': columns[0] },
                { 'propertyName': columns[1], 'displayName': columns[1] },
                { 'propertyName': columns[2], 'displayName': columns[2] },
                { 'propertyName': columns[3], 'displayName': columns[3] },
                { 'propertyName': columns[4], 'displayName': columns[4] },
                { 'propertyName': columns[5], 'displayName': columns[5] },
                { 'propertyName': columns[6], 'displayName': columns[6] },
                { 'propertyName': columns[7], 'displayName': columns[7] },

            ],
            headerMapping: { 'propertyName': 'Year', 'displayName': 'Year' }
        };
        this.itemsSource = itemSource;
    }
}

{% endhighlight %}

![](Getting-Started_images/Getting-Started_img1.png)

## Initialize Legend

A legend control is used to represent range value in a gradient, create a legend with the same color mapping as shown below.
 
{% highlight html %}

<template>
    <div>
        <ej-heat-map-legend style="margin: 0 auto; text-align: center;" 
            id="heatmap_legend"
            e-height="50px"
            e-width="75%"
            e-showlabel="true"
            e-color-mapping-collection.bind="colorMappingCollection">
        </ej-heat-map-legend>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}
 
export class BasicUse {
    constructor() {
      let colorMappingCollection = [
        { value: 0, color: '#8ec8f8', label: { text: '0' } },
        { value: 100, color: '#0d47a1', label: { text: '100' } }
      ];
      this.colorMappingCollection = colorMappingCollection;
    }
}

{% endhighlight %}

![](Getting-Started_images/Getting-Started_img2.png)