---
layout: post
title: getting-started
description: getting started
platform: js
control: CurrencyTextbox
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the Aurelia CurrencyTextbox with the step-by-step instructions.

## Create an CurrencyTextbox

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).

We already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

> git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
> cd syncfusion-template-repository
> npm install
> jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia CurrencyTextbox component.

* Create `currencytextbox` folder inside `src/samples/` location.
* Create `currencytextbox.html` file inside `src/samples/currencytextbox` folder and use the below code example to render the CurrencyTextbox component.

{% highlight html %}

<template>
     <input id="currency" type="text" ej-currency-textbox="e-value.bind:currencyValue;e-width.bind:cwidth" />
</template>

{% endhighlight %}

* Create `currencytextbox.js` file with the below code snippet inside `src/samples/currencytextbox` folder.

{% highlight javascript %}

export class Default {
    constructor() {
      this.currencyValue = 500;
      this.cwidth = '100%';
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
   { route: 'currencytextbox',        name: 'currencytextbox',       moduleId: 'samples/currencytextbox/currencytextbox',                
                nav: true, title: 'CurrencyTextbox' }
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

You can set the “minValue" and “maxValue" in Currency text boxes for maintaining the range in Textboxes widgets. In this scenario, you have to enter the values between the given ranges. The following code example illustrates how to achieve this.

{% highlight html %}
<template>
           <input id="currency" type="text" ej-currency-textbox="e-value.bind:cValue;e-min-value.bind:minvalue;e-max-value.bind:maxvalue" />
</template>
{% endhighlight %}


{% highlight javascript %}

export class Default {
    constructor() {
      this.cvalue = 500;
      this.minvalue = 30;
      this.maxvalue = 1000;
    }
}
{% endhighlight %}