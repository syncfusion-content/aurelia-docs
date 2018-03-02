---
title: Getting started with Schedule component
description: Rendering a basic Scheduler
platform: Aurelia
control: schedule
documentation: ug
keywords: ejschedule, schedule, schedule widget, js schedule
---

# Getting Started

A separate wrapper has been created for all the Syncfusion widgets in order to bridge the Aurelia framework and the Syncfusion components. To know more about the Aurelia interface with Syncfusion widgets, refer the general content from [here](/aurelia/overview).

To start using Scheduler in Aurelia Framework, we already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository) to quick start with it. Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

> git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
> cd syncfusion-template-repository
> npm install
> jspm install

{% endhighlight %}

## Adding Scheduler HTML File

The below steps describes the way to create Syncfusion Aurelia Schedule component.

Create `schedule` folder inside `src/samples/` location.

Create `schedule.html` file inside `src/samples/schedule` folder and use the below code example to render the Schedule component.

{% highlight html %}

<template>    
    <div>
        <ej-schedule id="Schedule1" e-width="100%" e-height="575px" e-appointment-settings.bind="AppointmentList" e-current-date="04/03/2016">
        </ej-schedule>
    </div>
</template>

{% endhighlight %}

Create `schedule.js` file with the below code snippet inside `src/samples/schedule` folder.

{% highlight javascript %}

export class DefaultSchedule {
    constructor() {
      this.AppointmentList = {
        // Schedule appointment dataSource
        dataSource: [
          {
            Id: 100,
            Subject: 'Bering Sea Gold',
            StartTime: '2016/4/5 10:00:00',
            EndTime: '2016/4/5 11:00:00',
            AllDay: false,
            Recurrence: false
          }, {
            Id: 101,
            Subject: 'Daily Planet',
            StartTime: '2016/4/3 01:00:00',
            EndTime: '2016/4/3 02:00:00',
            AllDay: false,
            Recurrence: false
          }, {
            Id: 104,
            Subject: 'Close Encounters',
            StartTime: '2016/3/30 14:00:00',
            EndTime: '2016/3/30 15:30:00',
            AllDay: false,
            Recurrence: true,
            RecurrenceRule: 'FREQ=WEEKLY;BYDAY=MO,TH;INTERVAL=1;COUNT=5'
          }],
        // Schedule dataSource field mapping
        id: 'Id',
        subject: 'Subject',
        startTime: 'StartTime',
        endTime: 'EndTime',
        description: 'Description',
        allDay: 'AllDay',
        recurrence: 'Recurrence',
        recurrenceRule: 'RecurrenceRule'
      };
    }
}

{% endhighlight %}


![](Getting-Started_images/Getting-Started_img1.png)

## Configure the Router

Now, Configure the sample navigation for the created Schedule sample in `src/app.js` file.

{% highlight javascript %}

export class App {
 configureRouter(config, router) {
  config.title = 'Aurelia Syncfusion';
  config.map([
   { route: ['', 'welcome'], name: 'welcome', moduleId: 'welcome',
                nav: true, title: 'Welcome' },
   { route: 'child-router',  name: 'child-router', moduleId: 'child-router',
                nav: true, title: 'Child Router' },
   { route: 'button', name: 'button', moduleId: 'samples/button/button',
                nav: true, title: 'Button' },
   { route: 'schedule', name: 'schedule', moduleId: 'samples/schedule/schedule',
                nav: true, title: 'Schedule' }
 ]);
 this.router = router;
 }
}

{% endhighlight %}

## Run the Application

To run the application, execute the following command.

{% highlight javascript %}

* gulp watch

{% endhighlight %}

Browse through [`http://localhost:9000`](http://localhost:9000)  to see the application. You can also make changes in the code found under the `src` folder, so that the browser will auto-refresh itself while you save the modified files.
