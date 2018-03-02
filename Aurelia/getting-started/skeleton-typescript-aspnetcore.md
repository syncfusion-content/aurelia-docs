---
layout: post
title: Integration of aurelia-syncfusion-bridge with Aurelia skeleton-navigation-typescript-aspnetcore
description: How to integrate aurelia-syncfusion-bridge with Aurelia skeleton-navigation-typescript-aspnetcore
platform: Aurelia
control: Getting started
documentation: ug
keywords: Aurelia,Syncfusion,aurelia-syncfusion-bridge,Aurelia skeleton-navigation-typescript-aspnetcore
---
# Integration of aurelia-syncfusion-bridge with Aurelia skeleton-navigation-typescript-aspnetcore

[Aurelia skeleton-navigation-typescript-aspnetcore](https://github.com/aurelia/skeleton-navigation/tree/master/skeleton-typescript-aspnetcore/src/skeleton) is an ASP.NET Core web project pre-configured for building a .NET backend and an Aurelia front-end. It is configured for [TypeScript](https://www.typescriptlang.org/) support. This skeleton uses [JSPM](http://jspm.io/) for package management and [SystemJS](https://github.com/systemjs/systemjs) for loading and bundling.

The [aurelia-syncfusion-bridge](https://github.com/aurelia-ui-toolkits/aurelia-syncfusion-bridge) plugin brings the [Syncfusion Essential Studio for JavaScript Widgets](https://github.com/syncfusion/JavaScript-Widgets) into Aurelia world. So, by configuring aurelia-syncfusion-bridge plugin with Aurelia skeleton-navigation-typescript-aspnetcore, we can use Syncfusion components in Aurelia application.

## Synopsis

* [Prerequisites](#prerequisites)
* [Aurelia skeleton-navigation-typescript-aspnetcore](#aurelia-skeleton-navigation-typescript-aspnetcore)
* [Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge](#installation-of-syncfusion-javascript-widgets-and-aurelia-syncfusion-bridge)
* [Bridge registration](#bridge-registration)
* [Getting started](#getting-started)
* [Building the Application](#building-the-application)
* [Running the Application](#running-the-application)
* [Deploying the Application in production](#deploying-the-application-in-production)

## Prerequisites

* [NodeJS](https://nodejs.org/en/) version >=4.0
* [Gulp](http://gulpjs.com/)
* [JSPM](http://jspm.io/)
* [.NET Core SDK for Windows](https://www.microsoft.com/net/download/core)

In the upcoming sections, we will discuss about the integration of aurelia-syncfusion-bridge with Aurelia skeleton-navigation-typescript-aspnetcore. 

To quick start with Syncfusion Aurelia components, we have already configured aurelia-syncfusion-bridge with Aurelia skeleton-navigation-typescript-aspnetcore. Those who are wish to directly getting started with Syncfusion Aurelia components execute the below commands and navigate to [here](#getting-started).

{% highlight bash %}

> git clone https://github.com/aurelia-ui-toolkits/syncfusion-templates-repository.git
> cd syncfusion-templates-repository/skeleton-typescript-aspnetcore/src/skeleton
> npm install

{% endhighlight %}

## Aurelia skeleton-navigation-typescript-aspnetcore

In this section, we will discuss about the installation of Aurelia project dependencies.

*	Download Aurelia skeleton-navigation from this [link](https://github.com/aurelia/skeleton-navigation/archive/1.1.2.zip) and extract it.
*	From the extracted folder, execute the following commands to install project dependencies.

{% highlight bash %}

> cd skeleton-typescript-aspnetcore/src/skeleton
> npm install

{% endhighlight %}

N> Ensure all the dependencies are installed without any errors.

N> While running the application, we may encounter issues like `error TS***: Duplicate identifier` due to the typescript configuration. To overcome from this error remove the `global dependencies` from `typings.json`.

{% highlight javascript %}

"globalDependencies": {
    "url": "github:aurelia/fetch-client/doc/url.d.ts#bbe0777ef710d889a05759a65fa2c9c3865fc618",
    "whatwg-fetch": "registry:dt/whatwg-fetch#0.0.0+20160524142046"
  }

{% endhighlight %}

## Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge

Install syncfusion-javascript Widgets and aurelia-syncfusion-bridge by executing the following commands.

{% highlight bash %}

> jspm install npm:syncfusion-javascript
> jspm install npm:aurelia-syncfusion-bridge css

{% endhighlight %}

## Bridge registration

In this section, we will discuss about the registration of Syncfusion bridge with Aurelia.

Register the `aurelia-syncfusion-bridge` plugin with Aurelia in our `main.ts` file which is in `src` folder. For example, to register `ejGrid` component, we need to import `syncfusion-javascript/Scripts/ej/web/ej.grid.min` in `main.ts` file.

{% highlight javascript %}

import 'bootstrap';
import { Aurelia } from 'aurelia-framework';
import 'syncfusion-javascript/Scripts/ej/web/ej.grid.min';
export function configure(aurelia: Aurelia) {
  aurelia.use
    .standardConfiguration()
    .developmentLogging()
    //register aurelia-syncfusion-bridge plugin here
    .plugin('aurelia-syncfusion-bridge', (syncfusion) => syncfusion.useAll());
  aurelia.start().then(() => aurelia.setRoot());
}

{% endhighlight %}

N> To use `ejTemplate`, we need to add `syncfusion.ejGrid().ejTemplate();` in our `main.ts` file.

N> To load button component with grid component additionally, we need to import `syncfusion-javascript/Scripts/ej/web/ej.button.min` and add `syncfusion.ejGrid().ejButton();` in our `main.ts` file.

N> To load all Syncfusion components, we need to import `syncfusion-javascript/Scripts/ej/web/ej.web.all.min` and add `syncfusion.useAll()` in our `main.ts` file.

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

* Create `grid.ts` file with the below code snippet inside `src/samples/grid` folder.

{% highlight javascript %}

export class Grid {
  gridData: any;
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

* Now, we are going to configure the navigation for created Grid sample in `src/app.ts` file.

{% highlight javascript %}

import { Router, RouterConfiguration } from 'aurelia-router';
export class App {
  public router: Router;
  public configureRouter(config: RouterConfiguration, router: Router) {
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

## Building the Application

To restore project dependencies and build application, execute the following commands

{% highlight bash %}

> dotnet restore
> gulp build

{% endhighlight %}

## Running the Application

To run the app, execute the following command and browse to [http://localhost:5000](http://localhost:5000) to see the application.

{% highlight bash %}

> dotnet run

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