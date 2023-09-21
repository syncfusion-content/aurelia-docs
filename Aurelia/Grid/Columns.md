---
layout: post
title: Columns with Grid widget for Syncfusion Essential Aurelia
description: How to define the columns and its features
platform: Aurelia
control: Grid
documentation: ug
--- 
# Columns

Column definitions are used as the [`e-data-source`](https://help.syncfusion.com/api/js/ejgrid#members:datasource) schema in Grid and it plays vital role in rendering column values in required format. Grid operations such as sorting, filtering, editing would be performed based on the column definitions. The [`e-field`](https://help.syncfusion.com/api/js/ejgrid#members:columns-field) property of the [`ej-column`](https://help.syncfusion.com/api/js/ejgrid#members:columns) is necessary to map the datasource values in Grid columns.

N> 1. If the column with [`e-field`](https://help.syncfusion.com/api/js/ejgrid#members:columns-field) is not in the datasource, then the column values will be displayed as empty.
N> 2. If the [`e-field`](https://help.syncfusion.com/api/js/ejgrid#members:columns-field) name contains "dot" operator then it is considered as complex binding.

## Column Template

HTML templates can be specified in the [`ej-template`](https://help.syncfusion.com/api/js/ejgrid#members:columns-template) definition of the particular column as a string (HTML element) or ID of the template's HTML element.

N> If [`e-field`](https://help.syncfusion.com/api/js/ejgrid#members:columns-field) is not specified, you will not able to perform editing, grouping, filtering, sorting, search and summary functionalities in particular column.

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

N> When the columns are generated dynamically, JsRender templates can be used to render the template columns. Please refer the [`How To`](https://help.syncfusion.com/aurelia/grid/how-to "Column Template using JsRender") to render the template columns using JsRender templates.
