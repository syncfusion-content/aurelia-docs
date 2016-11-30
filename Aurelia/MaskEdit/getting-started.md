---
layout: post
title: getting-started
description: getting started
platform: js
control: MaskEdit
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the Aurelia MaskEdit with the step-by-step instructions.

## Create an MaskEdit Textbox

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).

We already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

> git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
> cd syncfusion-template-repository
> npm install
> jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia MaskEdit component.

* Create `maskedit` folder inside `src/samples/` location.
* Create `maskedit.html` file inside `src/samples/maskedit` folder and use the below code example to render the MaskEdit component.

{% highlight html %}

<template>
       <input id="maskedit" type="text" ej-mask-edit="e-value.bind:mvalue;e-mask-format.bind:maskFormat;e-width.bind:mwidth" />
</template>

{% endhighlight %}

* Create `maskedit.js` file with the below code snippet inside `src/samples/maskedit` folder.

{% highlight javascript %}

export class Default {
    constructor() {
      this.mvalue = '4242422424';
      this.maskFormat = '99 999-99999';
      this.mwidth = '100%';
    }
}

{% endhighlight %}

* Now, we are going to configure the navigation for created MaskEdit sample in `src/app.js` file.

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
   { route: 'maskedit',        name: 'maskedit',       moduleId: 'samples/maskedit/maskedit',                
                nav: true, title: 'maskedit' }
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

## Error Visibility

The MaskEdit has an option that shows the error value with red colored text. It is used to validate the Mask Edit value. You can set the showError property as “true” to enable this option.

The following steps explain the showError property in the MaskEdit control.

{% highlight html %}

<template>
       <input id="maskedit" type="text" ej-mask-edit="e-value.bind:mvalue;e-mask-format.bind:maskFormat;e-show-error.bind:showerror" />
</template>

{% endhighlight %}

{% highlight javascript %}

export class Default {
    constructor() {
      this.mvalue = '123456';
      this.maskFormat = '99 999-99999';
      this.showerror = true;
    }
}

{% endhighlight %}

Execution of above code will render the following output.

![](getting-started-images/getting-started-img2.png)