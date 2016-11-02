---
layout: post
title: getting-started
description: getting started
platform: js
control: Control Name undefined
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the Aurelia AutoComplete with the step-by-step instructions.

## Create an AutoComplete

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).

We configured a Syncfusion template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). The above link is explain set of commands to run and install the required packages for Syncfusion Aurelia application.

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
    <script src="https://ajax.aspnetcdn.com/ajax/jquery.validate/1.14.0/jquery.validate.min.js"> </script>
    <script src="http://cdn.syncfusion.com/{{site.releaseversion}}/js/web/ej.web.all.min.js" type="text/javascript"></script>

    <script src="systemjs.config.js"></script>
  </head>
  <body>
   <ej-app>Loading...</ej-app>
  </body>



{% endhighlight %}



   Create an autocomplete folder inside `src/samples/` location.

   Create **html** file inside `src/samples/autocomplete` folder and use the below code example to render the Aurelia AutoComplete component.    

    Properties can be defined with `e-` prefix and long text properties needs to separate by `-`. E.g. (`e-watermark-text`, `e-width`).

Create **input** element with in template as below.

{% highlight html %}

<template>
    <div class="frame">
        <div class="atccontrol">
            <span class="txt">Car:</span>
            <input type="text" id="selectCar" ej-autocomplete="e-watermark-text:Select a car;" />
        </div>
    </div>
    </template>



{% endhighlight %}



To render the Aurelia AutoComplete using below code.

{% highlight js %}

export class BasicUse {
    constructor() { }
}



{% endhighlight %}



![](getting-started_images\getting-started_img1.png)



## Data binding

The data for AutoComplete suggestion list which can be populated using the `dataSource` property. 

{% highlight html %}

<template>
    <div class="frame">
        <div class="atccontrol">
            <span class="txt">Car:</span>
            <input type="text" id="selectCar" ej-autocomplete="e-watermark-text:Select a car; e-data-source.bind: carList;" />
        </div>
    </div>
</template> 


{% endhighlight %}



{% highlight js %}

export class BasicUse {
  constructor() {
    this.carList = [
      'Audi S6', 'Austin-Healey', 'Alfa Romeo', 'Aston Martin',
      'BMW 7', 'Bentley Mulsanne', 'Bugatti Veyron',
      'Chevrolet Camaro', 'Cadillac',
      'Duesenberg J', 'Dodge Sprinter',
      'Elantra', 'Excavator',
      'Ford Boss 302', 'Ferrari 360', 'Ford Thunderbird',
      'GAZ Siber',
      'Honda S2000', 'Hyundai Santro',
      'Isuzu Swift', 'Infiniti Skyline',
      'Jaguar XJS',
      'Kia Sedona EX', 'Koenigsegg Agera',
      'Lotus Esprit', 'Lamborghini Diablo',
      'Mercedes-Benz', 'Mercury Coupe', 'Maruti Alto 800',
      'Nissan Qashqai',
      'Oldsmobile S98', 'Opel Superboss',
      'Porsche 356', 'Pontiac Sunbird',
      'Scion SRS/SC/SD', 'Saab Sportcombi', 'Subaru Sambar', 'Suzuki Swift',
      'Triumph Spitfire', 'Toyota 2000GT',
      'Volvo P1800', 'Volkswagen Shirako'
    ];
  }
} 


{% endhighlight %}



![](getting-started_images\getting-started_img2.png)

## Enable Popup Button


This button helps you to show all the available suggestions on clicking it.

{% highlight html %}

<template>
    <div class="frame">
        <div class="atccontrol">
                <span class="txt">Car:</span>
            <input type="text" id="selectCar" ej-autocomplete="e-width.bind:width;e-show-popup-button:true; e-watermark-text:Select a car; e-data-source.bind: carList;" />
        </div>
    </div>
</template> 


{% endhighlight %}



![](getting-started_images\getting-started_img3.png)


 N> You can find the Rotator properties from the [API reference](https://help.syncfusion.com/api/js/ejautocomplete) document 



