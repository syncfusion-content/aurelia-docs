---
layout: post
title: Integration of aurelia-syncfusion-bridge with latest Aurelia skeleton-navigation-esnext-webpack
description: How to integrate aurelia-syncfusion-bridge with latest Aurelia skeleton-navigation-esnext-webpack
platform: Aurelia
control: Getting started
documentation: ug
keywords: Aurelia,Syncfusion,aurelia-syncfusion-bridge,Aurelia skeleton-navigation-esnext-webpack
---
# Integration of aurelia-syncfusion-bridge with latest Aurelia skeleton-navigation-esnext-webpack

[Aurelia skeleton-navigation-esnext-webpack](https://github.com/aurelia/skeleton-navigation/tree/master/skeleton-esnext-webpack) uses the [Babel](https://babeljs.io/) transpiler so that we can write our application with esnext code which works well with any standard text editor. This skeleton uses [NPM](https://www.npmjs.com/) for package management and [Webpack](https://webpack.github.io/) for bundling.

The [aurelia-syncfusion-bridge](https://github.com/aurelia-ui-toolkits/aurelia-syncfusion-bridge) plugin brings the [Syncfusion Essential Studio for JavaScript Widgets](https://github.com/syncfusion/JavaScript-Widgets) into Aurelia world. So, by configuring aurelia-syncfusion-bridge plugin with latest Aurelia skeleton-navigation-esnext-webpack, we can use Syncfusion components in Aurelia application.

## Synopsis

* [Prerequisites](#prerequisites)
* [Aurelia skeleton-navigation-esnext-webpack](#aurelia-skeleton-navigation-esnext-webpack)
* [Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge](#installation-of-syncfusion-javascript-widgets-and-aurelia-syncfusion-bridge)
* [Webpack configuration](#webpack-configuration)
* [Bridge registration](#bridge-registration)
* [Getting started](#getting-started)
* [Running the Application](#running-the-application)

## Prerequisites

*	[NodeJS](https://nodejs.org/en/) version >=6.0

## Aurelia skeleton-navigation-esnext-webpack

In this section, we will discuss about the installation of Aurelia project dependencies.

*   Clone Aurelia skeleton-navigation from master branch and install project dependencies by executing the following commands.

{% highlight bash %}

> git clone https://github.com/aurelia/skeleton-navigation.git
> cd skeleton-navigation/skeleton-esnext-webpack
> npm install

{% endhighlight %}

N> Ensure all the dependencies are installed without any errors.

## Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge

Install syncfusion-javascript Widgets and aurelia-syncfusion-bridge by executing the following commands.

{% highlight bash %}

> npm install syncfusion-javascript --save
> npm install aurelia-syncfusion-bridge --save

{% endhighlight %}

## Webpack configuration

In this section, we will discuss about the configuration of webpack to seamlessly work with aurelia-syncfusion-bridge.

*   In `webpack.config.js` file, add `aurelia-syncfusion-bridge` to `entry.vendor` like the below code section.

{% highlight javascript %}

entry: {
    app: ['aurelia-bootstrapper'],
    vendor: ['bluebird', 'jquery', 'bootstrap', 'aurelia-syncfusion-bridge'],
  }

{% endhighlight %}

## Bridge registration

In this section, we will discuss about the registration of Syncfusion bridge with Aurelia.

Register the `aurelia-syncfusion-bridge` plugin with Aurelia in our `main.js` file which is in `src` folder. For example, to register `ejGrid` component, we need to import `syncfusion-javascript/Scripts/ej/web/ej.grid.min` in `main.js` file.

{% highlight javascript %}

import '../static/styles.css';
import 'font-awesome/css/font-awesome.css';
import 'bootstrap/dist/css/bootstrap.css';
import 'babel-polyfill';
import * as Bluebird from 'bluebird';
import 'syncfusion-javascript/Scripts/ej/web/ej.grid.min';
Bluebird.config({ warnings: { wForgottenReturn: false } });

export async function configure(aurelia) {
    aurelia.use
        .standardConfiguration()
        .developmentLogging()
        //register aurelia-syncfusion-bridge plugin here
        .plugin(PLATFORM.moduleName('aurelia-syncfusion-bridge'), (syncfusion) => syncfusion.ejGrid());
    await aurelia.start();
    await aurelia.setRoot(PLATFORM.moduleName('app'));
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

* Add Syncfusion themes in our project by adding the below code snippet in `src/app.html` file.

{% highlight html %}

<template>
    <require from="./nav-bar.html"></require>
    <!--Add Syncfusion JavaScript themes here-->
    <require from="syncfusion-javascript/Content/ej/web/bootstrap-theme/ej.web.all.min.css"></require>
    <require from="syncfusion-javascript/Content/ej/web/responsive-css/ej.responsive.css"></require>
    <nav-bar router.bind="router"></nav-bar>

    <div class="page-host">
        <router-view></router-view>
    </div>
</template>

{% endhighlight %}

* Now, we are going to configure the navigation for created Grid sample in `src/app.js` file.

{% highlight javascript %}

import {PLATFORM} from 'aurelia-pal';

export class App {
  configureRouter(config, router) {
    config.title = 'Aurelia';
    config.map([
      { route: ['', 'welcome'], name: 'welcome',      moduleId: PLATFORM.moduleName('./welcome'),           nav: true, title: 'Welcome' },
      { route: 'users',         name: 'users',        moduleId: PLATFORM.moduleName('./users'),             nav: true, title: 'Github Users' },
      { route: 'child-router',  name: 'child-router', moduleId: PLATFORM.moduleName('./child-router'),      nav: true, title: 'Child Router' },
      { route: 'grid',          name: 'grid',         moduleId: PLATFORM.moduleName('./samples/grid/grid'), nav: true, title: 'grid' }
    ]);

    this.router = router;
  }
}

{% endhighlight %}

## Running the Application

To run the app, execute the following command and browse to [http://localhost:8080](http://localhost:8080) to see the application.

{% highlight bash %}

> npm start

{% endhighlight %}