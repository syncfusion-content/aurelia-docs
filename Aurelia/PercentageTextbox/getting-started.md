---
layout: post
title: getting-started
description: getting started
platform: js
control: PercentageTextbox
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the Aurelia PercentageTextbox with the step-by-step instructions.

## Create an PercentageTextbox

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).

We already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

> git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
> cd syncfusion-template-repository
> npm install
> jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia PercentageTextbox component.

* Create `percentagetextbox` folder inside `src/samples/` location.
* Create `percentagetextbox.html` file inside `src/samples/percentagetextbox` folder and use the below code example to render the PercentageTextbox component.

{% highlight html %}

<template>
     <input id="percent" type="text" ej-percentage-textbox="e-value.bind:percentValue;e-width.bind:percentWidth" />
</template>

{% endhighlight %}

* Create `percentagetextbox.js` file with the below code snippet inside `src/samples/percentagetextbox` folder.

{% highlight javascript %}

export class Default {
    constructor() {
      this.percentValue = 5;
      this.percentWidth = '100%';
    }
}

{% endhighlight %}

* Now, we are going to configure the navigation for created Textbox sample in `src/app.js` file.

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
   { route: 'percentagetextbox',        name: 'percentagetextbox',       moduleId: 'samples/percentagetextbox/percentagetextbox',                
                nav: true, title: 'PercentageTextbox' }
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

You can set the “minValue” and “maxValue” in Percentage text boxes for maintaining the range in Textbox widgets. In this scenario, you have to enter the values between the given ranges. The following code example illustrates how to achieve this.

{% highlight html %}
<template>
           <input id="percent" type="text" ej-percentage-textbox="e-value.bind:percentValue;e-min-value.bind:minimumValue;e-max-value-bind:maximumValue" />
</template>
{% endhighlight %}


{% highlight javascript %}

export class Default {
    constructor() {
      this.percentValue = 5;
      this.minimumValue = 30;
      this.maximumValue = 100;
    }
}
{% endhighlight %}