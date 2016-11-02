---
layout: post
title: Getting started for Tooltip
description: How to create the Tooltip in Aurelia
platform: Aurelia
control: Tooltip
documentation: ug
keywords : ejTooltip, Tooltip, js Tooltip, Tooltip widget
---
# Getting started

## Preparing HTML document

The Tooltip control has the following list of external JavaScript dependencies. 

* [jQuery](http://jquery.com/) 1.7.1 and later versions

* [jQuery.easing](http://gsgd.co.uk/sandbox/jquery/easing/) - to support animation effects in the components

Refer to the internal dependencies in the following table.

<table>
<tr>
<th>
File                                </th><th>
Description/Usage</th></tr>
<tr>
<td>
ej.core.min.js</td><td>
It is referred always before using all the JS controls.</td></tr>
<tr>
<td>
ej.tooltip.min.js</td><td>
The Tooltip's main file.</td></tr>
</table>

To get started, you can use the `ej.web.all.min.js` file that encapsulates all the `ej` controls and frameworks in one single file.

## Create a Tooltip

Before we start with Tooltip, please refer [this page](https://help.syncfusion.com/aurelia/overview#getting-started) page for general information regarding integrating Syncfusion widget’s.

For quick start, we already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

    > git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
    > cd syncfusion-template-repository
    > npm install
    > jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia Tooltip component.

    Create Tooltip folder inside src/samples/ location.
    Create Tooltip.html file inside src/samples/Tooltip folder and use the below code example to render the Tooltip component.
	
The Tooltip can be created from any HTML element with the HTML `id` attribute and pre-defined options set to it. To create the Tooltip, you should call the `ejTooltip` jQuery plug-in function with the options as parameter. Refer to the following code example.

{% highlight html %}
 
      <template>
          <div>
          <div class="img" id="sample" ej-tooltip="e-content.bind:content;">
          <img src="http://js.syncfusion.com/demos/web/images/tooltip/template-05.png" alt="Delphi">
          <div class="desc">Delphi Succinctly</div>
          </div>
	  </template>

{% endhighlight %}

{% highlight html %}
   
    export class Tooltip {
     constructor() {
       this.content = "Learn the fundamentals of Delphi to build a variety of solutions for many devices and platforms.";
      }
    }

{% endhighlight %}

Apply the following style sheet

{% highlight html %}

    <style>
       div.img {
        border: 1px solid #ccc;
        width: 159px;
        height: 213px;
        left: 35%;
        position: relative;
        top: 20%;
      }
     div.img img {
        width: 159px;
        height: 179px;
       }
     div.desc {
        padding: 8px;
        text-align: center;
       }
    </style>
    
{% endhighlight %}

![](Getteing-Started_images/Getteing-Started_img1.jpeg)

## Setting Dimensions

Tooltip dimensions can be set using [width](http://help.syncfusion.com/js/api/ejtooltip#members:width) and [height](http://help.syncfusion.com/js/api/ejtooltip#members:height) API.

{% highlight html %}
 
     <template>
        <div>
	     TypeScript lets you write <a  id="link1" ej-tooltip="e-content.bind:content;e-width:200px;e-height:100px"><u>JavaScript</u> </a>the way you really want to.
         </div>
	 </template>
	 // Creates the Tooltip

{% endhighlight %}

{% highlight html %}

     export class Tooltip {
      constructor() {
        this.content = "JavaScript is the programming language of HTML and the Web.";
   
          }
          }

{% endhighlight %}

## Tooltip Appearance 

You can configure the appearance of the Tooltip with the title, close button and call out as your application requires.

{% highlight html %}
 
    <template>
          <div>
          <div class="img" id="sample" ej-tooltip="e-content.bind:content;e-width:200px;e-height:100px;e-title:Delphi Succintly;e-close-mode:sticky;e-is-balloon:false">
          <img src="http://js.syncfusion.com/demos/web/images/tooltip/template-05.png" alt="Delphi">
          <div class="desc">Delphi Succinctly</div>
          </div>
	  </template>

// Creates the Tooltip
    
{% endhighlight %}

Apply the following styles to show the Tooltip.

{% highlight html %}

    <style>
       div.img {
        border: 1px solid #ccc;
        float: left;
        box-sizing: border-box;
        height: 200px;
        width: 146px;
         }
        div.img img{
        width: 100%;
        height: 166px;
        }
       div.desc {
        padding: 6px;
        text-align: center;
         }
    </style>
    
{% endhighlight %}

![](Getteing-Started_images/Getteing-Started_img2.jpeg)

