---
layout: post
title: getting-started
description: getting started
platform: js
control: Slider
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the Aurelia Slider with the step-by-step instructions.

## Create an Slider

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).

We already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

> git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
> cd syncfusion-template-repository
> npm install
> jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia Slider component.

* Create `slider` folder inside `src/samples/` location.
* Create `slider.html` file inside `src/samples/slider` folder and use the below code example to render the slider component.

{% highlight html %}

<template>
    <div id="slider" ej-slider="e-value.bind:slidervalue;e-width.bind:width"></div>
</template>

{% endhighlight %}

* Create `slider.js` file with the below code snippet inside `src/samples/slider` folder.

{% highlight javascript %}

export class Default {
    constructor() {
        this.slidervalue = 40;
        this.width = '100%';
    }
}

{% endhighlight %}

* Now, we are going to configure the navigation for created Slider sample in `src/app.js` file.

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
   { route: 'slider',        name: 'slider',       moduleId: 'samples/slider/slider',                
                nav: true, title: 'Slider' }
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


## Set Min and Max Values

You can set the ???minValue??? and ???maxValue???  maintaining the range in slider widgets. The following code example illustrates how to achieve this.

{% highlight html %}
<template>
            <div id="slider" ej-slider="e-value.bind:slidervalue;e-width.bind:width;e-min-value.bind:minvalue;e-max-value.bind:maxvalue"></div>
</template>
{% endhighlight %}


{% highlight javascript %}

export class Default {
    constructor() {
      this.slidervalue = 40;
      this.width = '100%';
      this.minvalue = 40;
      this.maxvalue = 100;
    }
}
{% endhighlight %}