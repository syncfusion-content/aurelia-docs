---
layout: post
title:  Group
description: group
documentation: ug
platform: Aurelia
keywords: group,ribbon group
---

# Group

`Group` is a collection of logical content groups that are combined under related Tab. Each group can be defined using content groups or custom content.

## Adding Tab Groups

Group items can be added to Tabs by specifying `text` and corresponding `content` to be displayed. The content of group can be specified as either with `content` collection, `contentID` or `customContent`.

### Adding Content

Add content to Group item which is based on `type` of content specified. The available types are `button`, `splitButton`, `toggleButton`,`gallery`, and `dropDownList`.

Groups and defaults settings can be added with the `content`.

#### _Defaults_

The `height`, `width`, `type`, `isBig` property to the controls in the `group` can be specified commonly.
The `height` & `width` applicable to button, split button, dropdown list ,Toggle button controls and `isBig` applicable to only button controls ( button, split , toggle)

#### _Adding Content Groups_

Controls such as button, split button, dropdown list, toggle button, gallery in the subgroup of the Ribbon tab can be rendered. All of these can be customized using its corresponding settings property such as `buttonSettings`, `dropdownSettings`, etc.

Custom controls or items (such as table, div etc.) can be added when the `type` set as `custom`. `defaults` control settings of group can be specified for an `individual group` instead of specifying them to groups collection commonly.

`Tooltip` and `Custom Tooltip` can be specified for each group controls.

{% highlight html %}
	
    <template>
    <div>
        <ej-ribbon id="default" e-width="100%" e-application-tab.bind="ApplicationTab" e-tabs.bind="Tabs">
        </ej-ribbon>
    </div>
    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div>
                    <div id="defaultRibbon"></div>
                </div>
                <ul id="ribbonmenu">
                    <li>
                        <a>FILE</a>
                        <ul>
                            <li><a>New</a></li>
                            <li><a>Open</a></li>
                            <li><a>Save</a></li>
                            <li><a>Save As</a></li>
                            <li><a>Print</a></li>
                        </ul>
                    </li>
                </ul>
                <ul id="pasteSplit">
                    <li>
                        Paste
                    </li>
                    <li>
                        Paste Special
                    </li>
                </ul>
            </div>
        </div>
    </template>

{% endhighlight %}

{% highlight html %}

    export class default {
    constructor() {
        this.ApplicationTab = { type: ej.Ribbon.ApplicationTabType.Menu, menuItemID: 'ribbonmenu', menuSettings: {  openOnClick: false } };
        this.Tabs = [{ id: 'home', text: 'HOME', groups: [{ text: 'Clipboard', alignType: ej.Ribbon.AlignType.Columns, content: [{ groups: [{ id: 'paste', text: 'paste', toolTip: 'Paste', quickAccessMode: ej.Ribbon.QuickAccessMode.ToolBar, splitButtonSettings: { contentType: ej.ContentType.ImageOnly, prefixIcon: 'e-icon e-ribbon e-ribbonpaste', targetID: 'pasteSplit', buttonMode: 'dropdown', click: 'executeAction'}}], defaults: { type: ej.Ribbon.Type.SplitButton, width: 50, height: 70}}]},{
            text: "Font",
            //group aligntype as columns
            alignType: ej.Ribbon.alignType.columns,
            content: [{
                groups: [{
                    // contentgroup with toggle button settings
                    id: "cut",
                    toggleButtonSettings: {
                        defaultText: "Cut",
                        activeText: "Cut Over"
                    }
                }, {
                    id: "copy",
                    toggleButtonSettings: {
                        defaultText: "Copy",
                        activeText: "Copy Over"
                    }
                }],
                // defaults settings of above group’s control
                defaults: {
                    width: 75,
                    height: 30,
                    type: ej.Ribbon.type.toggleButton
                }
            }],
        }]}];
    }
    }

{% endhighlight %}

![](Group_images/Group_img1.png)

#### _Enable Separator_ 

Separates the control from the next control in the group when group `alignType` is `row`. Set “true” to `enableSeparator`.

{% highlight html %}

	<template>
    <div>
        <ej-ribbon id="default" e-width="100%" e-application-tab.bind="ApplicationTab" e-tabs.bind="Tabs">
        </ej-ribbon>
    </div>
    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div>
                    <div id="defaultRibbon"></div>
                </div>
                <ul id="ribbonmenu">
                    <li>
                        <a>FILE</a>
                        <ul>
                            <li><a>New</a></li>
                            <li><a>Open</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </template>

{% endhighlight %}

{% highlight html %}

    export class default {
    constructor() {
        this.ApplicationTab = { type: ej.Ribbon.ApplicationTabType.Menu, menuItemID: 'ribbonmenu', menuSettings: {  openOnClick: false } };
        this.Tabs = [{
            id: "home",
            text: "HOME",
            groups: [{
                text: "New",
                // group alignType is "row”
                alignType: ej.Ribbon.alignType.rows,
                content: [{
                    groups: [{
                        id: "new",
                        text: "New",
                        toolTip: "New",

                        // separates New and Font controls
                        enableSeparator: true,
                        buttonSettings: {
                            width: 100,
                        }
                    }, {
                        id: "font",
                        text: "Font",
                        toolTip: "Font",
                        buttonSettings: {
                            width: 150,
                        }
                    }],
                    defaults: {
                        type: ej.Ribbon.type.button,
                        height: 70
                    }
                }]
            }]
        }];
    }
    }

{% endhighlight %}

![](Group_images/Group_img2.png)

### Adding Custom Content 

Set group `type` as `custom` to add custom items such as div, table and custom controls. With type as custom, content can be added in two ways as specified below.

*	HTML contents can be directly added into the groups as string content using `customContent` property
*	Custom template id can be specified to render those specific custom template using `contentID` property

{% highlight html %}

	 <template>
    <div>
        <ej-ribbon id="default" e-width="100%" e-application-tab.bind="ApplicationTab" e-tabs.bind="Tabs">
        </ej-ribbon>
    </div>
    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div>
                    <div id="defaultRibbon"></div>
                </div>
                <button id="btn">Using Content ID</button>
                <ul id="ribbonmenu">
                    <li>
                        <a>FILE</a>
                        <ul>
                            <li><a>New</a></li>
                            <li><a>Open</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
    </template>

{% endhighlight %}

{% highlight html %}

    export class default {
    constructor() {
        this.ApplicationTab = { type: ej.Ribbon.ApplicationTabType.Menu, menuItemID: 'ribbonmenu', menuSettings: {  openOnClick: false } };
        this.Tabs = [{
            id: "home",
            text: "HOME",
            groups: [{
                text: "New",
                type: "custom",
                customContent: "<button id='customContent'>Using Custom Content</button>"
            }, {
                text: "Data",
                type: "custom",
                contentID: "btn"
            }]
        }];
    }
    }

{% endhighlight %}

![](Group_images/Group_img3.png)

## Group Expander

Set `enableGroupExpander` as true to show Group Expander for each group in Tab. These expanders can be customized using `groupExpand` event, such as to show popup dialog.

{% highlight html %}

     <template>
    <div>
        <ej-ribbon id="default" e-width="100%" e-application-tab.bind="ApplicationTab" e-tabs.bind="Tabs">
        </ej-ribbon>
    </div>
    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div>
                    <div id="defaultRibbon"></div>
                </div>
                <button id="btn">Home button</button>
                <ul id="ribbonmenu">
                    <li>
                        <a>FILE</a>
                        <ul>
                            <li><a>New</a></li>
                            <li><a>Open</a></li>
                        </ul>
                    </li>
                </ul>
            </div>
        </div>
     </template>

{% endhighlight %}

{% highlight html %}

    export class default {
    constructor() {
        this.ApplicationTab = { type: ej.Ribbon.ApplicationTabType.Menu, menuItemID: 'ribbonmenu', menuSettings: {  openOnClick: false } };
        this.Tabs = [{
            id: "home",
            text: "HOME",
            groups: [{
                text: "New",
                alignType: ej.Ribbon.alignType.rows,
                type: "custom",
                // group expander enabled
                enableGroupExpander: true,
                contentID: "btn"
            }]
        }];
    }
    }

{% endhighlight %}

![](Group_images/Group_img4.png)
