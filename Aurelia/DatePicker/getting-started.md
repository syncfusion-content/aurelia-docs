---
layout: post
title: Getting started with Aurelia 
description: How to start with EJ components with Aureia framework?
platform: js
control: DatePicker
documentation: ug
---

# Getting Started

This section helps to understand the rendering of the DatePicker in Aurelia environment with the step-by-step instructions.

## Create DatePicker with Aurelia 

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).

We already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

  * git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository" 

  * cd syncfusion-template-repository

  * npm install

  * jspm install

The below steps describes to create Syncfusion Aurelia DatePicker component.

Create DatePicker folder inside **src/samples/** location in sample files folder.

Create html file (here datepicker.html file) inside newly created folder and use the below code example to render the DatePicker component.


{% highlight html %}

    <input id="button" ej-date-picker/>

{% endhighlight %}


Create script file in Aurelia application to add the EJ component rendering code, here for example we created the  datepicker.js file with the below code snippet inside src/samples/datepicker folder.


{% highlight javascript %}

    export class DatePickerApi {
    }

{% endhighlight %}


Now, we need to configure the navigation for created DatePicker sample in src/app.js file.


{% highlight javascript %}


      { route: 'datepicker',        name: 'datepicker',       moduleId: 'samples/datepicker/datepicker',                nav: true, title: 'DatePicker' },


{% endhighlight %}


Execute the following command to run the application

* gulp watch

Execution of above code will render the following output.

![](gettingstarted_images\gettingstarted_img1.png)

## Two way binding

DatePicker value can be bounded as two way binding to synchronize the date value between view and model. 

Check Below code example to know about two way binding


{% highlight html %}


    <input id="datepick" ej-date-picker="e-value.two-way:dateValue;"  ></input>      


{% endhighlight %}


In script section set the variables values,


{% highlight javascript %}


    export class DatePickAPI{

    constructor() {

        this.dateValue = new Date();

    }

    }

{% endhighlight %}


## Configuring the DatePicker properties

DatePicker component have option to render the calendar with min and max date specified. Please refer the below code example to render the DatePicker in component in Aurelia environment with minDate and maxDate 


{% highlight html %}

    <input id="stdate" ej-date-picker="e-value.bind:dtValue1;e-min-date.bind:minDate1;e-max-date.bind:maxDate1;e-width.bind:'100%'"></input>        

{% endhighlight %}

Set the required variable values in corresponding script file like below,

{% highlight javascript %}


    export class DatePickAPI {

    constructor() {

      this.dtValue1 = new Date();

      this.minDate1 = new Date(this.currentYear, this.currentMonth, this.currentDay - 7);

      this.maxDate1 = new Date(this.currentYear, this.currentMonth + 3, this.currentDay);

     }

  }
{% endhighlight %}