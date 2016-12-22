---
layout: post
title: getting-started
description: getting started
platform: aurelia
control: ColorPicker
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the Aurelia ColorPicker with the step-by-step instructions.

## Create a ColorPicker control

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).

We have already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

> git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
> cd syncfusion-template-repository
> npm install
> jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia ColorPicker component.

* Create `colorpicker` folder inside `src/samples/` location.
* Create `colorpicker.html` file inside `src/samples/colorpicker` folder and use the below code example to render the ColorPicker component.

{% highlight html %}

<template>
       <input id="colorpick" type="text" ej-color-picker="e-value.bind:colorvalue" />
</template>

{% endhighlight %}

* Create `colorpicker.js` file with the below code snippet inside `src/samples/ColorPicker` folder.

{% highlight javascript %}

export class Default {
    constructor() {
      this.colorvalue = '#278787';
    }
}

{% endhighlight %}

* Now, we are going to configure the navigation for created ColorPicker sample in `src/app.js` file.

{% highlight javascript %}

export class App {
 configureRouter(config, router) {
  config.title = 'Aurelia Syncfusion';
  config.map([
   { route: ['', 'welcome'], name: 'welcome', moduleId: 'welcome',                              
                nav: true, title: 'Welcome' },
   { route: 'child-router',  name: 'child-router', moduleId: 'child-router',                         
                nav: true, title: 'Child Router' },
   { route: 'button',        name: 'button', moduleId: 'samples/button/button',                
                nav: true, title: 'Button' },
   { route: 'colorpicker',        name: 'colorpicker',       moduleId: 'samples/colorpicker/colorpicker',                
                nav: true, title: 'ColorPicker' }
 ]);
 this.router = router;
 }
}

{% endhighlight %}


* To run the application, execute the following command.

{% highlight javascript %}

gulp watch

{% endhighlight %}

Execution of above code will render the following output.

![](getting-started-images/getting-started-img1.png) 
