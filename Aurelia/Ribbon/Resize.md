---
layout: post
title:  Resize
description: resize
documentation: ug
platform: Aurelia
keywords: resize,ribbon resize,responsive
---

# Resize 

Ribbon control dynamically resizes to display possible number of controls in the optimal layout as the application window size changes.

As the window is narrowed, controls in the Ribbon will be combined as group button with dropdown arrow, in which controls can be expanded with dropdown arrow.

## Tablet Layout 

Set `isResponsive` as true to enable responsive layout in Ribbon.If client width is above  420px or control content exceeds the page then, the ribbon will render in Tablet mode.

{% highlight html %}

    <template>  
    <div>
     <ej-ribbon id="Customtooltip" e-width="30%" e-is-responsive="true" e-application-tab.bind="ApplicationTab" e-tabs.bind="Tabs">
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
	  </template>

{% endhighlight %}

{% highlight html %}
 
    export class CustomToolTip {
    constructor() {
    this.ApplicationTab = { type: ej.Ribbon.ApplicationTabType.Menu, menuItemID: 'ribbonmenu', menuSettings: {  openOnClick: false } };
    this.Tabs = [{
                    id: "home",
                    text: "HOME",
                    groups: [{
                        text: "Clipboard",
                        content: [{
                            groups: [{
                                id: "cut",
                                text: "Cut"
                            }, {
                                id: "copy",
                                text: "Copy"
                            }],
                            defaults: {
                                height: 70,
                                width: 40
                            }
                        }]
                    }, {
                        text: "Font",
                        content: [{
                            groups: [{
                                id: "bold",
                                text: "Bold"
                            }, {
                                id: "italic",
                                text: "Italic"
                            }],
                            defaults: {
                                height: 70,
                                width: 40
                            }
                        }]
                    }, {
                        text: "Align",
                        content: [{
                            groups: [{
                                id: "left",
                                text: " Left"
                            }, {
                                id: "right",
                                text: "Right"
                            }],
                            defaults: {
                                height: 70,
                                width: 40
                            }
                        }]
                    }]
                }];
     }
     }
     
{% endhighlight %}

![](Resize_images/Resize_img1.png)

## Mobile Layout

If client width is less than 420px, the ribbon will render in mobile mode. In which, you can see that ribbon user interface is customized and redesigned for best view in small screens.
The customized features includes responsive tab & group rendering, backstage, gallery and button controls.

### Responsive Tab and group

Set `isResponsive` as true to enable responsive mode in Ribbon.
   
{% highlight html %}
    
    <template>
    <div>
        <ej-ribbon id="default" e-width="30%" e-is-responsive="true" e-application-tab.bind="ApplicationTab" e-tabs.bind="Tabs">
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
    </template>

{% endhighlight %}
   
{% highlight html %}

    export class default {
    constructor() {
        this.ApplicationTab = { type: ej.Ribbon.ApplicationTabType.Menu, menuItemID: 'ribbonmenu', menuSettings: {  openOnClick: false } };
        this.Tabs = [{
            id: "home", text: "HOME", groups: [
                 {
                     text: "Font", alignType: "rows", content: [{
                         groups: [{
                             id: "bold",
                             type: ej.Ribbon.Type.ToggleButton,
                             isMobileOnly: true,
                             toggleButtonSettings: {
                                 contentType: ej.ContentType.ImageOnly,
                                 defaultText: "Bold",
                                 activeText: "Bold",
                                 defaultPrefixIcon: "e-icon e-ribbon e-resbold",
                                 activePrefixIcon: "e-icon e-ribbon e-resbold",
                             }
                         },
                            {
                                id: "italic",
                                type: ej.Ribbon.Type.ToggleButton,
                                isMobileOnly: true,
                                toggleButtonSettings: {
                                    contentType: ej.ContentType.ImageOnly,
                                    defaultText: "Italic",
                                    activeText: "Italic",
                                    defaultPrefixIcon: "e-icon e-ribbon e-resitalic",
                                    activePrefixIcon: "e-icon e-ribbon e-resitalic",
                                    click: "executeAction"
                                }
                            },
                            {
                                id: "underline",
                                text: "Underline",
                                type: ej.Ribbon.Type.ToggleButton,
                                isMobileOnly: true,
                                toggleButtonSettings: {
                                    contentType: ej.ContentType.ImageOnly,
                                    defaultText: "Underline",
                                    activeText: "Underline",
                                    defaultPrefixIcon: "e-icon e-ribbon e-resunderline",
                                    activePrefixIcon: "e-icon e-ribbon e-resunderline",
                                }
                            },
                            {
                                id: "strikethrough",
                                text: "strikethrough",
                                isMobileOnly: true,
                                type: ej.Ribbon.Type.ToggleButton,
                                toggleButtonSettings: {
                                    contentType: ej.ContentType.ImageOnly,
                                    defaultText: "Strikethrough",
                                    activeText: "Strikethrough",
                                    defaultPrefixIcon: "e-icon e-ribbon strikethrough",
                                    activePrefixIcon: "e-icon e-ribbon strikethrough",
                                }
                            },
                            {
                                id: "superscript",
                                text: "superscript",
                                isMobileOnly: true,
                                buttonSettings: {
                                    contentType: ej.ContentType.ImageOnly,
                                    prefixIcon: "e-icon e-ribbon e-superscripticon",
                                }
                            }
                         ],
                         defaults: {
                             isBig: false
                         }
                     }]
                 },
            ]
        }];
    }
    }

{% endhighlight %}

![](Resize_images/responsive1.png)

{:caption}
Ribbon Responsive with tab content 

N> To make the Ribbon control to react as responsive in mobile devices, it is necessary to refer the additional `ej.responsive.css` file in the application.
