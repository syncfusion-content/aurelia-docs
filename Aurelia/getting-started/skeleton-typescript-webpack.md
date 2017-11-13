---
layout: post
title: Integration of aurelia-syncfusion-bridge with Aurelia skeleton-navigation-typescript-webpack
description: How to integrate aurelia-syncfusion-bridge with Aurelia skeleton-navigation-typescript-webpack
platform: Aurelia
control: Getting started
documentation: ug
keywords: Aurelia,Syncfusion,aurelia-syncfusion-bridge,Aurelia skeleton-navigation-typescript-webpack
---
# Integration of aurelia-syncfusion-bridge with Aurelia skeleton-navigation-typescript-webpack

[Aurelia skeleton-navigation-typescript-webpack](https://github.com/aurelia/skeleton-navigation/tree/master/skeleton-typescript-webpack) uses the [TypeScript](https://www.typescriptlang.org/) transpiler so that we can write our application with TypeScript code which works well with any standard text editor. This skeleton uses [NPM](https://www.npmjs.com/) for package management and [Webpack](https://webpack.github.io/) for bundling.

The [aurelia-syncfusion-bridge](https://github.com/aurelia-ui-toolkits/aurelia-syncfusion-bridge) plugin brings the [Syncfusion Essential Studio for JavaScript Widgets](https://github.com/syncfusion/JavaScript-Widgets) into Aurelia world. So, by configuring aurelia-syncfusion-bridge plugin with Aurelia skeleton-navigation-typescript-webpack, we can use Syncfusion components in Aurelia application.

## Synopsis

* [Prerequisites](#prerequisites)
* [Aurelia skeleton-navigation-typescript-webpack](#aurelia-skeleton-navigation-typescript-webpack)
* [Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge](#installation-of-syncfusion-javascript-widgets-and-aurelia-syncfusion-bridge)
* [Webpack configuration](#webpack-configuration)
* [Bridge registration](#bridge-registration)
* [Getting started](#getting-started)
* [Running the Application](#running-the-application)

## Prerequisites

*	[NodeJS](https://nodejs.org/en/) version >=4.0

In the upcoming sections, we will discuss about the integration of aurelia-syncfusion-bridge with Aurelia skeleton-navigation-typescript-webpack. 

To quick start with Syncfusion Aurelia components, we have already configured aurelia-syncfusion-bridge with Aurelia skeleton-navigation-typescript-webpack. Those who are wish to directly getting started with Syncfusion Aurelia components execute the below commands and navigate to [here](#getting-started).

{% highlight bash %}

> git clone https://github.com/aurelia-ui-toolkits/syncfusion-templates-repository.git
> cd syncfusion-templates-repository/skeleton-typescript-webpack
> npm install

{% endhighlight %}

## Aurelia skeleton-navigation-typescript-webpack

In this section, we will discuss about the installation of Aurelia project dependencies.

* Download Aurelia skeleton-navigation from this [link](https://github.com/aurelia/skeleton-navigation/archive/1.1.2.zip) and extract it.
* From the extracted folder, execute the following commands to install project dependencies.

{% highlight bash %}

> cd skeleton-typescript-webpack
> npm install

{% endhighlight %}

N> Ensure all the dependencies are installed without any errors.

N> While running the application, we may encounter issues like `error TS***: Duplicate identifier` due to the typescript configuration. To overcome from this error remove the following `devDependencies` from `package.json`.

{% highlight javascript %}

"@types/whatwg-fetch": "^0.0.32"

{% endhighlight %}

And, remove the following reference path from `custom_typings/fetch.d.ts` file

{% highlight javascript %}

/// <reference path="../node_modules/@types/whatwg-fetch/index.d.ts" />

{% endhighlight %}

## Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge

Install syncfusion-javascript Widgets and aurelia-syncfusion-bridge by executing the following commands.

{% highlight bash %}

> npm install syncfusion-javascript --save
> npm install aurelia-syncfusion-bridge --save

{% endhighlight %}

## Webpack configuration

In this section, we will discuss about the configuration of webpack to seamlessly work with aurelia-syncfusion-bridge.

* In `webpack.config.ts`, add aurelia-syncfusion-bridge to `generateConfig.entry` section like the below code section.

{% highlight javascript %}

entry: {
      'app': ['./src/main' /* this is filled by the aurelia-webpack-plugin */],
      'aurelia-bootstrap': coreBundles.bootstrap,
      'aurelia': coreBundles.aurelia.filter(pkg => coreBundles.bootstrap.indexOf(pkg) === -1),
      'aurelia-syncfusion-bridge': ['aurelia-syncfusion-bridge']
    }

{% endhighlight %}

* In `package.json`, we need to add the path for Syncfusion Aurelia components in `aurelia.build.resources` to load the aurelia-syncfusion-bridge component source into webpack. For example, to render ejGrid component, we need to add the following path.

{% highlight javascript %}

"aurelia": {
  "build": {
    "resources": [
      "aurelia-syncfusion-bridge/grid/grid",
      "aurelia-syncfusion-bridge/grid/column"
    ]
  }
}

{% endhighlight %}

N> To use `ejTemplate`, add `aurelia-syncfusion-bridge/common/template` to `aurelia.build.resources` in `package.json` and include the ejTemplate() in `main.ts` file.

N> To use any other Syncfusion components in Aurelia application, we need to add specific Syncfusion Aurelia component path to `aurelia.build.resources` in `package.json` file. For example, To use button component, add `aurelia-syncfusion-bridge/button/button` to `aurelia.build.resources` in `package.json`.

## Bridge registration

In this section, we will discuss about the registration of Syncfusion bridge with Aurelia.

Register the `aurelia-syncfusion-bridge` plugin with Aurelia in our `main.ts` file which is in `src` folder. For example, to register `ejGrid` component, we need to import `syncfusion-javascript/Scripts/ej/web/ej.grid.min` in `main.ts` file.

{% highlight javascript %}

import { Aurelia } from 'aurelia-framework';
import '../styles/styles.css';
import 'font-awesome/css/font-awesome.css';
import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap';
import * as Bluebird from 'bluebird';
import 'syncfusion-javascript/Scripts/ej/web/ej.grid.min';
Bluebird.config({ warnings: false });
export async function configure(aurelia: Aurelia) {
  aurelia.use
    .standardConfiguration()
    .developmentLogging()
    //register aurelia-syncfusion-bridge plugin here
    .plugin('aurelia-syncfusion-bridge', (syncfusion) => syncfusion.ejGrid());
  await aurelia.start();
  aurelia.setRoot('app');
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

* Add Syncfusion themes in our project by adding the below code snippet in `src/app.html` file.

{% highlight html %}

<template>
    <require from="./nav-bar.html"></require>
    <!--Add Syncfusion JavaScript themes here-->
    <require from="../node_modules/syncfusion-javascript/Content/ej/web/bootstrap-theme/ej.web.all.min.css"></require>
    <require from="../node_modules/syncfusion-javascript/Content/ej/web/responsive-css/ej.responsive.css"></require>
    <nav-bar router.bind="router"></nav-bar>
    <div class="page-host">
        <router-view></router-view>
    </div>
</template>

{% endhighlight %}

* Now, we are going to configure the navigation for created Grid sample in `src/app.ts` file.

{% highlight javascript %}

import {Aurelia} from 'aurelia-framework';
import {Router, RouterConfiguration} from 'aurelia-router';
export class App {
  router: Router;
  configureRouter(config: RouterConfiguration, router: Router) {
    config.title = 'Aurelia';
    config.map([
      { route: ['', 'welcome'], name: 'welcome',      moduleId: './welcome',         nav: true, title: 'Welcome' },
      { route: 'users',         name: 'users',        moduleId: './users',           nav: true, title: 'Github Users' },
      { route: 'child-router',  name: 'child-router', moduleId: './child-router',    nav: true, title: 'Child Router' },
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

> npm start

{% endhighlight %}

N> We need to execute the below command to overcome the issue `You may need an appropriate loader to handle this file type(cur)`. Since, the Syncfusion JavaScript component’s theme uses `.cur` file.

{% highlight bash %}

> npm install @easy-webpack/config-fonts-and-images@^3.1.0 --save-dev

{% endhighlight %}