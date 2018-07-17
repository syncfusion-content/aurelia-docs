---
layout: post
title: Getting-Started
description: getting started
platform: Aurelia
control: Gantt
documentation: ug
---

# Getting Started

This section explains briefly about how to create a Gantt chart in your application with Aurelia.

## Create your first Gantt in JavaScript

To get started Syncfusion Aurelia application refer [`this`](https://help.syncfusion.com/aurelia/overview) page for basic control integration and script references.

In this tutorial, you can learn how to create a simple Gantt chart, add tasks or subtasks, and set relationship between tasks during the design phase of a software project. The following screenshot displays the desired output after completing this tutorial,

![](Getting-Started_images/Getting-Started_img4.png)

## Adding script references

* Create Gantt folder inside src/samples/ location.
* Create gantt.html file inside src/samples/Gantt folder and use the below code example to render the Gantt component.

Create an HTML file and add the following template to the HTML file.

{% highlight html %}

    <!DOCTYPE html>

    <html xmlns="http://www.w3.org/1999/xhtml">

    <head>

        <title>Getting Started with Gantt Control for Aurelia</title>

        <!-- style sheet for default theme(flat azure) -->
        <link href="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />

        <!--scripts-->
        <script src="http://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js"></script>

        <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js"></script>

        <script src="http://cdn.syncfusion.com/js/assets/external/jquery.globalize.min.js"></script>

        <script src="http://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js"></script>

        <script src="http://cdn.syncfusion.com/{{ site.releaseversion }}/js/web/ej.web.all.min.js "></script>

    </head>

    <body>
        <!--Add  Gantt control here-->
    </body>

    </html>

{% endhighlight %}

## Initialize the Gantt with data source

{% highlight javascript %}

   export class DefaultFuntionalities {
    constructor() {
        this.ProjectData = [{
            taskID: 1,
            taskName: 'Project Schedule',
            startDate: '02/03/2014',
            endDate: '03/07/2014',
            subtasks: [{
                    taskID: 2,
                    taskName: 'Planning',
                    startDate: '02/03/2014',
                    endDate: '02/07/2014',
                }
                //...
            ]
        }]
    }
}

{% endhighlight %}

Initialize the Gantt with data source created in the last step.

{% highlight html %}

<template>
    <div>
        <ej-gantt id="Gantt"
                  e-data-source.bind="ProjectData" 
                  e-task-id-mapping="taskID" 
                  e-task-name-mapping="taskName"
                  e-start-date-mapping="startDate" 
                  e-tree-column-index="1" 
                  e-child-mapping="subtasks"
                  e-progress-mapping="progress" 
                  e-end-date-mapping="endDate">
        </ej-gantt>
    </div>
   
</template>

{% endhighlight %}

A Gantt chart is created as shown in the following screen shot.

![](Getting-Started_images/Getting-Started_img5.png)

## Enable Toolbar

Gantt control contains toolbar options to edit, search, expand or collapse all records, indent, outdent, delete, and add a task. You can enable toolbar using the [`e-toolbar-settings`](http://help.syncfusion.com/js/api/ejgantt#members:toolbarsettings "toolbarSettings") property.

{% highlight javascript %}

<template>
    <div>
        <ej-gantt id="Gantt"
            e-toolbar-settings.bind="toolbarSettings"
            e-edit-settings.bind="editSettings"
            //...        >
        </ej-gantt>
    </div>
   
</template>

{% endhighlight %}

{% highlight javascript %}

export class DefaultFuntionalities {
    constructor() {
        this.toolbarSettings = {
            showToolbar: true,
            toolbarItems: [
                ej.Gantt.ToolbarItems.Add,
                ej.Gantt.ToolbarItems.Edit,
                ej.Gantt.ToolbarItems.Delete,
                ej.Gantt.ToolbarItems.Update,
                ej.Gantt.ToolbarItems.Cancel,
                ej.Gantt.ToolbarItems.Indent,
                ej.Gantt.ToolbarItems.Outdent,
                ej.Gantt.ToolbarItems.ExpandAll,
                ej.Gantt.ToolbarItems.CollapseAll
            ]
        };
        this.editSettings = {
            allowEditing: true,
            allowAdding: true,
            allowDeleting: true,
            allowIndent: true,
            editMode: 'cellEditing'
        };
    }
}

{% endhighlight %}

The following screen shot displays a Tool bar in Gantt chart control:

![](Getting-Started_images/Getting-Started_img6.png)

N>  Add, edit, delete, indent and outdent options are enabled when enabling the allowEditing, allowAdding, allowDelete, allowIndent and allowOutdent properties in the edit Options.

## Enable Sorting

The Gantt control has sorting functionality to arrange the tasks in ascending or descending order based on a particular column.

### Multicolumn Sorting

Enable the multicolumn sorting in Gantt by setting [`e-allow-multi-sorting`](http://help.syncfusion.com/js/api/ejgantt#members:allowmultisorting "allowMultiSorting") as `true`. You can sort multiple columns in Gantt, by selecting the desired column header while holding the `CTRL` key.

{% highlight javascript %}

 <template>
    <div>
        <ej-gantt id="Gantt"
            e-allow-sorting="true"
            e-allow-multi-sorting="true"
            //...        >
        </ej-gantt>
    </div>   
</template>

{% endhighlight %}

## Enable Editing

You can enable editing using [`e-edit-settings`](http://help.syncfusion.com/js/api/ejgantt#members:editsettings "editSettings") and [`e-allow-gantt-chart-editing`](http://help.syncfusion.com/js/api/ejgantt#members:allowganttchartediting "allowGanttChartEditing") options.

### Cell Editing

Modify the task details through the grid cell editing by setting the [`e-edit-mode`](http://help.syncfusion.com/js/api/ejgantt#members:editsettings-editmode "editSettings.editMode") as [`e-cell-editing`](http://help.syncfusion.com/js/api/ejgantt#members:editsettings-editmode "cellEditing").

### Normal Editing

Modify the task details through the edit dialog by setting the [`e-edit-mode`](http://help.syncfusion.com/js/api/ejgantt#members:editsettings-editmode "editSettings.editMode") as [`e-normal`](http://help.syncfusion.com/js/api/ejgantt#members:editsettings-editmode "normal").

### Taskbar Editing

Modify the task details through user interaction such as resizing and dragging the taskbar.

### Predecessor Editing

Modify the predecessor details of a task using mouse interactions by setting [`e-allow-gantt-chart-editing`](http://help.syncfusion.com/js/api/ejgantt#members:allowganttchartediting "allowGanttChartEditing") as `true` and setting the value for `e-predecessor-mapping` property.

{% highlight javascript %}

 <template>
    <div>
        <ej-gantt id="Gantt"
            e-allow-gantt-chart-editing="true"
            e-predecessor-mapping="predecessor"
            e-edit-settings.bind="editSettings"
            //...        >
        </ej-gantt>
    </div>   
</template>

{% endhighlight %}

{% highlight javascript %}

export class DefaultFuntionalities {
    constructor() {
        this.editSettings = {
            allowEditing: true,
            allowAdding: true,
            allowDeleting: true,
            allowIndent: true,
            editMode: 'cellEditing'
        };
    }
}

{% endhighlight %}

The following screen shot displays a Gantt chart control with Enable Editing options.

![](Getting-Started_images/Getting-Started_img7.png)

N>  Both cellEditing and  normal  editing operations are performed through double-click action.

## Enable Context Menu

You can enable the context menu in Gantt, by setting the [`e-enable-context-menu`](http://help.syncfusion.com/js/api/ejgantt#members:enablecontextmenu "enableContextMenu") as `true`.

{% highlight javascript %}

<template>
    <div>
        <ej-gantt id="Gantt"
           e-enable-context-menu="true"
           //...        >
        </ej-gantt>
    </div>   
</template>

{% endhighlight %}

The following screen shot displays Gantt chart in which Context menu option is enabled:

![](Getting-Started_images/Getting-Started_img8.png)

## Enable Column Menu

You can enable the column menu in Gantt, by setting the [`e-show-column-chooser`](http://help.syncfusion.com/js/api/ejgantt#members:showcolumnchooser "showColumnChooser") as `true`.

{% highlight javascript %}

<template>
    <div>
        <ej-gantt id="Gantt"
           e-show-column-chooser="true"
           //...        >
        </ej-gantt>
    </div>   
</template>

{% endhighlight %}

The following screen shot displays Gantt chart in which column chooser option is enabled:

![](Getting-Started_images/Getting-Started_img11.png)

## Provide tasks relationship

In Gantt, you have the predecessor support to show the relationship between two different tasks.

* **Start to Start (SS)** - You cannot start a task until the other task also starts.
* **Start to Finish (SF)** - You cannot finish a task until the other task finishes.
* **Finish to Start (FS)** - You cannot start a task until the other task completes.
* **Finish to Finish (FF)** - You cannot finish a task until the other task completes.

You can show the relationship in tasks, by using the [`e-predecessor-mapping`](http://help.syncfusion.com/js/api/ejgantt#members:predecessormapping "predecessorsMapping")

, as shown in the following code example.

{% highlight javascript %}

<template>
    <div>
        <ej-gantt id="Gantt"
           e-predecessor-mapping="predecessor"
           //...        
           >
        </ej-gantt>
    </div>   
</template>

{% endhighlight %}

The following screenshot displays the relationship between tasks.

![](Getting-Started_images/Getting-Started_img9.png)

## Provide Resources

In Gantt control, you can display and assign the resource for each task. Create a collection of `JSON` object, which contains id and name of the resource and assign it to [`e-resources`](http://help.syncfusion.com/js/api/ejgantt#members:resources "resources") property. Then, specify the field name for id and name of the resource in the resource collection to [`e-resource-id-mapping`](http://help.syncfusion.com/js/api/ejgantt#members:resourceidmapping "e-resource-id-mapping") and [`e-resource-name-mapping`](http://help.syncfusion.com/js/api/ejgantt#members:resourcenamemapping "resourceNameMapping") options. The name of the field, which contains the actual resources assigned for a particular task in the `e-data-source` is specified using [`e-resource-info-mapping`](http://help.syncfusion.com/js/api/ejgantt#members:resourceinfomapping "resourceInfoMapping").

1.Create the resource collection to be displayed in ejGantt

{% highlight javascript %}

export class DefaultFuntionalities {
    constructor() {
        this.projectResources =[{
        resourceId: 1,
        resourceName: "Project Manager"
    },{
        resourceId: 2,
        resourceName: "Software Analyst"
    },{
        resourceId: 3,
        resourceName: "Developer"
    },{
        resourceId: 4,
        resourceName: "Testing Engineer"
    }];
    }
}

{% endhighlight %}

2.Initialize the Gantt with resources created in last step. 

{% highlight javascript %}

<template>
    <div>
        <ej-gantt id="Gantt"
            e-resource-info-mapping="resourceId"
            e-resource-name-mapping="resourceName"
            e-resource-id-mapping="resourceId"
            e-resources.bind="projectResources"
            //...        >
        </ej-gantt>
    </div>   
</template>

{% endhighlight %}

The following screenshot displays resource allocation for tasks in Gantt chart.

![](Getting-Started_images/Getting-Started_img10.png)

By following these steps, you have learned how to provide data source to Gantt chart, how to configure Gantt to set task relationships, assign resources for each task, and add toolbar with necessary buttons.

## Highlight Weekend

In Gantt, you can on or off weekends high lighting by setting the [`e-highlight-week-ends`](/api/js/ejgantt#members:highlightweekends "highlightWeekEnds")

 as `true` or `false`.

{% highlight javascript %}

 <template>
    <div>
        <ej-gantt id="Gantt"
            e-highlight-week-ends="true"
            //...        >
        </ej-gantt>
    </div>   
</template>
{% endhighlight %}

The following screen shot displays Gantt chart in which highlight weekends is disabled:

![](Getting-Started_images/Getting-Started_img12.png)
