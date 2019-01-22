---
layout: post
title: Electron and Syncfusion Aurelia Skeleton esnext with Webpack
description: How to integrate aurelia-syncfusion-bridge with Aurelia skeleton-navigation-esnext-webpack and configure electron
platform: Aurelia
control: Getting started
documentation: ug
keywords: Aurelia,Syncfusion,aurelia-syncfusion-bridge,Aurelia skeleton-navigation-esnext-webpack,
---

# Desktop application using Electron with Aurelia Skeleton-navigation-esnext with Webpack

[Electron](https://electron.atom.io/docs/tutorial/quick-start/) is a framework which enables the development of cross-platform desktop application using web technologies (HTML, CSS, JavaScript).

## Integration of aurelia-syncfusion-bridge with Aurelia skeleton-navigation-esnext-webpack

[Aurelia skeleton-navigation-esnext-webpack](https://github.com/aurelia/skeleton-navigation/tree/master/skeleton-esnext-webpack) uses the [Babel](https://babeljs.io/) transpiler so that we can write our application with esnext code which works well with any standard text editor. This skeleton uses [NPM](https://www.npmjs.com/) for package management and [Webpack](https://webpack.github.io/) for bundling.

The [aurelia-syncfusion-bridge](https://github.com/aurelia-ui-toolkits/aurelia-syncfusion-bridge) plugin brings the [Syncfusion Essential Studio for JavaScript Widgets](https://github.com/syncfusion/JavaScript-Widgets) into Aurelia world. So, by configuring aurelia-syncfusion-bridge plugin with Aurelia skeleton-navigation-esnext-webpack, we can use Syncfusion components in Aurelia application.

## Synopsis

* [Prerequisites](#prerequisites)
* [Aurelia skeleton-navigation-esnext-webpack](#aurelia-skeleton-navigation-esnext-webpack)
* [Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge](#installation-of-syncfusion-javascript-widgets-and-aurelia-syncfusion-bridge)
* [Webpack configuration](#webpack-configuration)
* [Bridge registration](#bridge-registration)
* [Getting started](#getting-started)
* [Running the Application](#running-the-application)

## Prerequisites

* [NodeJS](https://nodejs.org/en/) version >=6.0

## Aurelia skeleton-navigation-esnext-webpack

Below steps explains about the installation of Aurelia project dependencies.

* Clone Aurelia skeleton-navigation from master branch and install project dependencies by executing the following commands.

{% highlight bash %}

> git clone https://github.com/aurelia/skeleton-navigation.git
> cd skeleton-navigation/skeleton-esnext-webpack
> npm install

{% endhighlight %}

N> Ensure all the dependencies are installed without any errors.

## Installation of syncfusion-javascript Widgets and aurelia-syncfusion-bridge

Install [syncfusion-javascript Widgets](https://www.npmjs.com/package/syncfusion-javascript) and [aurelia-syncfusion-bridge](https://www.npmjs.com/package/aurelia-syncfusion-bridge) by executing the following commands.

{% highlight bash %}

> npm install syncfusion-javascript --save
> npm install aurelia-syncfusion-bridge --save

{% endhighlight %}

## Webpack configuration

Configure the webpack to seamlessly work with `aurelia-syncfusion-bridge`.

* In `webpack.config.js` file, add aurelia-syncfusion-bridge to `entry.vendor` like the below code section.

{% highlight javascript %}

entry: {
    app: ['aurelia-bootstrapper'],
    vendor: ['bluebird', 'jquery', 'bootstrap', 'aurelia-syncfusion-bridge'],
  },

{% endhighlight %}

## Bridge registration

Register the `aurelia-syncfusion-bridge` plugin with Aurelia in our `main.js` file which is in `src` folder. For example, to register `ejGrid` component, we need to import `syncfusion-javascript/Scripts/ej/web/ej.grid.min` in `main.js` file.

{% highlight javascript %}

import '../static/styles.css';
import 'font-awesome/css/font-awesome.css';
import 'bootstrap/dist/css/bootstrap.css';
import 'babel-polyfill';
import 'syncfusion-javascript/Scripts/ej/web/ej.grid.min';
import * as Bluebird from 'bluebird';
// remove out if you don't want a Promise polyfill (remove also from webpack.config.js)
Bluebird.config({ warnings: { wForgottenReturn: false } });

export async function configure(aurelia) {
  aurelia.use
    .standardConfiguration()
    .developmentLogging()
    //register aurelia-syncfusion-bridge plugin here
    .plugin(PLATFORM.moduleName('aurelia-syncfusion-bridge'), (syncfusion) => syncfusion.ejGrid());

  // Uncomment the line below to enable animation.
  // aurelia.use.plugin(PLATFORM.moduleName('aurelia-animator-css'));
  // if the css animator is enabled, add swap-order="after" to all router-view elements

  // Anyone wanting to use HTMLImports to load views, will need to install the following plugin.
  // aurelia.use.plugin(PLATFORM.moduleName('aurelia-html-import-template-loader'));

  await aurelia.start();
  await aurelia.setRoot(PLATFORM.moduleName('app'));
}

{% endhighlight %}

N> To use `ejTemplate`, we need to add `syncfusion.ejGrid().ejTemplate();` in our `main.js` file.

N> To load button component with grid component additionally, we need to import `syncfusion-javascript/Scripts/ej/web/ej.button.min` and add `syncfusion.ejGrid().ejButton();` in our `main.js` file.

N> To load all Syncfusion components, we need to import `syncfusion-javascript/Scripts/ej/web/ej.web.all.min` and add `syncfusion.useAll()` in our `main.js` file.

## Getting started

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
      { route: ['', 'welcome'], name: 'welcome',      moduleId: PLATFORM.moduleName('./welcome'),      nav: true, title: 'Welcome' },
      { route: 'users',         name: 'users',        moduleId: PLATFORM.moduleName('./users'),        nav: true, title: 'Github Users' },
      { route: 'child-router',  name: 'child-router', moduleId: PLATFORM.moduleName('./child-router'), nav: true, title: 'Child Router' },
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

## Installing Electron dependencies

[electron](https://www.npmjs.com/package/electron) - The Electron framework lets us write cross-platform desktop applications using JavaScript, HTML and CSS. Run the below command to install the electron dependency.

{% highlight bash %}

> npm install electron --save-dev

{% endhighlight %}

## Configure Electron application window for Electron

Create JavaScript file index.js which is the startup of electron application. It should create window and it handles the system events. To know more about main process of electron, refer the link [here](https://electron.atom.io/docs/tutorial/quick-start/#write-your-first-electron-app).

Copy the below code into `index.js` file.

{% highlight javascript %}

//Note: This file is provided as an aid to help you get up and running with
//Electron for desktop apps. See the readme file for more information.
/* eslint-disable strict, no-var, no-console */

'use strict';

const electron = require('electron');
const {app} = electron;
const {BrowserWindow} = electron;
let mainWindow;

app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') {
    app.quit();
  }
});

app.on('ready', () => {
  mainWindow = new BrowserWindow({
    width: 800,
    height: 600,
    // Note: The following line turns off Node integration to allow
    // jQuery to work properly. If you need Node integration, please
    // see the Electron FAQ for how to enable this:
    // http://electron.atom.io/docs/faq/
    webPreferences: {
      nodeIntegration: false
    }
  });

  mainWindow.loadURL(`file://${__dirname}/dist/index.html`);
  mainWindow.webContents.on('did-finish-load', () => {
    mainWindow.setTitle(app.getName());
  });
  
  mainWindow.on('closed', () => {
    mainWindow = null;
  });
});

{% endhighlight %}

Modify the `webpack.config.js` file with below script to run the electron sample with webpack.

{% highlight javascript %}

const path = require('path')
const HtmlWebpackPlugin = require('html-webpack-plugin');
const CopyWebpackPlugin = require('copy-webpack-plugin');
const ExtractTextPlugin = require('extract-text-webpack-plugin');
const { AureliaPlugin } = require('aurelia-webpack-plugin');
var webpack = require('webpack');
const { optimize: { CommonsChunkPlugin }, ProvidePlugin } = require('webpack')
const buildPath = path.resolve(__dirname, "./dist");

// config helpers:
const ensureArray = (config) => config && (Array.isArray(config) ? config : [config]) || []
const when = (condition, config, negativeConfig) =>
  condition ? ensureArray(config) : ensureArray(negativeConfig)

// primary config:
const title = 'Aurelia Navigation Skeleton';
const outDir = path.resolve(__dirname, 'dist');
const srcDir = path.resolve(__dirname, 'src');
const nodeModulesDir = path.resolve(__dirname, 'node_modules');

const cssRules = [
  { loader: 'css-loader' },
  {
    loader: 'postcss-loader',
    options: { plugins: () => [require('autoprefixer')({ browsers: ['last 2 versions'] })]}
  }
]

module.exports = ({production, server, extractCss, coverage} = {}) => ({
  resolve: {
    extensions: ['.js'],
    modules: [srcDir, 'node_modules'],
  },
  devtool: production ? 'source-map' : 'cheap-module-eval-source-map',
  entry: {
    app: ['aurelia-bootstrapper'],
    vendor: ['bluebird', 'jquery', 'bootstrap', 'aurelia-syncfusion-bridge'],
  },

  output: {
    path: outDir,
    filename: production ? '[name].[chunkhash].bundle.js' : '[name].[hash].bundle.js',
    sourceMapFilename: production ? '[name].[chunkhash].bundle.map' : '[name].[hash].bundle.map',
    chunkFilename: production ? '[name].[chunkhash].chunk.js' : '[name].[hash].chunk.js',
  },
  devServer: {
    contentBase: outDir,
    // serve index.html for all 404 (required for push-state)
    historyApiFallback: true,
  },
  module: {
    rules: [
      // CSS required in JS/TS files should use the style-loader that auto-injects it into the website
      // only when the issuer is a .js/.ts file, so the loaders are not applied inside html templates
      {
        test: /\.css$/i,
        issuer: [{ not: [{ test: /\.html$/i }] }],
        use: extractCss ? ExtractTextPlugin.extract({
          fallback: 'style-loader',
          use: cssRules,
        }) : ['style-loader', ...cssRules],
      },
      {
        test: /\.css$/i,
        issuer: [{ test: /\.html$/i }],
        // CSS required in templates cannot be extracted safely
        // because Aurelia would try to require it again in runtime
        use: cssRules,
      },
      { test: /\.html$/i, loader: 'html-loader' },
      { test: /\.js$/i, loader: 'babel-loader', exclude: nodeModulesDir,
        options: coverage ? { sourceMap: 'inline', plugins: [ 'istanbul' ] } : {},
      },
      { test: /\.json$/i, loader: 'json-loader' },
      // use Bluebird as the global Promise implementation:
      { test: /[\/\\]node_modules [\/\\]bluebird[\/\\].+\.js$/, loader: 'expose-loader?Promise' },
      // exposes jQuery globally as $ and as jQuery:
      { test: require.resolve('jquery'), loader: 'expose-loader?$!expose-loader?jQuery' },
      // embed small images and fonts as Data Urls and larger ones as files:
      { test: /\.(png|gif|jpg|cur)$/i, loader: 'url-loader', options: { limit: 8192 } },
      { test: /\.woff2(\?v=[0-9]\.[0-9]\.[0-9])?$/i, loader: 'url-loader', options: { limit: 10000, mimetype: 'application/font-woff2' } },
      { test: /\.woff(\?v=[0-9]\.[0-9]\.[0-9])?$/i, loader: 'url-loader', options: { limit: 10000, mimetype: 'application/font-woff' } },
      // load these fonts normally, as files:
      { test: /\.(ttf|eot|svg|otf)(\?v=[0-9]\.[0-9]\.[0-9])?$/i, loader: 'file-loader' },
    ]
  },
  plugins: [
    new AureliaPlugin(),
    new ProvidePlugin({
      'Promise': 'bluebird',
      '$': 'jquery',
      'jQuery': 'jquery',
      'window.jQuery': 'jquery',
      Popper: ['popper.js', 'default'] // Bootstrap 4 Dependency.
    }),
    new webpack.DefinePlugin({
      'process.env.production': JSON.stringify(production)
    }),
    new HtmlWebpackPlugin({
      template: 'index.html',
      minify: production ? {
        removeComments: true,
        collapseWhitespace: true
      } : undefined,
      metadata: {
        title, server,
      },
    }),
    new CopyWebpackPlugin([
      { from: 'static/favicon.ico', to: 'favicon.ico' }
    ]),
    ...when(extractCss, new ExtractTextPlugin({
      filename: production ? '[contenthash].css' : '[id].css',
      allChunks: true,
    })),
    ...when(production, new CommonsChunkPlugin({
      name: 'common'
    }))
  ],

  externals: ['electron']
  
})

{% endhighlight %}

Specify the `index.js` file in [main](https://docs.npmjs.com/files/package.json#main) field of `package.json` file, which is the startup script of your app. Refer below code snippet for adding main field. And also add the below `clean` and `prod` scripts to `clean the folder` and `generate the production build`.

{% highlight javascript %}

"name": "skeleton-esnext-webpack",
  "version": "1.0.0",
  "description": "A starter kit for building a standard navigation-style app with Aurelia and Webpack.",
  "main": "index.js", // Specify index.js file in main field
  "repository": {
    "url": "git+ssh://git@github.com/aurelia/skeleton-navigation.git",
    "type": "git"
  },
. . .
. . .
"scripts": {
    . . .
    . . .
    "clean": "rimraf dist", // To clean the dist
    "prod": "npm run clean && webpack -p" // Generate production build
  },
. . .

{% endhighlight %}

Run the below command for production build(dist)

{% highlight bash %}

> npm run prod

{% endhighlight %}

Run the electron app with below command

{% highlight bash %}

> electron .

{% endhighlight %}

Refer to the below link for sample application which is fully configured with Syncfusion Aurelia bridge and Electron.

[Sample](http://www.syncfusion.com/downloads/support/directtrac/general/ze/skeletonwithsyncfusion1660917682.zip)