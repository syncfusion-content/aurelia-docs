---
layout: post
title: getting-started
description: getting started for TimePicker
platform: reactjs
control: TimePicker
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the TimePicker in Aurelia environment with the step-by-step instructions.

## Create DatePicker with Aurelia

You can create an Aurelia application and add necessary scripts and styles with the help of the given Aurelia Getting Started Documentation.
We already configured a template project in GitHub repository syncfusion-template-repository. Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.
	git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository" 

	cd syncfusion-template-repository

	npm install

	jspm install

The below steps describes to create Syncfusion Aurelia TimePicker component.

Create TimePicker folder inside src/samples/ location in sample files folder.

Create html file (here timepicker.html file) inside newly created folder and use the below code example to render the TimePicker component.
		
        {% highlight html %}

        	<input id="button" ej-time-picker/>

{% endhighlight %}

Create script file in Aurelia application to add the EJ component rendering code, here for example we created the  timepicker.js file with the below code snippet inside src/samples/timepicker folder.
 
  {% highlight html %}

     
export class TimePickerApi {
    
}
  

{% endhighlight %}

Now, we need to configure the navigation for created TimePicker sample in src/app.js file.
  
  {% highlight html %}

      { route: 'timepicker',name: 'timepicker',moduleId: 'samples/timepicker/timepicker',nav: true, title: 'TimePicker' },

{% endhighlight %}

Execute the following command to run the application

 gulp watch

Execution of above code will render the following output.

## Two way binding

TimePicker value can be bounded as two way binding to synchronize the date value between view and model. 

Check Below code example to know about two way binding

 {% highlight html %}
            <input id="timepick" ej-time-picker="e-value.two-way:timeValue;"  ></input>   
            
            {% endhighlight %}   

In script section set the variables values,

 {% highlight html %}

export class DatePickAPI{

    constructor() {

      this.timeValue = "10:00 AM ";

    }

}
  {% endhighlight %} 

## Configuring the TimePicker properties

### DisableTimeRanges


This property specifies the list of time range to be disabled in TimePicker control.To know more about TimePicker properties please refer the [API reference](https://help.syncfusion.com/api/js/ejtimepicker) 
               {% highlight html %}

                <input id="stdate" ej-time-picker="e-value.bind:timeValue;e-disable-time-ranges:disabletime;e-width.bind:'100%'"></input>

  {% endhighlight %} 

Set the required variable values in corresponding script file like below,

 {% highlight html %}

export class DatePickAPI {

    constructor() {

      this.timeValue = "12:00 AM";

      this.disabletime =[{ startTime: "3:00 AM", endTime: "6:00 AM" },

                    { startTime: "1:00 PM", endTime: "3:00 PM" },

                    { startTime: "8:00 PM", endTime: "10:00 PM" }]; 
                    
     
     }
}

  {% endhighlight %} 

Execution of above code will render the following output.
