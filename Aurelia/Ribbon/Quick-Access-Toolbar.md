---
layout: post
title:  Quick Access Toolbar
description: quick access toolbar
documentation: ug
platform: Aurelia
keywords: quick access toolbar,ribbon quick access toolbar
---

# Quick Access Toolbar

Quick Access Toolbar provides the shortcuts to the most commonly used commands by placing the controls at the Quick Access Toolbar section. It can be placed at the top or bottom of the Ribbon.

Set `showQAT` as true to enable Quick Access Toolbar in Ribbon. It supports the Button, Split Button, Toggle Button controls. The `quickAccessMode` is used to change the controls state in Quick Access Toolbar through options as `toolbar`,`menu` and `none`. Default value is `none` and QAT toolbar is created with specified controls added in Toolbar.

The `toolbar` option used to set controls visibility in Quick Access Toolbar.The `menu` option shows the controls in Quick Access Menu and does not show controls in Quick Access Toolbar.

Once the controls are visible in Toolbar , then controls state will be set as ticked in Quick Access Menu and vice versa.  

The client side event for Quick Access Toolbar menu click is `qatMenuItemClick` and it will be triggered with QAT menu item click.

`More Commands` command provides with Quick Access Menu. This can be customized using `qatMenuItemClick` event, such as to show popup dialog. 

{% highlight html %}

	<template>
    <div>
        <ej-ribbon id="default" e-width="30%" e-application-tab.bind="ApplicationTab" e-tabs.bind="Tabs" e-show-q-a-t="true">
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
                <style>
                    .e-ribbon .e-rbnquickaccessbar .e-ribbonpaste:before {
                        font-size: 27px;
                        left: -5px;
                        top: -6px;
                    }
                    .e-ribbon .e-ribbonpaste:before {
                        font-family: 'ej-ribbonfont';
                        content: "\e169";
                        font-size: 36px;
                        position: relative;
                        left: -9px;
                        top: -4px;
                    }
                    .e-ribbon .e-ribbonitalic:before, .e-ribbon .bold:before {
                        font-family: 'ej-ribbonfont';
                        font-size: 16px;
                        left: -1px;
                        position: relative;
                        top: -1px;
                    }
                    .e-ribbon .e-ribbonitalic:before, .e-ribbon .bold:before {
                        content: "\e163";
                    }

                    .e-ribbon .bold:before {
                        content: "\e15a";
                    }
                    .e-ribbon .e-rbnquickaccessbar .e-undo::before {
                        font-size: 18px;
                        line-height: 12px;
                        text-indent: -3px;
                    }
                </style>
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
                text: "SplitButton",
                alignType: ej.Ribbon.alignType.columns,
                content: [{
                    groups: [{
                        id: "paste",
                        text: "paste",
                        toolTip: "Paste",
                        type: ej.Ribbon.type.splitButton,
                        quickAccessMode: ej.Ribbon.quickAccessMode.toolBar,
                        splitButtonSettings: {
                            contentType: ej.ContentType.ImageOnly,
                            targetID: "split",
                            prefixIcon: "e-ribbon e-icon e-ribbonpaste",
                            buttonMode: "dropdown",
                            arrowPosition: "bottom"
                        }
                    }],
                    defaults: {
                        type: ej.Ribbon.type.splitButton,
                        width: 50,
                        height: 70
                    }
                }]
            }, {
                text: "Button",
                alignType: ej.Ribbon.alignType.rows,
                content: [{
                    groups: [{ id: 'italic', toolTip: 'Italic', type: ej.Ribbon.Type.ToggleButton, quickAccessMode: ej.Ribbon.QuickAccessMode.ToolBar, toggleButtonSettings: { contentType: ej.ContentType.ImageOnly, defaultText: 'Italic', activeText: 'Italic', defaultPrefixIcon: 'e-icon e-ribbon e-ribbonitalic', activePrefixIcon: 'e-icon e-ribbon e-ribbonitalic', click: 'executeAction'}}]
                }]
            }, {
                text: "Toggle",
                alignType: ej.Ribbon.alignType.columns,
                content: [{
                    groups: [{
                        id: "bold",
                        toolTip: "Bold",
                        type: ej.Ribbon.type.toggleButton,
                        quickAccessMode: ej.Ribbon.quickAccessMode.toolBar,
                        toggleButtonSettings: {
                            contentType: ej.ContentType.ImageOnly,
                            defaultText: "Bold",
                            activeText: "Bold",
                            defaultPrefixIcon: "e-ribbon bold",
                            activePrefixIcon: "e-ribbon e-icon bold"
                        }
                    }],
	
                }]
            }]
        }];
    }
    }
	 
{% endhighlight %}

![](Quick-Access-Toolbar_images/Quick-Access-Toolbar_img1.png)
