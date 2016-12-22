---
layout: post
title: getting-started
description: getting started for SplitButton
platform: aurelia
control: SplitButton
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the Aurelia SplitButton with the step-by-step instructions.

## Create a SplitButton in Aurelia

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).

We already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

> git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
> cd syncfusion-template-repository
> npm install
> jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia SplitButton component.

* Create `splitButton` folder inside `src/samples/` location.
* Create `splitButton.html` file inside `src/samples/splitButton` folder and use the below code example to render the SplitButton component.

{% highlight html %}

<template>
    <button id="miniBtn" ej-split-button="e-size.bind: miniBtnValue;
                        e-show-rounded-corner.bind: roundedCorner;
                        e-target-id: subMenu2;
                        e-button-mode.bind: buttonMode;
                        e-text: login"></button>
                        <ul id="subMenu2">
                            <li><span>User</span></li>
                            <li><span>Guest</span></li>
                            <li><span>Admin</span></li>
                        </ul>
</template>

{% endhighlight %}

* Create `splitButton.js` file with the below code snippet inside `src/samples/splitButton` folder.

{% highlight javascript %}

export class SplitButton {
  constructor() {
    this.miniBtnValue = 'mini';
    this.roundedCorner = true;
    this.index = 0;
    this.buttonMode = 'split';
  }
  onChange(args) {
    this.buttonMode = args.detail.value;
  }
}

{% endhighlight %}

* Now, we are going to configure the navigation for created SplitButton sample in `src/app.js` file.

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
   { route: 'spliButton',        name: 'splitButton',       moduleId: 'samples/splitButton/splitButton',                
                nav: true, title: 'SplitButton' }
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

![](getting-started_images/getting-started_img1.png) 


