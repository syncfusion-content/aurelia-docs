---
layout: post
title: Getting Started for DropDownList
description: Getting Started for DropDownList
platform: Aurelia
control: DropDownList
documentation: ug
keywords: DropDownList, js dropdown, Populating data
---

# Getting Started

The external script dependencies of the DropDownList widget are,

* [jQuery 1.7.1](http://jquery.com/) and later versions.
* [jQuery.easing](http://gsgd.co.uk/sandbox/jquery/easing/) - to support the animation effects.

And the internal script dependencies of the DropDownList widget are:

<table>
	<tr>
		<th>File </th>
		<th>Description / Usage </th>
	</tr>
	<tr>
		<td>ej.core.min.js</td>
		<td>Must be referred always before using all the JS controls.</td>
	</tr>
	<tr>
		<td>ej.data.min.js</td>
		<td>Used to handle data operation and should be used while binding data to JS controls.</td>
	</tr>
	<tr>
		<td>ej.dropdownlist.min.js</td>
		<td>The dropdownlist’s main file</td>
	</tr>
	<tr>
		<td>ej.checkbox.min.js</td>
		<td>Should be referred when using checkbox functionalities in DropDownList.</td>
	</tr>
	<tr>
		<td>ej.scroller.min.js</td>
		<td>Should be referred when using scrolling in DropDownList.</td>
	</tr>
	<tr>
		<td>ej.draggable.min.js</td>
		<td>Should be referred when using popup resize functionality in DropDownList.</td>
	</tr>
</table>

For getting started you can use the ‘ej.web.all.min.js’ file, which encapsulates all the 'ej' controls and frameworks in one single file.<br/> 

For themes, you can use the ‘ej.web.all.min.css’ CDN link from the snippet given. To add the themes in your application, please refer [this link](http://help.syncfusion.com/js/theming-in-essential-javascript-components#adding-specific-theme-to-your-application).

## Creating DropDownList in Aurelia

Before we start with DropDownList, please refer [this page](https://help.syncfusion.com/aurelia/overview#getting-started) page for general information regarding integrating Syncfusion widget’s.

For quick start, we already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

    > git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
    > cd syncfusion-template-repository
    > npm install
    > jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia DropDownList component.

    Create DropDownList folder inside src/samples/ location.
    Create DropDownList.html file inside src/samples/DropDownList folder and use the below code example to render the DropDownList component.

The DropDownList can be created from a HTML ‘input’ element with the HTML 'id' attribute and pre-defined options set to it. To create the DropDownList, you should call the 'ejDropDownList' jQuery plug-in function.

{% highlight html %}
	
	<template>
      <div>
        <input type="text" id="dropdown1" ej-drop-down-list="e-data-source.bind:dataSource;e-fields.bind:fields;"/>
      </div>
    </template>
			
{% endhighlight %}
	
{% highlight html%}	
	
   export class DDL{
      items= [
            {item: 'ListItem 1' }, { item: 'ListItem 2' }, { item: 'ListItem 3' },
            { item: 'ListItem 4' }, { item: 'ListItem 5' }
            ];
     constructor() {
     this.fields = {text: 'item'};
     this.dataSource = this.items;
   
       }
    }

{% endhighlight %}

![](Getting-Started-images/Getting-Started_img1.jpeg)

## Populating data

The DropDownList can be bounded to both local array and remote data services .You can bind data to DropDownList through services using  [dataSource](http://help.syncfusion.com/js/api/ejdropdownlist#members:datasource) property 
 
{% highlight html %}

    <template>
      <div>
        <input type="text" id="dropdown1" ej-drop-down-list="e-data-source.bind:dataSource;e-fields.bind:fields;"/>
      </div>
    </template>
	
{% endhighlight %}
	
{% highlight html%}	
	
    export class DDL{
        
     customers= [
                 { id: "1", text: "ALFKI" }, { id: "2", text: "ANATR" }, { id: "3", text: "ANTON" },
                 { id: "4", text: "AROUT" }, { id: "5", text: "BERGS" }, { id: "6", text: "BLAUS" }
            ];
    constructor() {   
        this.fields = {text: 'text',id:'id',value:'text'};
        this.dataSource = ej.DataManager(this.customers);
       }
    }
	
{% endhighlight %}
	
![](Getting-Started-images/Getteing-Started_img2.jpeg)

## Setting Dimensions

DropDownList dimensions can be set using width and height API.
	
{% highlight html %}
	
	<template>
      <div>
        <input type="text" id="dropdown1" ej-drop-down-list="e-data-source.bind:dataSource;e-fields.bind:fields;e-width:200px;e-height:50px"/>
     </div>
   </template>

{% endhighlight %}
	
**Setting dimensions to Popup list**

PopupWidth and popupHeight can be used to create a fixed size popup list.

{% highlight html %}

	<template>
      <div>
        <input type="text" id="dropdown1" ej-drop-down-list="e-data-source.bind:dataSource;e-fields.bind:fields;e-popup-width:200px;e-popup-height:100px"/>
      </div>
  </template>

{% endhighlight %}
	
## Setting and Getting Value

You can select single or multiple values from DropDownList widget. To assign a value initially to the DropDownList, you can use [value](http://help.syncfusion.com/js/api/ejdropdownlist#members:value) property.

N> To select multiple items based on index, refer [here](functionalities#selection).

{% highlight html %}

	<template>
      <div>
        <input type="text" id="dropdown1" ej-drop-down-list="e-data-source.bind:dataSource;e-fields.bind:fields;e-popup-width:200px;e-popup-height:100px;e-value.bind:value" e-on-change.trigger="change($event)" />
     </div>
  </template>

{% endhighlight %}
	
{% highlight html %}	
	
     export class DDL{
        items= [
            {item: 'ListItem 1', value:"item 1"}, { item: 'ListItem 2',value:"item 2" }, { item: 'ListItem 3',value:"item 3" },
            { item: 'ListItem 4',value:"item 4" }, { item: 'ListItem 5',value:"item 5"}
            ];
       constructor() {
        this.fields = {text: 'item' ,value:'value'};
        this.dataSource = this.items;
	    this.value="item 3";
   
       }
     change(event) {
  
       var obj=$("#dropdown1").data("ejDropDownList");
      console.log("Selected Item's Text - " + obj.option("text"));
      console.log("selected Item's Value - " + obj.option("value"));  
       }
  
      }

{% endhighlight %}

