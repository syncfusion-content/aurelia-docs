---
layout: post
title: How to
description: How to
platform: aurelia
control: Grid
documentation: ug
---
# How to

## Column Template using JsRender

If the columns of the grid are defined in the code behind then the template columns can be rendered using js-render templates by defining the templateId in the columns API.

The following code example explains how to use the js-render templates for rendering template column.

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
                   template:'#Template',  
                   width: 40  
                  }];  
			}
    }
    
{% endhighlight %}


The following output is displayed as a result of the above code example.

![](columns_images/columns_img2.PNG)

