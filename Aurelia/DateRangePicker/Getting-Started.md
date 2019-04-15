---
layout: post
title: getting-started | DateRangePicker | Aurelia | Syncfusion
description: getting started for DateRangePicker
platform: aurelia
control: DateRangePicker
documentation: ug
---

# Getting Started

This section discloses the details on how to render and configure DateRangePicker component in an Aurelia application.

## Create DateRangePicker

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).
We have already configured a template project in GitHub repository syncfusion-template-repository. Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight javascript %}

*	git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository" 
*	cd syncfusion-template-repository
*	npm install
*	jspm install

{% endhighlight %}

The below steps describes the steps to create Syncfusion Aurelia DateRangePicker component.

Create `dateRangePicker` folder inside `src/samples/` location in sample files folder.

Create an HTML file (here `dateRangePicker.html` file) inside newly created folder and use the below code example to render the DateRangePicker component.

{% highlight HTML %}

<input id="daterangepick" ej-date-range-picker/>

{% endhighlight %}

Create a javascript file in Aurelia application and add the Model class for binding with DateRangePicker component as given below.
Here, for example, we created the  `dateRangePicker.js` file with the below code snippet inside `src/samples/dateRangePicker` folder.

{% highlight javascript %}

export class DateRangePicker{

}

{% endhighlight %}

### Configure Router

Now that, we are done with adding DateRangePicker component, let us see how to configure our Aurelia application to add additional tab for showcasing DateRangePicker component.

The Routing configuration is available inside 'src/app.js' file. 

Add the below  code to the config.map method.

{% highlight javascript %}

{ route: 'dateRangePicker', name: 'dateRangePicker', moduleId: 'samples/dateRangePicker/dateRangePicker', nav: true, title: 'DateRangePicker' }

{% endhighlight %}

### Run the application

Execute the following command to run the application

{% highlight javascript %}

gulp watch

{% endhighlight %}

Execution of above code will render the following output.

![DateRangePicker](getting-started_images/daterangepick.png)

## Get/Set Value

DateRangePicker provides an options to configure all its properties and to get its value. DateRangePicker value can be assigned during initialization or at run time. Below code shows how to assign the values at initialization.

{% highlight HTML %}

<input id="datepick" ej-date-range-picker="e-value.bind:dateValue;"  ></input>

{% endhighlight%}

In script section set the Model values,

{% highlight javascript %}

export class DateRangePicker {
    constructor(){
        this.dateValue = '"11/1/2013 - 12/3/2019"';
    }
}

{% endhighlight%}

N> You can assign values after initialization in DateRangePicker (it helps to get or set value at run time). Let's consider that going to set date range at button click.