---
layout: post
title: Getting-Started
description: getting started
platform: Aurelia
control: TreeGrid
documentation: ug
---

# Getting Started
This section helps to understand the getting started of the Aurelia TreeGrid with the step-by-step instructions.

## Create your first TreeGrid in Aurelia

To get started Syncfusion Aurelia application refer [`this`](https://help.syncfusion.com/aurelia/overview) page for basic control integaration and script references.

The **Essential Aurelia TreeGrid** has been designed to represent and edit the hierarchical data. 

This section explains how to create a TreeGrid widget in your application with hierarchical data source and enable sorting and editing. The following screenshot displays the output.

![](/Getting-Started_images/Getting-Started_img1.png)

* Create TreeGrid folder inside src/samples/ location.
* Create treegrid.html file inside src/samples/TreeGrid folder and use the below code example to render the TreeGrid component.

1.Create HTML file and add the following necessery script and css files to the HTML file.

{% highlight html %}

    <!DOCTYPE html>
    <html xmlns="http://www.w3.org/1999/xhtml">
        <head>
            <meta name="viewport"content="width=device-width, initial-scale=1.0"/>
            <meta charset="utf-8" />
            <link href=" http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet"/>
            <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js"></script>
            <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js"></script>
            <script src="http://cdn.syncfusion.com/js/assets/external/jquery.globalize.min.js"></script>
            <script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js"></script>
            <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js" type="text/javascript"></script>
        </head>
        <body>
        <!--Add TreeGrid control here -->
        </body>
    </html>

{% endhighlight %}

2.Create the TreeGrid with the empty data source.

{% highlight html %}

<template>
    <div>
        <ej-tree-grid id="Treegrid"
        //...
        >
        </ej-tree-grid>
    </div>
   
</template>

{% endhighlight %}

To render the Aurelia TreeGrid using below code.

{% highlight javascript %}

export class DefaultSample {
  constructor() {
      //...
       }
}

{% endhighlight %}

![](/Getting-Started_images/Getting-Started_img2.png)

TreeGrid with empty datasource 
{:.caption}

3.Create data source for TreeGrid.

{% highlight javascript %}

export class DefaultSample {
  constructor() {
  this.ProjectData = [{
    taskID: 2,
    taskName: "Planning",
    startDate: "02/03/2014",
    endDate: "02/07/2014",
    duration: 10,
    progress: 56,
    subtasks: [{
        taskID: 3,
        taskName: "Plan timeline",
        startDate: "02/03/2014",
        endDate: "02/07/2014",
        duration: 5,
        progress: "100"
    }, {
        taskID: 4,
        taskName: "Plan budget",
        startDate: "02/03/2014",
        endDate: "02/07/2014",
        duration: 5,
        progress: "100"
    }, {
        taskID: 5,
        taskName: "Allocate resources",
        startDate: "02/03/2014",
        endDate: "02/07/2014",
        duration: 5,
        progress: "100"
    }, {
        taskID: 6,
        taskName: "Planning complete",
        startDate: "02/07/2014",
        endDate: "02/07/2014",
        duration: 0,
        progress: 40
    }]
}, {
    taskID: 7,
    taskName: "Design",
    startDate: "02/10/2014",
    endDate: "02/14/2014",
    duration: 10,
    progress: 76,
    subtasks: [{
        taskID: 8,
        taskName: "Software Specification",
        startDate: "02/10/2014",
        endDate: "02/12/2014",
        duration: 3,
        progress: "60"
    }, {
        taskID: 9,
        taskName: "Develop prototype",
        startDate: "02/10/2014",
        endDate: "02/12/2014",
        duration: 3,
        progress: "100"
    }, {
        taskID: 10,
        taskName: "Get approval from customer",
        startDate: "02/13/2014",
        endDate: "02/14/2014",
        duration: 2,
        progress: "100"
    }, {
        taskID: 11,
        taskName: "Design complete",
        startDate: "02/14/2014",
        endDate: "02/14/2014",
        duration: 0,
        predecessor: "10FF",
        progress: 65
    }]
}]
this.columns = [{ field: 'taskID', headerText: 'Task Id', width: '45'}, 
                { field: 'taskName', headerText: 'Task Name'},
                { field: 'startDate', headerText: 'Start Date'},
                { field: 'endDate', headerText: 'End Date'},
                { field: 'duration', headerText: 'Duration'},
                { field: 'progress', headerText: 'Progress'}
               ];
       }
}

{% endhighlight %}

4.Initialize the TreeGrid with data source created in last step.

{% highlight html %}

<template>
    <div>
        <ej-tree-grid id="Treegrid"
                  e-data-source.bind="ProjectData"                 
                  e-child-mapping="subtasks"
                  e-tree-column-index="1"
                  e-columns.bind="columns">
        </ej-tree-grid>
    </div>   
</template>

{% endhighlight %}

TreeGrid widget is displayed as the output in the following screenshot.

![](/Getting-Started_images/Getting-Started_img3.png)

### Enable Sorting

The TreeGrid control has sorting functionality, to arrange the data in ascending or descending order based on a particular column.

#### Multicolumn Sorting

Enable the multicolumn sorting in TreeGrid by setting [`e-allow-multi-sorting`](http://help.syncfusion.com/js/api/ejtreegrid#allowmultisorting "allowMultiSorting") as `true`. You can sort multiple columns in TreeGrid, by selecting the desired column header while holding the `Ctrl` key.

{% highlight html %}

<template>
    <div>
        <ej-tree-grid id="Treegrid"
        //...
         e-allow-sorting="true"
         e-allow-multi-sorting="true"
        >
        </ej-tree-grid>
    </div>   
</template>

{% endhighlight %}

![](/Getting-Started_images/Getting-Started_img4.png)

### Enable Editing

You can enable Editing in TreeGrid by using the [`e-edit-settings`](http://help.syncfusion.com/js/api/ejtreegrid#editsettings "editSettings") property as follows.

{% highlight html %}

<template>
    <div>
        <ej-tree-grid id="Treegrid"
        //...
         e-edit-settings.bind="editsettings"
        >
        </ej-tree-grid>
    </div>
   
</template>

{% endhighlight %}

{% highlight javascript %}

export class DefaultSample {
    constructor() {
        this.editsettings = {
            allowAdding: true,
            allowEditing: true,
            allowDeleting: true,
            editMode: 'cellEditing',
            rowPosition: 'belowSelectedRow'
        };
    }
}

{% endhighlight %}

And also, the following editors are provided for editing support in TreeGrid control.

* string
* boolean
* numeric
* dropdown
* datepicker
* datetimepicker

You can set the editor type for a particular column as follows.

{% highlight html %}

<template>
    <div>
        <ej-tree-grid id="Treegrid"
        //...
          e-columns.bind="columns">
        </ej-tree-grid>
    </div>   
</template>

{% endhighlight %}

{% highlight javascript %}

export class DefaultSample {
    constructor() {
        this.columns =  [
                    { field: 'taskID', headerText: 'Task Id', width: '45', editType: 'numericedit' },
                    { field: 'taskName', headerText: 'Task Name', editType: 'stringedit' },
                    { field: 'startDate', headerText: 'Start Date', editType: 'datepicker' },
                    { field: 'endDate', headerText: 'End Date', editType: 'datepicker'},
                    { field: 'duration', headerText: 'Duration', editType: 'numericedit' },
                    { field: 'progress', headerText: 'Progress', editType: 'numericedit' }
        ];
    }
}

{% endhighlight %}

The output of the DateTimePicker editor in TreeGrid control is as follows.

![](/Getting-Started_images/Getting-Started_img5.png)

