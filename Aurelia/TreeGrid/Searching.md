---
layout: post
title: Searching | TreeGrid
description: Searching
platform: Aurelia
control: TreeGrid
documentation: ug
---

## Searching

The TreeGrid control has an option to search its content using toolbar search box. The toolbar search box can be enabled by using the `toolbarSettings.toolbarItems` property. The following code example explains how to integrate search textbox in toolbar.

{% highlight html %}
<template>
    <div style="padding:10px;">
        <ej-tree-grid 
            e-widget.bind="TreeGrid"
            id="TreeGrid"
            e-toolbar-settings.bind="toolbarSettings"
            >
        </ej-tree-grid>
    </div>
</template>
{% endhighlight %}

{% highlight js %}
export class DefaultSample {
    constructor() {
        this.toolbarSettings = {
            showToolbar: true,
            toolbarItems: [
                ej.TreeGrid.ToolbarItems.Search
            ]
        };
    }
}
{% endhighlight %}

The below screenshot shows TreeGrid search with `plan` key word.
![](Searching_images/Searching_default.png)