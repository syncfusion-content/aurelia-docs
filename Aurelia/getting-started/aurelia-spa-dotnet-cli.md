---
layout: post
title: Integration of aurelia-syncfusion-bridge with Aurelia application on ASP.NET Core SPA
description: How to integrate aurelia-syncfusion-bridge with Aurelia application on ASP.NET Core SPA
platform: Aurelia
control: Getting started
documentation: ug
keywords: Aurelia,Syncfusion,aurelia-syncfusion-bridge,ASP.NET Core SPA
---
# Integration of aurelia-syncfusion-bridge with Aurelia application on ASP.NET Core SPA

An ASP.NET Core web application with an Aurelia frontend is configured for [TypeScript](https://www.typescriptlang.org/) support.This application uses [NPM](https://www.npmjs.com/) for package management and [Webpack](https://webpack.github.io/) for bundling.

The [aurelia-syncfusion-bridge](https://github.com/aurelia-ui-toolkits/aurelia-syncfusion-bridge) plugin brings the [Syncfusion Essential Studio for JavaScript Widgets](https://github.com/syncfusion/JavaScript-Widgets) into Aurelia world. So, by configuring aurelia-syncfusion-bridge plugin with Aurelia application on ASP.NET Core SPA, we can use Syncfusion components in Aurelia application.

## Synopsis

* [Setting up machine Environment](#setting-up-machine-environment)
* [Creating an Aurelia application on ASP.NET Core SPA via command line](#creating-an-aurelia-application-on-aspnet-core-spa-via-command-line)
* [Restoring the project dependencies](#restoring-the-project-dependencies)
* [Installation of syncfusion-javascript widgets and aurelia-syncfusion-bridge](#installation-of-syncfusion-javascript-widgets-and-aurelia-syncfusion-bridge)
* [Configuring our Environment](#configuring-our-environment)
* [Webpack configuration](#webpack-configuration)
* [Bridge registration](#bridge-registration)
* [Getting started](#getting-started)
* [Running the Application](#running-the-application)
* [Running the project using Visual Studio 2017](#running-the-project-using-visual-studio-2017)

## Setting up machine Environment

The following steps must be performed once on the target machine.

* Install Node.js from [https://nodejs.org](https://nodejs.org).
* Install the .NET CLI from [https://www.microsoft.com/net/core](https://www.microsoft.com/net/core).
* Install the ASP.NET SPA Templates by executing following command.

{% highlight bash %}

> dotnet new --install "Microsoft.AspNetCore.SpaTemplates::*"

{% endhighlight %}

## Creating an Aurelia application on ASP.NET Core SPA via command line

Create a project folder, from that folder execute the following command to create a new Aurelia application.

{% highlight bash %}

> dotnet new aurelia

{% endhighlight %}

## Restoring the project dependencies

To restore project dependencies, execute the following commands at root of our application.

{% highlight bash %}

> dotnet restore
> npm install

{% endhighlight %}

## Installation of syncfusion-javascript widgets and aurelia-syncfusion-bridge

Install [syncfusion-javascript widgets](https://www.npmjs.com/package/syncfusion-javascript) and [aurelia-syncfusion-bridge](https://www.npmjs.com/package/aurelia-syncfusion-bridge) by executing the following commands.

{% highlight bash %}

> npm install syncfusion-javascript --save
> npm install aurelia-syncfusion-bridge --save

{% endhighlight %}

* We are working with `typescript`, since, we need to install the typings dependencies `jquery` and `ej.web.all`. We may need of accessing the `ej` object for Syncfusion widget's properties in Aurelia application, which is defined in `ej.web.all` typings file.
E.g.  `ej.TextAlign.right`

{% highlight javascript %}

npm install --save-dev @types/jquery
npm install --save-dev @types/ej.web.all

{% endhighlight %}

* And also include the typings `jquery` and `ej.web.all` in `tsconfig.json` file. 

{% highlight javascript %}

{
  "compilerOptions": {
    "module": "es2015",
    "moduleResolution": "node",
    "target": "es5",
    "sourceMap": true,
    "experimentalDecorators": true,
    "emitDecoratorMetadata": true,
    "skipDefaultLibCheck": true,
    "strict": true,
    "lib": [ "es2015", "dom" ],
    "types": [ "webpack-env", "jquery", "ej.web.all" ]
  },
  "exclude": [ "bin", "node_modules" ],
  "atom": { "rewriteTsconfig": false }
}

{% endhighlight %}

## Configuring our Environment

Before running the application, we want to configure our environment so that the ASP.NET tooling runs in development mode.

* Set the environment variable to development mode by executing the following command.

{% highlight bash %}

> setx ASPNETCORE_ENVIRONMENT "Development"

{% endhighlight %}

N> After executing the above command, restart the command prompt to make the change take effect.

## Webpack configuration

In this section, we will discuss about the configuration of webpack to seamlessly work with aurelia-syncfusion-bridge.

* In `webpack.config.js` file, add the following loader configuration in `module.rules` to support various Syncfusion file formats.

{% highlight javascript %}

module: {
            rules: [
                { test: /\.ts$/i, include: /ClientApp/, use: 'ts-loader?silent=true' },
                { test: /\.html$/i, use: 'html-loader' },
                { test: /\.css$/i, use: isDevBuild ? 'css-loader' : 'css-loader?minimize' },
                { test: /\.(png|jpg|jpeg|gif|cur|svg)$/, use: 'url-loader?limit=25000' },
                { test: /\.woff2(\?v=[0-9]\.[0-9]\.[0-9])?$/, loader: 'url-loader', query: { limit: 10000, mimetype: 'application/font-woff2' } },
                { test: /\.woff(\?v=[0-9]\.[0-9]\.[0-9])?$/, loader: 'url-loader', query: { limit: 10000, mimetype: 'application/font-woff' } },
                { test: /\.(ttf|eot|svg|otf)(\?v=[0-9]\.[0-9]\.[0-9])?$/, loader: 'file-loader' },

            ]
        }

{% endhighlight %}

## Bridge registration

In this section, we will discuss about the registration of Syncfusion bridge with Aurelia.

* In `boot.ts` file, Export `jquery` to `window` object and register the `aurelia-syncfusion-bridge` plugin with Aurelia which is in `ClientApp` folder.

{% highlight javascript %}

import 'isomorphic-fetch';
import { Aurelia, PLATFORM } from 'aurelia-framework';
import { HttpClient } from 'aurelia-fetch-client';
import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap';
declare const IS_DEV_BUILD: boolean; // The value is supplied by Webpack during the build

//Export jQuery to window object
import * as $ from 'jquery';
let winObj:any = <any>window;
winObj['jQuery'] = $;
winObj['$'] = $;

export function configure(aurelia: Aurelia) {
    aurelia.use.standardConfiguration()
        //register aurelia-syncfusion-bridge plugin here
    .plugin(PLATFORM.moduleName('aurelia-syncfusion-bridge'), (syncfusion: any) => syncfusion.ejGrid());

    if (IS_DEV_BUILD) {
        aurelia.use.developmentLogging();
    }

    new HttpClient().configure(config => {
        const baseUrl = document.getElementsByTagName('base')[0].href;
        config.withBaseUrl(baseUrl);
    });

    aurelia.start().then(() => aurelia.setRoot(PLATFORM.moduleName('app/components/app/app')));
}

{% endhighlight %}

N> To use `ejTemplate`, we need to add `syncfusion.ejGrid().ejTemplate();` in our `boot.ts` file.

N> To load button component with grid component additionally, we need to add `syncfusion.ejGrid().ejButton();` in our `boot.ts` file.

N> To load all Syncfusion components, we need to add `syncfusion.useAll()` in our `boot.ts` file.

* To load `ejGrid` component, we need to import `syncfusion-javascript/Scripts/ej/web/ej.grid.min` in `app.ts` file which is in `ClientApp/app/components/app` folder.


{% highlight javascript %}

import { Aurelia, PLATFORM } from 'aurelia-framework';
import { Router, RouterConfiguration } from 'aurelia-router';
import 'syncfusion-javascript/Scripts/ej/web/ej.grid.min';

export class App {
    router: Router;

    configureRouter(config: RouterConfiguration, router: Router) {
        config.title = 'Aurelia';
        config.map([{
            route: [ '', 'home' ],
            name: 'home',
            settings: { icon: 'home' },
            moduleId: PLATFORM.moduleName('../home/home'),
            nav: true,
            title: 'Home'
        }, {
            route: 'counter',
            name: 'counter',
            settings: { icon: 'education' },
            moduleId: PLATFORM.moduleName('../counter/counter'),
            nav: true,
            title: 'Counter'
        }, {
            route: 'fetch-data',
            name: 'fetchdata',
            settings: { icon: 'th-list' },
            moduleId: PLATFORM.moduleName('../fetchdata/fetchdata'),
            nav: true,
            title: 'Fetch data'
        },{
            route: 'grid',
            name: 'grid',
            settings: { icon: 'th' },
            moduleId: PLATFORM.moduleName('../samples/grid/grid'),
            nav: true,
            title: 'Grid'
        }]);

        this.router = router;
    }
}

{% endhighlight %}

N> To load button component, we need to import `syncfusion-javascript/Scripts/ej/web/ej.button.min` in our `app.ts` file.

N> To load all Syncfusion components, we need to import `syncfusion-javascript/Scripts/ej/web/ej.web.all.min` in our `app.ts` file.

## Getting started

In this section, we will discuss about the creation of Aurelia Syncfusion Grid component.

The below step describes to create Syncfusion Aurelia Grid component.

* Create `grid.html` file inside `ClientApp/app/components/samples/grid` folder structure and use the below code example to render the Grid component.

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

* Create `grid.ts` file with the below code snippet inside `ClientApp/app/components/samples/grid` folder.

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

* Add Syncfusion theme in our project by adding the below code snippet in `ClientApp/app/components/app/app.html` file.

{% highlight html %}

<template>
    <require from="../navmenu/navmenu.html"></require>
    <require from="./app.css"></require>
    <!--Add Syncfusion JavaScript themes here-->
    <require from="syncfusion-javascript/Content/ej/web/bootstrap-theme/ej.web.all.min.css"></require>
    <require from="syncfusion-javascript/Content/ej/web/responsive-css/ej.responsive.css"></require>

    <div class="container-fluid">
        <div class="row">
            <div class="col-sm-3">
                <navmenu router.bind="router"></navmenu>
            </div>
            <div class="col-sm-9 body-content">
                <router-view></router-view>
            </div>
        </div>
    </div>
</template>

{% endhighlight %}

* Now, we are going to configure the navigation for created Grid sample in `ClientApp/app/components/app/app.ts` file.

{% highlight javascript %}

import { Aurelia, PLATFORM } from 'aurelia-framework';
import { Router, RouterConfiguration } from 'aurelia-router';

export class App {
    router: Router;

    configureRouter(config: RouterConfiguration, router: Router) {
        config.title = 'Aurelia';
        config.map([{
            route: ['', 'home'],
            name: 'home',
            settings: { icon: 'home' },
            moduleId: PLATFORM.moduleName('../home/home'),
            nav: true,
            title: 'Home'
        }, {
            route: 'counter',
            name: 'counter',
            settings: { icon: 'education' },
            moduleId: PLATFORM.moduleName('../counter/counter'),
            nav: true,
            title: 'Counter'
        }, {
            route: 'fetch-data',
            name: 'fetchdata',
            settings: { icon: 'th-list' },
            moduleId: PLATFORM.moduleName('../fetchdata/fetchdata'),
            nav: true,
            title: 'Fetch data'
        }, {
            route: 'grid',
            name: 'grid',
            settings: { icon: 'th' },
            moduleId: PLATFORM.moduleName('../samples/grid/grid'),
            nav: true,
            title: 'Grid'
        }
        ]);

        this.router = router;
    }
}

{% endhighlight %}

## Running the Application

To run the app, execute the following command and browse to [http://localhost:5000](http://localhost:5000) to see the application.

{% highlight bash %}

> dotnet run

{% endhighlight %}

## Running the project using Visual Studio 2017

Open the `.csproj file` which is in project folder. Then the IDE will take care of restoring the .NET and NPM dependencies. After restoring project dependencies, press `Ctrl+F5` to launch the application in a browser.
