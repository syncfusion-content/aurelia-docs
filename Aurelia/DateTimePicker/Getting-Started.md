---
layout: post
title: getting-started
description: getting started for DateTimePicker
platform: aurelia
control: DateTimePicker
documentation: ug
---

# GettingStarted

This section discloses the details on how to render and configure DateTimePicker component in an Aurelia application.

## Create DateTimePicker 

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).
We have already configured a template project in GitHub repository syncfusion-template-repository. Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight javascript %}

*	git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository" 
*	cd syncfusion-template-repository
*	npm install
*	jspm install

{% endhighlight %}

The below steps describes the steps to create Syncfusion Aurelia DateTimePicker component.

Create DateTimePicker folder inside src/samples/ location in sample files folder.

Create an HTML file (here DateTimePicker.html file) inside newly created folder and use the below code example to render the DateTimePicker component.

{% highlight HTML %}

<input id="datetimepick" ej-date-time-picker/>

{% endhighlight %}

Create a javascript file in Aurelia application and add the Model class for binding with DateTimePicker component as given below.
Here, for example, we created the  datetimepicker.js file with the below code snippet inside src/samples/DateTimePicker folder.

{% highlight javascript %}

export class DateTimePicker{

}

{% endhighlight %}

### Configure Router

Now that, we are done with adding DateTimePicker component, let us see how to configure our Aurelia application to add additional tab for showcasing DateTimePicker component.

The Routing configuration is available inside 'src/app.js' file. 

Add the below  code to the config.map method.

{% highlight javascript %}

{ route: 'datetimepicker', name: 'datetimepicker', moduleId: 'samples/datetimepicker/datetimepicker', nav: true, title: 'Datetimepicker' }

{% endhighlight %}

### Run the application

Execute the following command to run the application

{% highlight javascript %}

	gulp watch

{% endhighlight %}

Execution of above code will render the following output.

![](getting-started_images/default.png)   

## Two way binding

DateTimePicker value can be bound to the model values to synchronize the date and time values between view and model. 
Check Below code example to know about two way binding

{% highlight HTML %}

<input id="datepick" ej-date-picker="e-value.two-way:dateValue;"  ></input>      

{% endhighlight%}

In script section set the Model values,

{% highlight javascript %}

export class DateTimePicker {
    constructor(){
        this.selectedDate = new Date("11/23/2016 4:00 PM");
    }
}

{% endhighlight%}

The following screenshot illustrates the output of above code.

![](getting-started_images/datetime.png)  

### Configuring the DateTimePicker properties

DateTimePicker component have options to render the calendar with min and max date specified.

{% highlight HTML %}

<input id="datetimepick" ej-date-time-picker="e-min-date-time.bind: minDatetime; e-max-date-time.bind: maxDatetime;" />        

{% endhighlight %}

Set the required variable values in corresponding script file like below,

export class DatePickAPI {
    constructor() {
      this.minDatetime = new Date("11/1/2016 10:00 AM");
      this.maxDatetime = new Date("11/27/2016 10:00 PM");
     }
}

Execution of above code will render the following output.

![](getting-started_images/minmax.png) 