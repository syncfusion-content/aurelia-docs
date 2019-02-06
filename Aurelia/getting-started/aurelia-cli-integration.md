---
layout: post
title: Integration of aurelia-syncfusion-bridge with Aurelia CLI
description: How to integrate aurelia-syncfusion-bridge with Aurelia CLI
platform: Aurelia
control: Getting started
documentation: ug
keywords: Aurelia,Syncfusion,aurelia-syncfusion-bridge,Aurelia CLI
---
# Integration of aurelia-syncfusion-bridge with Aurelia CLI

[Aurelia CLI](https://github.com/aurelia/cli) is the command line tooling for Aurelia, used for creating projects, scaffolding, bundling and more. we can write our application with either [esnext](https://esnext.github.io/) or [TypeScript](https://www.typescriptlang.org/) code which works well with any standard text editor. This Aurelia CLI project uses [NPM](https://www.npmjs.com/) for package management and [RequireJS](http://requirejs.org/) for loading.

The [aurelia-syncfusion-bridge](https://github.com/aurelia-ui-toolkits/aurelia-syncfusion-bridge) plugin brings the [Syncfusion Essential Studio for JavaScript Widgets](https://github.com/syncfusion/JavaScript-Widgets) into Aurelia world. So, by configuring aurelia-syncfusion-bridge plugin with Aurelia CLI, we can use Syncfusion components in Aurelia application.

The upcoming sections will describe about the installation and configuration of aurelia-syncfusion-bridge with Aurelia CLI.

## Synopsis

* [Prerequisites](#prerequisites)
* [Aurelia CLI project](#aurelia-cli-project)
* [Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge](#installation-of-syncfusion-javascript-widgets-and-aurelia-syncfusion-bridge)
* [Aurelia CLI configuration](#aurelia-cli-configuration)
* [Bridge registration](#bridge-registration)
* [Getting started](#getting-started)
* [Running the Application](#running-the-application)
* [Deploying the Application in production](#deploying-the-application-in-production)

## Prerequisites

* [NodeJS](https://nodejs.org/en/) version >=6.0

## Aurelia CLI project

In this section, we will discuss about the creation of [Aurelia CLI](http://aurelia.io/hub.html#/doc/article/aurelia/framework/latest/the-aurelia-cli) project and installation of Aurelia project dependencies.

* To create a new Aurelia project, we should run the following command which will show some configuration options to customize your project.

{% highlight bash %}

> npm install aurelia-cli -g
> au new

{% endhighlight %}

During project configuration, we will be asked to install project dependencies, please install it.
After creating our project with default configuration, our command prompt would be look like the below one.

{% highlight bash %}

E:\>au new

Please enter a name for your new project below.

[aurelia-app]> aurelia-syncfusion

Would you like to use the default setup or customize your choices?

1. Default ESNext (Default)
   A basic web-oriented setup with Babel for modern JavaScript development.
2. Default TypeScript
   A basic web-oriented setup with TypeScript for modern JavaScript development.
3. Custom
   Select transpiler, CSS pre-processors and more.

[Default ESNext]>

Project Configuration

    Name: aurelia-syncfusion
    Platform: Web
    Transpiler: Babel
    Markup Processor: Minimal Minification
    CSS Processor: None
    Unit Test Runner: Karma
    Editor: Visual Studio Code


Would you like to create this project?

1. Yes (Default)
   Creates the project structure based on your selections.
2. Restart
   Restarts the wizard, allowing you to make different selections.
3. Abort
   Aborts the new project wizard.

[Yes]>
Project structure created and configured.

Would you like to install the project dependencies?

1. Yes (Default)
   Installs all server, client and tooling dependencies needed to build the project.
2. No
   Completes the new project wizard without installing dependencies.

[Yes]>

Installing project dependencies.
aurelia-syncfusion@0.1.0 E:\aurelia-syncfusion
+-- aurelia-animator-css@1.0.1
| +-- aurelia-metadata@1.0.3
...................
...................

  +-- through2-filter@2.0.0

Congratulations! Your Project "aurelia-syncfusion" Has Been Created!


Now it's time for you to get started. It's easy. First, change directory into your new project's folder. You can use
cd aurelia-syncfusion to get there. Once in your project folder, simply run your new app with
au run. Your app will run fully bundled. If you would like to have it auto-refresh whenever you make
changes to your HTML, JavaScript or CSS, simply use the --watch flag. If you want to build your app for
production, run au build --env prod. That's just about all there is to it. If you need help, simply
run au help.


Happy Coding!

E:\>

{% endhighlight %}

## Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge

Install syncfusion-javascript Widgets and aurelia-syncfusion-bridge by executing the following commands.

{% highlight bash %}

> npm install syncfusion-javascript --save
> npm install aurelia-syncfusion-bridge --save

{% endhighlight %}

## Aurelia CLI configuration

In this section, we will discuss about the configuration of Aurelia to seamlessly work with aurelia-syncfusion-bridge.

* In `aurelia_project/aurelia.json` file, add the following lines to the `build.bundles.dependencies` to work with Aurelia and Syncfusion JavaScript components.

{% highlight javascript %}

"dependencies": [
          ......
          ......
          "text",
          "jquery",
          "jquery-validation",
          {
            "name": "aurelia-templating-resources",
            "path": "../node_modules/aurelia-templating-resources/dist/amd",
            "main": "aurelia-templating-resources"
          },
          {
            "name": "aurelia-templating-router",
            "path": "../node_modules/aurelia-templating-router/dist/amd",
            "main": "aurelia-templating-router"
          },
          {
            "name": "aurelia-testing",
            "path": "../node_modules/aurelia-testing/dist/amd",
            "main": "aurelia-testing",
            "env": "dev"
          },
          {
            "name": "aurelia-syncfusion-bridge",
            "path": "../node_modules/aurelia-syncfusion-bridge/dist/amd",
            "main": "index",
            "resources": [
              "grid/*.js"
            ]
          },
          {
            "name": "syncfusion-javascript",
            "path": "../node_modules/syncfusion-javascript/",
            "main": false,
            "resources": [
              "Content/ej/web/ej.widgets.core.bootstrap.min.css",
              "Content/ej/web/bootstrap-theme/ej.theme.min.css",
              "Content/ej/web/responsive-css/ej.responsive.css",
              "Scripts/ej/web/ej.grid.min.js"
            ]
          },
          {
            "name": "jsrender",
            "path": "../node_modules/jsrender/",
            "main": "jsrender"
          }
        ]

{% endhighlight %}

N> To use `ejTemplate`, we need to add `common/template.js` to the `resources` of `aurelia-syncfusion-bridge`.

N> To use any other Syncfusion components in Aurelia application, we need to add specific Syncfusion Aurelia component path to the `resources` of `aurelia-syncfusion-bridge` and `syncfusion-javascript` in `build.bundles.dependencies` file. For example, To use button component, add `button/*.js` to the `resources` of `aurelia-syncfusion-bridge` and `Scripts/ej/web/ej.grid.min.js` to the `resources` of `syncfusion-javascript`.

N> To use all Syncfusion component, we need to add `**/*.js` to the `resources` of `aurelia-syncfusion-bridge` and `Scripts/ej/web/ej.web.all.min.js` to the `resources` of `syncfusion-javascript`.

* We need to copy the `fonts/images` to the location where Syncfusion themes expects them. This can be done by using `copyFiles` in `aurelia.json`

{% highlight javascript %}

   "options": {
      "minify": "stage & prod",
      "sourcemaps": "dev & stage"
    },
    "copyFiles": {
      "node_modules/syncfusion-javascript/Content/ej/web/common-images/**/*": "common-images",
      "node_modules/syncfusion-javascript/Content/ej/web/bootstrap-theme/images/**": "images"
    },

{% endhighlight %}

N> If we are switching to any other theme, modify `copyFiles` according to our theme as well as update `syncfusion-javascript` resources in `build.bundles.dependencies`

* Also, change the `stub` property to `false` in `aurelia.json` file.

{% highlight javascript %}

    "loader": {
      "type": "require",
      "configTarget": "vendor-bundle.js",
      "includeBundleMetadataInConfig": "auto",
      "plugins": [
        {
          "name": "text",
          "extensions": [
            ".html",
            ".css"
          ],
          "stub": false
        }
      ]
    }

{% endhighlight %}

N> If the `stub` property is said to `true`, then the external files will not be loaded. To know more about this, navigate [here](https://github.com/aurelia/cli/issues/212).

## Bridge registration

In this section, we will discuss about the registration of Syncfusion bridge with Aurelia.

Register the `aurelia-syncfusion-bridge` plugin with Aurelia in our `main.js` file which is in `src` folder. For example, to register `ejGrid` component, we need to import `syncfusion-javascript/Scripts/ej/web/ej.grid.min` in `main.js` file.

{% highlight javascript %}

import environment from './environment';
import 'syncfusion-javascript/Scripts/ej/web/ej.grid.min';
Promise.config({
  warnings: {
    wForgottenReturn: false
  }
});

export function configure(aurelia) {
  aurelia.use
    .standardConfiguration()
    .feature('resources')
    //register aurelia-syncfusion-bridge plugin here
    .plugin('aurelia-syncfusion-bridge', (syncfusion) => syncfusion.useAll());

  if (environment.debug) {
    aurelia.use.developmentLogging();
  }

  if (environment.testing) {
    aurelia.use.plugin('aurelia-testing');
  }

  aurelia.start().then(() => aurelia.setRoot());
}

{% endhighlight %}

N> To use `ejTemplate`, we need to add `syncfusion.ejGrid().ejTemplate();` in our `main.js` file.

N> To load button component with grid component additionally, we need to import `syncfusion-javascript/Scripts/ej/web/ej.button.min` and add `syncfusion.ejGrid().ejButton();` in our `main.js` file.

N> To load all Syncfusion components, we need to import `syncfusion-javascript/Scripts/ej/web/ej.web.all.min` and add `syncfusion.useAll()` in our `main.js` file.

N> If you are facing issue like `ReferenceError: jQuery is not defined` in Aurelia-CLI with Typescript Compiler, the root cause of the issue is jQuery is not bundled in application. To resolve the issue, refer the below code snippet in `webpack.config.js` file.

{% highlight javascript %}

plugins: [
    ...when(!karma, new DuplicatePackageCheckerPlugin()),
    new AureliaPlugin(),
    new ProvidePlugin({
      'Promise': 'bluebird',
      '$': 'jquery', // jquery is defined
      'jQuery': 'jquery',
      'window.jQuery': 'jquery'
  }),
  
{% endhighlight %}

And in the updated Aurelia-CLI version, to register the `aurelia-syncfusion-bridge` in `main.ts` file , refer the below structure.

{% highlight javascript %}

aurelia.use
    .standardConfiguration()
    .feature(PLATFORM.moduleName('resources/index'))
    .plugin(PLATFORM.moduleName('aurelia-syncfusion-bridge'), (syncfusion) => syncfusion.useAll());
  
{% endhighlight %}

## Getting started

The below step describes to create Syncfusion Aurelia Grid component.

* In `src/app.html` file, add the following code snippet to your view.

{% highlight html %}

<template>
    <require from="syncfusion-javascript/Content/ej/web/ej.widgets.core.bootstrap.min.css"></require>
    <require from="syncfusion-javascript/Content/ej/web/bootstrap-theme/ej.theme.min.css"></require>
    <require from="syncfusion-javascript/Content/ej/web/responsive-css/ej.responsive.css"></require>
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

* In `src/app.js` file, add the following code snippet to your view model.

{% highlight javascript %}

export class App {
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

## Running the Application

To run the app, execute the following command and browse to [http://localhost:9000](http://localhost:9000) to see the application.

{% highlight bash %}

> au run –watch

{% endhighlight %}

## Deploying the Application in production

Run the following build command

{% highlight bash %}

> au build --env prod

{% endhighlight %}

Then copy below file/folder to main deployment folder on our server.

* index.html
* scripts
* favicon.ico
* Assets files mentioned in aurelia.json `copyFiles`. Here we mentioned the `common-images`, `images` folder which is used for Syncfusion themes.
