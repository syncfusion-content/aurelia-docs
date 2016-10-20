---
title: Getting Started for Aurelia Kanban
description: Getting-Started
platform: Aurelia
control: Kanban
documentation: Ug 
---

# Getting Started

Before we start with the Kanban, please refer [this page](https://help.syncfusion.com/aurelia/overview#getting-started) page for general information regarding integrating Syncfusion widget’s.

For quick start, we already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

    > git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
    > cd syncfusion-template-repository
    > npm install
    > jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia Kanban component.

    Create kanban folder inside src/samples/ location.
    Create kanban.html file inside src/samples/kanban folder and use the below code example to render the Kanban component.    
    Properties can be defined with `e-` prefix and long text properties needs to separated by `-`. E.g. ( `e-kanban` , `e-header-text`).

{% highlight html %}

    <template>
        <div>
            <ej-kanban id="Kanban">
                <ej-kanban-column  e-header-text="Backlog"></ej-kanban-column>
                <ej-kanban-column  e-header-text="In Progress"></ej-kanban-column>
                <ej-kanban-column  e-header-text="Testing"></ej-kanban-column>
                <ej-kanban-column  e-header-text="Done"></ej-kanban-column>
            </ej-kanban>
        </div>
    </template>

{% endhighlight %}

* Create `kanban.js` file inside `src/samples/kanban` folder with below code snippet.

{% highlight html %}

    export class Kanban {
        constructor() {
        }
    }

{% endhighlight %}

![](Getting-Started_images/Getting_Started_img1.png)

## Data Binding

`Data binding` in the Kanban is achieved by using the `ej.DataManager` that supports both RESTful JSON data services binding and local JSON array binding. 

To set the data source to Kanban, the `e-data-source.bind` property is assigned with the instance of the `this.KanbanData` which is specified in constructor.


{% highlight html %}

    <template>
    <div>
        <ej-kanban id="Kanban" e-data-source.bind="KanbanData">
            <ej-kanban-column e-header-text="Backlog"></ej-kanban-column>
            <ej-kanban-column e-header-text="In Progress"></ej-kanban-column>
            <ej-kanban-column e-header-text="Testing"></ej-kanban-column>
            <ej-kanban-column e-header-text="Done"></ej-kanban-column>

        </ej-kanban>
    </div>
    </template>

{% endhighlight %}

{% highlight html %}

    export class Kanban {
        constructor() {
            this.KanbanData = KanbanData;    
        }
    }

{% endhighlight %}

![](Getting-Started_images/Getting_Started_img2.png)

## Mapping Values

In order to display cards in Kanban control, you need to map the database fields to Kanban cards and columns. The required mapping field are listed as follows

* `e-fields.bind` - Field values can be bind with `this.Fields` which is specified in constructor.
* `e-key-field` - Map the column name to use as `e-key` values to columns.
* `columns` -  Map the corresponding `e-key` values of `e-key-field` column to each columns
* `content` - Map the column name to use as content to cards which is specified `this.Fields` under constructor method.
* `primaryKey` - Map the column name to use as primary Key which is specified `this.Fields` under constructor method.


{% highlight html %}

    <template>
    <div>
        <ej-kanban id="Kanban" e-data-source.bind="KanbanData" e-key-field="Status" e-fields.bind="Field">
            <ej-kanban-column e-header-text="Backlog" e-key="Open"></ej-kanban-column>
            <ej-kanban-column e-header-text="In Progress" e-key="InProgress"></ej-kanban-column>
            <ej-kanban-column e-header-text="Testing" e-key="Testing"></ej-kanban-column>
            <ej-kanban-column e-header-text="Done" e-key="Close"></ej-kanban-column>
        </ej-kanban>
    </div>
    </template>

{% endhighlight %} 

{% highlight html %}
    
    export class Kanban {
        constructor() {
            this.KanbanData = KanbanData;
            this.Field = { primaryKey: 'Id', content: 'Summary'};
        }
    }

{% endhighlight %} 

![](Getting-Started_images/Getting_Started_img3.png)

N>  `primaryKey` field is mandatory for “Drag and Drop” ,”Selection” and “Editing” Features.

## Enable Swimlane

`Swimlane` can be enabled by mapping the `swimlaneKey` to appropriate column name in `dataSource`. This enables the grouping of the cards based on the mapped column values.


{% highlight html %}

    <template>
    <div>
        <ej-kanban id="Kanban" e-data-source.bind="KanbanData" e-key-field="Status" e-fields.bind="Field">
            <ej-kanban-column e-header-text="Backlog" e-key="Open"></ej-kanban-column>
            <ej-kanban-column e-header-text="In Progress" e-key="InProgress"></ej-kanban-column>
            <ej-kanban-column e-header-text="Testing" e-key="Testing"></ej-kanban-column>
            <ej-kanban-column e-header-text="Done" e-key="Close"></ej-kanban-column>

        </ej-kanban>
    </div>
    </template>

{% endhighlight %} 

{% highlight html %}

    import './KanbanJsonData';
    export class Kanban {
        constructor() {
            this.KanbanData = KanbanData;
            this.Field = { primaryKey: 'Id', content: 'Summary', swimlaneKey: 'Assignee'};
        }
    }

{% endhighlight %} 

![](Getting-Started_images/Getting_Started_img4.png)

## Adding Filters

Filters allows to filter the collection of cards from `dataSource` which meets the predefined `query` in the filters collection. To enable filtering, define `filterSettings` collection with display `text` and `ej.Query`.

Filter settings can be defined under constructor method as array of objects with the name `this.Filter`.

{% highlight html %}

    <template>
    <div>
        <ej-kanban id="Kanban" e-data-source.bind="KanbanData" e-key-field="Status" e-fields.bind="Field" e-filter-settings.bind="Filter">
            <ej-kanban-column e-header-text="Backlog" e-key="Open"></ej-kanban-column>
            <ej-kanban-column e-header-text="In Progress" e-key="InProgress"></ej-kanban-column>
            <ej-kanban-column e-header-text="Testing" e-key="Testing"></ej-kanban-column>
            <ej-kanban-column e-header-text="Done" e-key="Close"></ej-kanban-column>

        </ej-kanban>
    </div>
    </template>

{% endhighlight %} 

{% highlight html %}

    export class Kanban {
        constructor() {
            this.KanbanData = KanbanData;
            this.Field = { primaryKey: 'Id', content: 'Summary',swimlaneKey: 'Assignee'};
            this.Filter = [{ text: 'Janet Issues', query: new ej.Query().where('Assignee', 'equal', 'Janet Leverling'), description: 'Displays issues which matches the assignee as Janet Leverling' }, { text: 'Testing Issues', query: new ej.Query().where('Status', 'equal', 'Testing'), description: 'Display the issues of Testing'}];
        }
    }

{% endhighlight %} 

![](Getting-Started_images/Getting_Started_img5.png)
