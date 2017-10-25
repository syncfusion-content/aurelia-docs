---
layout: post
title: Integration of aurelia-syncfusion-bridge with Aurelia skeleton-navigation-esnext
description: How to integrate aurelia-syncfusion-bridge with Aurelia skeleton-navigation-esnext
platform: Aurelia
control: Getting started
documentation: ug
keywords: Aurelia,Syncfusion,aurelia-syncfusion-bridge,Aurelia skeleton-navigation-esnext
---
# Integration of aurelia-syncfusion-bridge with Aurelia skeleton-navigation-esnext

[Aurelia skeleton-navigation-esnext](https://github.com/aurelia/skeleton-navigation/tree/master/skeleton-esnext) uses the [Babel](https://babeljs.io/) transpiler so that we can write our application with esnext code which works well with any standard text editor. This skeleton uses [JSPM](http://jspm.io/) for package management and [SystemJS](https://github.com/systemjs/systemjs) for loading and bundling.

The [aurelia-syncfusion-bridge](https://github.com/aurelia-ui-toolkits/aurelia-syncfusion-bridge) plugin brings the [Syncfusion Essential Studio for JavaScript Widgets](https://github.com/syncfusion/JavaScript-Widgets) into Aurelia world. So, by configuring aurelia-syncfusion-bridge plugin with Aurelia skeleton-navigation-esnext, we can use Syncfusion components in Aurelia application.

## Synopsis

*	[Prerequisites](#prerequisites)
*	[Aurelia skeleton-navigation-esnext](#aurelia-skeleton-navigation-esnext)
*	[Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge](#installation-of-syncfusion-javascript-widgets-and-aurelia-syncfusion-bridge)
*	[Bridge registration](#bridge-registration)
*	[Getting started](#getting-started)
*	[Running the Application](#running-the-application)
*   [Deploying the Application in production](#deploying-the-application-in-production)

## Prerequisites

*	[NodeJS](https://nodejs.org/en/) version >=4.0
*	[Gulp](http://gulpjs.com/)
*	[JSPM](http://jspm.io/)

In the upcoming sections, we will discuss about the integration of aurelia-syncfusion-bridge with Aurelia skeleton-navigation-esnext. 

To quick start with Syncfusion Aurelia components, we have already configured aurelia-syncfusion-bridge with Aurelia skeleton-navigation-esnext. Those who are wish to directly getting started with Syncfusion Aurelia components execute the below commands and navigate to [here](#getting-started).

{% highlight bash %}

> git clone https://github.com/aurelia-ui-toolkits/syncfusion-templates-repository.git
> cd syncfusion-templates-repository/skeleton-esnext
> npm install
> jspm install

{% endhighlight %}

## Aurelia skeleton-navigation-esnext

In this section, we will discuss about the installation of Aurelia project dependencies.

*	Download Aurelia skeleton-navigation from this [link](https://github.com/aurelia/skeleton-navigation/archive/1.1.2.zip) and extract it.
*	From the extracted folder, execute the following commands to install project dependencies.

{% highlight bash %}

> cd skeleton-esnext
> npm install
> jspm install

{% endhighlight %}

N> Ensure all the dependencies are installed without any errors.

## Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge

Install syncfusion-javascript Widgets and aurelia-syncfusion-bridge by executing the following commands.

{% highlight bash %}

> jspm install npm:syncfusion-javascript
> jspm install npm:aurelia-syncfusion-bridge css

{% endhighlight %}

## Bridge registration

In this section, we will discuss about the registration of Syncfusion bridge with Aurelia.

Register the `aurelia-syncfusion-bridge` plugin with Aurelia in our `main.js` file which is in `src` folder. For example, to register `ejGrid` component, we need to import `syncfusion-javascript/Scripts/ej/web/ej.grid.min` in `main.js` file.

{% highlight javascript %}

import 'bootstrap';
import 'syncfusion-javascript/Scripts/ej/web/ej.grid.min';
export function configure(aurelia) {
    aurelia.use
        .standardConfiguration()
        .developmentLogging()
        //register aurelia-syncfusion-bridge plugin here
        .plugin('aurelia-syncfusion-bridge', (syncfusion) => syncfusion.ejGrid());
    aurelia.start().then(() => aurelia.setRoot());
}

{% endhighlight %}

N> To use `ejTemplate`, we need to add `syncfusion.ejGrid().ejTemplate();` in our `main.js` file.

N> To load button component with grid component additionally, we need to import `syncfusion-javascript/Scripts/ej/web/ej.button.min` and add `syncfusion.ejGrid().ejButton();` in our `main.js` file.

N> To load all Syncfusion components, we need to import `syncfusion-javascript/Scripts/ej/web/ej.web.all.min` and add `syncfusion.useAll()` in our `main.js` file.

## Getting started

In this section, we will discuss about the creation of Aurelia Syncfusion Grid component.

The below step describes to create Syncfusion Aurelia Grid component.

* Create `grid.html` file inside `src/samples/grid` folder structure and use the below code example to render the Grid component.

{% highlight html %}

<template>
    <div>
        <ej-grid e-data-source.two-way="gridData" e-allow-paging=true e-allow-sorting=true e-on-record-click.delegate="recordClick($event.detail)">
            <ej-column e-field="OrderID" e-header-text="Order ID" e-text-align="right"></ej-column>
            <ej-column e-field="CustomerID" e-header-text="Customer ID"></ej-column>
            <ej-column e-field="EmployeeID" e-header-text="Employee ID" e-text-align="right"></ej-column>
            <ej-column e-field="Freight" e-header-text="Freight" e-format="{0:C}" e-text-align="right"></ej-column>
            <ej-column e-field="OrderDate" e-header-text="Order Date" e-format="{0:MM/dd/yyyy}" e-text-align="right"></ej-column>
        </ej-grid>
    </div>
</template>

{% endhighlight %}

* Create `grid.js` file with the below code snippet inside `src/samples/grid` folder.

{% highlight javascript %}

export class Grid {
    constructor() {
        this.gridData = [{
            OrderID: 10248, CustomerID: 'VINET', EmployeeID: 5,
            OrderDate: new Date(8364186e5), Freight: 32.38
        },
        {
            OrderID: 10249, CustomerID: 'TOMSP', EmployeeID: 6,
            OrderDate: new Date(836505e6), Freight: 11.61
        },
        {
            OrderID: 10250, CustomerID: 'HANAR', EmployeeID: 4,
            OrderDate: new Date(8367642e5), Freight: 65.83
        },
        {
            OrderID: 10251, CustomerID: 'VICTE', EmployeeID: 3,
            OrderDate: new Date(8367642e5), Freight: 41.34
        },
        {
            OrderID: 10252, CustomerID: 'SUPRD', EmployeeID: 4,
            OrderDate: new Date(8368506e5), Freight: 51.3
        }];
    }

    recordClick(e) {
        //handle event here
    }
}

{% endhighlight %}

* Add Syncfusion theme in our project by adding the below code snippet in `src/app.html` file.

{% highlight html %}

<template>
    <require from="nav-bar.html"></require>
    <require from="bootstrap/css/bootstrap.css"></require>
    <!--Add Syncfusion JavaScript themes here-->
    <require from="syncfusion-javascript/Content/ej/web/ej.widgets.core.bootstrap.min.css"></require>
    <require from="syncfusion-javascript/Content/ej/web/bootstrap-theme/ej.theme.min.css"></require>
    <require from="syncfusion-javascript/Content/ej/web/responsive-css/ej.responsive.css"></require>
    <nav-bar router.bind="router"></nav-bar>
    <div class="page-host">
        <router-view></router-view>
    </div>
</template>

{% endhighlight %}

* Now, we are going to configure the navigation for created Grid sample in `src/app.js` file.

{% highlight javascript %}

export class App {
  configureRouter(config, router) {
    config.title = 'Aurelia';
    config.map([
      { route: ['', 'welcome'], name: 'welcome',      moduleId: 'welcome',           nav: true, title: 'Welcome' },
      { route: 'users',         name: 'users',        moduleId: 'users',             nav: true, title: 'Github Users' },
      { route: 'child-router',  name: 'child-router', moduleId: 'child-router',      nav: true, title: 'Child Router' },
      //Add the router configuration for Grid sample here
      { route: 'grid',          name: 'grid',         moduleId: 'samples/grid/grid', nav: true, title: 'Grid' }
    ]);
    this.router = router;
  }
}

{% endhighlight %}

## Running the Application

To run the app, execute the following command and browse to [http://localhost:9000](http://localhost:9000) to see the application.

{% highlight bash %}

> gulp watch

{% endhighlight %}

## Deploying the Application in production

To deploy the application in production, we need to configure `build/bundles.js` and `build/export.js`.

In `build/bundles.js`, we need to include both `aurelia-syncfusion-bridge` and `syncfusion-javascript` in `bundles`.

To bundle `ejGrid` component, we need to include `grid resources` in `build/bundles.js` as like the below code section.

{% highlight javascript %}

"dist/aurelia-syncfusion-bridge": {
      "includes": [
        "aurelia-syncfusion-bridge",
        "aurelia-syncfusion-bridge/grid/*.js",
        "text"
      ],
      "options": {
        "inject": true,
        "minify": true,
        "depCache": false,
        "rev": false
      }
},
"dist/syncfusion-javascript": {
      "includes": [
        "syncfusion-javascript/Scripts/ej/web/ej.grid.min.js"
      ],
      "options": {
        "inject": true,
        "minify": true,
        "depCache": false,
        "rev": false
      }
}

{% endhighlight %}

N> To bundle `all Syncfusion components`, add `aurelia-syncfusion-bridge/**/*.js` to `dist/aurelia-syncfusion-bridge` and `syncfusion-javascript/Scripts/ej/web/ej.web.all.min.js` to `dist/syncfusion-javascript` as like the below code snippet.

{% highlight javascript %}

"dist/aurelia-syncfusion-bridge": {
      "includes": [
        "aurelia-syncfusion-bridge",
        "aurelia-syncfusion-bridge/**/*.js",
        "text"
      ]
      ......
      ......
},
"dist/syncfusion-javascript": {
      "includes": [
        "syncfusion-javascript/Scripts/ej/web/ej.web.all.min.js"
      ]
      ......
      ......
}

{% endhighlight %}

N> While running the application in production environment, we may encounter issues like `Failed loading required CSS file`. To overcome this error, add `text` plugin to `dist/aurelia-syncfusion-bridge` which will load all text resources.

In `build/export.js`, we need to include `Syncfusion themes` in `normalize` array.

{% highlight javascript %}

'normalize': [
    // include Syncfusion theme
    [
      'syncfusion-javascript', [
        '/Content/ej/web/ej.widgets.core.bootstrap.min.css',
        '/Content/ej/web/bootstrap-theme/ej.theme.min.css',
        '/Content/ej/web/common-images/**',
        '/Content/ej/web/bootstrap-theme/images/**',
        '/Content/ej/web/responsive-css/ej.responsive.css'
      ]
    ],
    [
      // include font-awesome.css and its fonts files
      'font-awesome', [
        '/css/font-awesome.min.css',
        '/fonts/*'
      ]
    ]
]

{% endhighlight %}

Then run the below command to export our application in production.

{% highlight bash %}

> gulp export

{% endhighlight %}

The app will be exported into `export` directory preserving the directory structure.