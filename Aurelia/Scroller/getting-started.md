---
layout: post
title: getting-started
description: getting started - Scroller
platform: aurelia
control: Scroller
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the Aurelia Scroller with the step-by-step instructions.

## Create a Scroller in Aurelia

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).

We already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

> git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
> cd syncfusion-template-repository
> npm install
> jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia Scroller component.

* Create `scroller` folder inside `src/samples/` location.
* Create `scroller.html` file inside `src/samples/scroller` folder and use the below code example to render the Scroller component.

{% highlight html %}

<template>
     <div ej-scroller="e-height:300px;e-width:560px" id="scrollcontent">
                <div>
                    <div class="sampleContent">
                        <h3 style="font-size: 20px;">MVC</h3>
                        <div>
                            <p>
                                Model–view–controller (MVC) is a software architecture pattern which separates the
                            representation of information from the user's interaction with it.
                            The model consists of application data, business rules, logic, and functions. A view can be any
                            output representation of data, such as a chart or a diagram. Multiple views of the same data 
                            are possible, such as a bar chart for management and a tabular view for accountants. 
                            The controller mediates input, converting it to commands for the model or view.The central 
                            ideas behind MVC are code reusability and n addition to dividing the application into three 
                            kinds of components, the MVC design defines the interactions between them.
                            </p>
                            <ul>
                                <li>
                                    <b>A controller </b>can send commands to its associated view to change the view's presentation of the model (e.g., by scrolling through a document). 
                                            It can also send commands to the model to update the model's state (e.g., editing a document).
                                </li>
                                <li>
                                    <b>A model</b> notifies its associated views and controllers when there has been a change in its state. This notification allows the views to produce updated output, and the controllers to change the available set of commands. 
                                        A passive implementation of MVC omits these notifications, because the application does not require them or the software platform does not support them.
                                </li>
                                <li>
                                    <b>A view</b> requests from the model the information that it needs to generate an output representation to the user.
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
</template>

{% endhighlight %}

* Create `scroller.js` file with the below code snippet inside `src/samples/scroller` folder.

{% highlight javascript %}

export class Default {}

{% endhighlight %}

* Now, we are going to configure the navigation for created Scroller sample in `src/app.js` file.

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
   { route: 'scroller',        name: 'scroller',       moduleId: 'samples/scroller/scroller',                
                nav: true, title: 'Scroller' }
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


