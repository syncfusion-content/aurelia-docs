---
layout: post
title: Getting started with Grid widget for Syncfusion Essential Aurelia
description: How to create the Grid, data bind, enable paging, grouping, filtering and add summaries
platform: Aurelia
control: Grid
documentation: ug
---

# Getting Started

Before we start with the Grid, please refer [this page](https://help.syncfusion.com/aurelia/overview#getting-started) page for general information regarding integrating Syncfusion widget’s.

For quick start, we already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

    > git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
    > cd syncfusion-template-repository
    > npm install
    > jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia Grid component.

    Create grid folder inside src/samples/ location.
    Create grid.html file inside src/samples/grid folder and use the below code example to render the Grid component.
    Properties can be defined with `e-` prefix and long text properties needs to separated by `-`. E.g. ( `e-field` , `e-header-text`).
	
{% highlight html %}

    <template>
    <div>
        <ej-grid e-data-source.bind="shipDetails" >
            
        </ej-grid>
    </div>
    </template>

{% endhighlight %}	

* Create `grid.js` file inside `src/samples/grid` folder with below code snippet.

{% highlight js %}

    export class Grid {
    
            constructor() {
			    this.shipDetails = [
				       { Name: 'Hanari Carnes', City: 'Brazil' },
                       { Name: 'Split Rail Beer & Ale', City: 'USA' },
                       { Name: 'Ricardo Adocicados', City: 'Brazil' }
			    ]
			}

    }

{% endhighlight %}


![](Getting-started_images/Getting-started_img1.png)


## Data binding

[`Data binding`](http://helpjs.syncfusion.com/js/grid/data-binding) in the grid is achieved by using the [`ej.DataManager`](http://helpjs.syncfusion.com/js/datamanager/overview) that supports both RESTful JSON data services binding and local JSON array binding.  To set the data source to the grid, the [`dataSource`](http://help.syncfusion.com/api/js/ejgrid#members:columns-datasource) property is assigned with the instance of the `ej.DataManger`. For demonstration purpose, [Northwind OData service](http://mvc.syncfusion.com/Services/Northwnd.svc/) is used in this tutorial. Refer to the following code example.

{% highlight html %}

    <template>
    <div>
        <ej-grid e-data-source.bind="dataManager" >
            
        </ej-grid>
    </div>
    </template>

{% endhighlight %}	

Configure the `e-data-source` bind value `this.datamanager` in Aurelia view-model as shown in the following code.

{% highlight js %}

    export class Grid {
    
            constructor() {
			    this.dataManager = new ej.DataManager("http://mvc.syncfusion.com/Services/Northwnd.svc/Foods");
			}
    }

{% endhighlight %}

![](Getting-started_images/Getting-started_img2.png)



N> ODataAdaptor is the default adaptor for the DataManager. On binding to other web services, proper [data adaptor](http://helpjs.syncfusion.com/js/datamanager/data-adaptors) needs to be set on `adaptor` option of the DataManager.

## Enable Paging

[Paging](http://helpjs.syncfusion.com/js/grid/paging) can be enabled by setting the `e-allow-paging` to true.  This adds the pager in the bottom of the grid and page size can be customized by using the `e-page-settings` property.


{% highlight html %}

    <template>
    <div>
        <ej-grid e-data-source.bind="dataManager" e-allow-paging=true e-page-settings.bind="pageSettings">
            
        </ej-grid>
    </div>
    </template>

{% endhighlight %}	

Configure the `e-page-settings` bind value `this.pageSettings` in Aurelia view-model as shown in the following code.

{% highlight js %}

    export class Grid {
    
            constructor() {
			    this.dataManager = new ej.DataManager("http://mvc.syncfusion.com/Services/Northwnd.svc/Foods");
				this.pageSettings = { pageSize: 8 };
			}
    }

{% endhighlight %}

N> Pager settings can be customized by using the `e-page-settings` property. When it is not given the default values for `e-page-size` and `e-page-count` are 12 and 8 respectively.


![](Getting-started_images/Getting-started_img3.png)



## Enable Filtering

[`Filtering`](http://helpjs.syncfusion.com/js/grid/filter) can be enabled by setting the `e-allow-filtering` to `true`. By default, the filter bar row is displayed to perform filtering, you can change the filter type by using the `e-filter-setting` property.


{% highlight html %}

    <template>
    <div>
        <ej-grid e-data-source.bind="dataManager" e-allow-paging=true e-page-settings.bind="pageSettings" e-allow-filtering=true>
            
        </ej-grid>
    </div>
    </template>

{% endhighlight %}	


{% highlight js %}

    export class Grid {
    
            constructor() {
			    this.dataManager = new ej.DataManager("http://mvc.syncfusion.com/Services/Northwnd.svc/Foods");
				this.pageSettings = { pageSize: 8 };
			}
    }

{% endhighlight %}


![](Getting-started_images/Getting-started_img4.png)



## Enable Grouping

[`Grouping`](http://helpjs.syncfusion.com/js/grid/grouping) can be enabled by setting the `e-allow-grouping` to `true`. Columns can be grouped dynamically by drag and drop the grid column header to the group drop area. The initial grouping can be done by adding required column names in the `e-group-settings` property.


{% highlight html %}

    <template>
    <div>
        <ej-grid e-data-source.bind="dataManager" e-allow-paging=true e-page-settings.bind="pageSettings" e-allow-grouping=true>
            
        </ej-grid>
    </div>
    </template>

{% endhighlight %}	


{% highlight js %}

    export class Grid {
    
            constructor() {
			    this.dataManager = new ej.DataManager("http://mvc.syncfusion.com/Services/Northwnd.svc/Foods");
				this.pageSettings = { pageSize: 8 };
			}
    }

{% endhighlight %}


![](Getting-started_images/Getting-started_img5.png)



Refer to the following code example for initial grouping.


{% highlight html %}

    <template>
    <div>
        <ej-grid e-data-source.bind="dataManager" e-allow-paging=true e-page-settings.bind="pageSettings" e-allow-grouping=true e-group-settings.bind="groupSettings">
            
        </ej-grid>
    </div>
    </template>

{% endhighlight %}	

Configure the `e-group-settings` bind value `this.groupSettings` in Aurelia view-model as shown in the following code.

{% highlight js %}

    export class Grid {
    
            constructor() {
			    this.dataManager = new ej.DataManager("http://mvc.syncfusion.com/Services/Northwnd.svc/Foods");
				this.pageSettings = { pageSize: 8 };
				this.groupSettings= { groupedColumns: ['ItemType'] };
			}
    }

{% endhighlight %}


![](Getting-started_images/Getting-started_img6.png)



## Add Summaries

[`Summaries`](http://helpjs.syncfusion.com/js/grid/summary) can be added by setting the `e-show-summary` to true and adding required summary rows and columns in the `e-summary-rows` property. For demonstration, Stock column's sum value is displayed as summary.


{% highlight html %}

    <template>
    <div>
        <ej-grid e-data-source.bind="dataManager" e-allow-paging=true e-page-settings.bind="pageSettings" e-allow-grouping=true e-group-settings.bind="groupSettings" e-show-summary=true e-summary-rows.bind="summaryRows">
            
        </ej-grid>
    </div>
    </template>

{% endhighlight %}	

Configure the `e-summary-rows` bind value `this.summaryRows` in Aurelia view-model as shown in the following code.

{% highlight js %}

    export class Grid {
    
            constructor() {
			    this.dataManager = new ej.DataManager("http://mvc.syncfusion.com/Services/Northwnd.svc/Foods");
				this.pageSettings = { pageSize: 8 };
				this.groupSettings = { groupedColumns: ['ItemType'] };
				this.summaryRows = [
				     {
                  	     title: "Sum",
                  	     summaryColumns: [{ summaryType: ej.Grid.SummaryType.Sum, displayColumn: "Stock", dataMember: "Stock" }]
              	     }
				];
			}
    }

{% endhighlight %}

![](Getting-started_images/Getting-started_img7.png)