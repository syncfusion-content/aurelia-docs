---
layout: post
title: getting-started
description: getting started for Button with Aurelia
platform: aurelia
control: Button
documentation: ug
---

# GettingStarted

This section discloses the details on how to render and configure Button component in an Aurelia application.

## Create Button 

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).
We have already configured a template project in GitHub repository syncfusion-template-repository. Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight javascript %}

*	git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository" 
*	cd syncfusion-template-repository
*	npm install
*	jspm install

{% endhighlight %}

The below steps describes the steps to create Syncfusion Aurelia Button component.

Create Button folder inside src/samples/ location in sample files folder.

Create an HTML file (here Button.html file) inside newly created folder and use the below code example to render the Button component.

{% highlight HTML %}

<table>
    <tr>
        <td >My First Button</td>
        <td>
            <button id="button" ej-button>Button</button>
        </td>
    </tr>
</table>

{% endhighlight %}

Create a javascript file in Aurelia application and add the Model class for binding with Button component as given below.
Here, for example, we created the  Button.js file with the below code snippet inside src/samples/Button folder.

{% highlight javascript %}

export class Button{
}

{% endhighlight %}

### Configure Router

Now that, we are done with adding Button component, let us see how to configure our Aurelia application to add additional tab for showcasing Button component.

The Routing configuration is available inside 'src/app.js' file. 

Add the below  code to the config.map method.

{% highlight javascript %}

{ route: 'Button', name: 'Button', moduleId: 'samples/Button/Button', nav: true, title: 'Button' }

{% endhighlight %}

### Run the application

Execute the following command to run the application

{% highlight javascript %}

	gulp watch

{% endhighlight %}

Execution of above code will render the following output.
  

## Configuring Button control

This section encompasses the details on how you can configure the Button control in your application and customize it with various properties such as various size based on your requirement.
	
To modify the size of the Button and rename the button, add the following snippet in your html file.

{% highlight HTML %}

<template>    
<section>
    <h3>Basic Syncfusion JavaScript Button API sample</h3>
	<input id="button" ej-button="e-text.bind:'Button'"></input>        
</section>
</template>

{% endhighlight %}

The following screenshot illustrates the Button control with text and size properties.
 
![](Getting-Started_images/Getting-Started_img1.jpg)