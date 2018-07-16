---
layout: post
title: DataBinding with Grid widget for Syncfusion Essential Aurelia
description: How to bind in-memory JSON and remote web services in Grid
platform: Aurelia
control: Grid
documentation: ug
--- 
# Data binding

The Grid control uses [`ej.DataManager`](http://helpjs.syncfusion.com/js/datamanager/overview# "ej.DataManager") which supports both RESTful JSON data services binding and local JSON array binding.  The [`e-data-source`](http://help.syncfusion.com/api/js/ejgrid#members:datasource "dataSource") property can be assigned either with the instance of [`ej.DataManger`](http://help.syncfusion.com/api/js/ejdatamanager# "ej.DataManager") or JSON data array collection. It supports different kinds of data binding methods such as

1. Local data
2. Remote data

## Local Data

To bind local data to the Grid, you can assign a JSON array to the [`e-data-source`](http://help.syncfusion.com/api/js/ejgrid#members:datasource "dataSource") property.

The following code example describes the above behavior.

{% highlight html %}

    <template>
    <div>
        <ej-grid e-data-source.bind="data" e-allow-paging=true>
            <ej-column e-field="OrderID" ></ej-column>
            <ej-column e-field="EmployeeID"></ej-column>
            <ej-column e-field="ShipCity"></ej-column>
            <ej-column e-field="ShipCountry"></ej-column>
            <ej-column e-field="Freight"></ej-column
        </ej-grid>
    </div>
    </template>
{% endhighlight %}


{% highlight javascript %}
import 'http://js.syncfusion.com/demos/web/scripts/jsondata.min.js';
  export class Grid {
    
            constructor() {
			    this.data = window.gridData;
			}

    }
{% endhighlight %}


The following output is displayed as a result of the above code example.

![](dataBinding_images/dataBinding_img1.png)


N> 1. There is no in-built support to bind the XML data to the grid. But you can achieve this requirement with the help of [custom adaptor] concept. 
N> 2. Refer this [Knowledge Base link](http://www.syncfusion.com/kb/3377/how-to-process-xml-data-from-server-using-datamanager-and-bound-to-grid#) for bounding XML data to grid using custom adaptor. 

## Remote Data

To bind remote data to Grid Control, you can assign a service data as an instance of [`ej.DataManager`](http://help.syncfusion.com/api/js/ejdatamanager# "DataManager") to the [`e-data-source`](http://help.syncfusion.com/api/js/ejgrid#members:datasource "dataSource") property.

### OData

OData is a standardized protocol for creating and consuming data. You can provide the [OData service](http://www.odata.org/#) URL directly to the [`ej.DataManager`](http://help.syncfusion.com/api/js/ejdatamanager# "DataManager") class and then you can assign it to Grid [`e-data-source`](http://help.syncfusion.com/api/js/ejgrid#members:datasource "datasource").

The following code example describes the above behavior.

{% highlight html %}
   <ej-grid e-data-source.bind="data" e-allow-paging=true>
            <ej-column e-field="OrderID" ></ej-column>
            <ej-column e-field="EmployeeID"></ej-column>
            <ej-column e-field="ShipCity"></ej-column>
            <ej-column e-field="ShipCountry"></ej-column>
            <ej-column e-field="Freight"></ej-column
   </ej-grid>

{% endhighlight %}

{% highlight javascript %}
  export class Grid {
    
            constructor() {
			    this.data = ej.DataManager({
                        url: "http://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders"
	                    });
			}

    }
{% endhighlight %}

The following output is displayed as a result of the above code example.

![](dataBinding_images/dataBinding_img2.png)

N> By default , if no adaptor is specified for ej.DataManager and only the url link is mentioned it will consider as ODataService.