---
layout: post
title: Columns with Grid widget for Syncfusion Essential Aurelia
description: How to define the columns and its features
platform: Aurelia
control: Grid
documentation: ug
--- 
# Columns

Column definitions are used as the [`e-data-source`](http://help.syncfusion.com/api/js/ejgrid#members:datasource "dataSource") schema in Grid and it plays vital role in rendering column values in required format. Grid operations such as sorting, filtering, editing would be performed based on the column definitions. The [`e-field`](http://help.syncfusion.com/api/js/ejgrid#members:columns-field "field") property of the [`ej-column`](http://help.syncfusion.com/api/js/ejgrid#members:columns "columns") is necessary to map the datasource values in Grid columns.

N> 1. If the column with [`e-field`](http://help.syncfusion.com/api/js/ejgrid#members:columns-field "field") is not in the datasource, then the column values will be displayed as empty.
N> 2. If the [`e-field`](http://help.syncfusion.com/api/js/ejgrid#members:columns-field "field") name contains "dot" operator then it is considered as complex binding.

## Column Template

HTML templates can be specified in the [`ej-template`](http://help.syncfusion.com/api/js/ejgrid#members:columns-template "template") definition of the particular column as a string (HTML element) or ID of the template's HTML element.

N> If [`e-field`](http://help.syncfusion.com/api/js/ejgrid#members:columns-field "field") is not specified, you will not able to perform editing, grouping, filtering, sorting, search and summary functionalities in particular column.

The following code example describes the above behavior.

{% highlight html %}

 <ej-grid e-data-source.bind="data" e-allow-paging=true e-page-settings.bind="pageSettings">
        <ej-column e-header-text="Photo">
            <ej-template>
            <img style='width: 75px; height: 70px' src='images/Employees/${EmployeeID}.png' alt='${EmployeeID}' />
            </ej-template>
        </ej-column>
        <ej-column e-field="EmployeeID"></ej-column>
        <ej-column e-field="FirstName"></ej-column>
        <ej-column e-field="LastName"></ej-column>
        <ej-column e-field="Country"></ej-column>
 </ej-grid>

{% endhighlight %}

{% highlight javascript %}
import 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js';
  export class Grid {
    
            constructor() {
			    this.data = window.employeeView;
                this.pageSettings = {pageSize:4};
			}
    }
{% endhighlight %}

The following output is displayed as a result of the above code example.

![](columns_images/columns_img1.png)


If the columns are created dynamically at run time in the code behind then the template columns can be rendered using js-render templates by defining the templateId in the columns API.

The following code example explains how to use the js-render templates for template column.

{% highlight html %}

<template>

   <ej-grid e-data-source.bind="gridData"
            e-allow-paging="true"
            e-page-settings.bind="pageSettings"
            e-columns.bind="columns">
   </ej-grid>
   
   <script id="Template" type="text/x-jsrender"> 
         <a href="https://www.syncfusion.com">{{:CustomerID}}</a> 
   </script>

</template>

{% endhighlight %}

{% highlight javascript %}

import 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js';
  export class Grid {
    
            constructor() {
			    this.data = window.gridData;
                this.pageSettings = {pageSize:4};
                this.columns = [  
                  {  
                   field: 'OrderID',  
                   headerText: 'OrderID',  
                   width: 40  
                  },
                  {  
                   field: 'CustomerID',  
                   headerText: 'CustomerID',  
                   width: 40  
                  },
                  {  
                   field: 'Freight',  
                   headerText: 'Freight',  
                   width: 40  
                  },
                  {  
                   field:"EmployeeID",  
                   headerText: 'EmployeeID',  
                   isTemplateColumn:true,  
                   templateID:'#Template',  
                   width: 40  
                  }];  
			}
    }
    
{% endhighlight %}


The following output is displayed as a result of the above code example.

![](columns_images/columns_img2.PNG)
