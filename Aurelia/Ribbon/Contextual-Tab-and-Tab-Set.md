---
layout: post
title:  Contextual-Tab-and-Tab-Set
description: contextual tab and tab set
documentation: ug
platform: Aurelia
keywords: contextual tab and tab set
---

# Contextual Tabs

`Contextual Tabs` are collection of Tabs that extended styling and can be shown based on some criteria. Contextual Tabs can be added like `tabs` including groups and content section. You can set `backgroundColor` and `borderColor` to highlight them as Tab set. Contextual tabs can be added or set dynamically in ribbon control using [`addContextualTabs`](https://help.syncfusion.com/api/js/ejribbon#methods:addcontextualtabs) with it's object and index position.

{% highlight html %}

     <template>
    <div>
        <ej-ribbon id="default" e-width="100%" e-application-tab.bind="ApplicationTab" e-tabs.bind="Tabs" e-contextual-tabs.bind="contextualTabs">
        </ej-ribbon>
    </div>
    <div class="content-container-fluid">
        <div class="row">
            <div class="cols-sample-area">
                <div>
                    <div id="defaultRibbon"></div>
                </div>
                <ul id="RibbonMenu">
                    <li>
                        <a>FILE</a>
                        <ul>
                            <li><a>New</a></li>
                            <li><a>Open</a></li>
                        </ul>
                    </li>
                </ul>
                <div id="Contents">Custom Control</div>
                <div id="headings" class="e-headings">
                    <div>
                        <p>ABCD</p>
                        <p>No Spacing</p>
                    </div>
                    <div>
                        <p class="e-strong">ABCD</p>
                        <p>Strong</p>
                    </div>
                    <div>
                        <p class="e-emphasis">ABCD</p>
                        <p>Emphasis</p>
                    </div>
                </div>
                <table id="design" class="e-designtablestyle">
                    <tr>
                        <td>
                            <input type="checkbox" id="Check2" />
                            <label for="Check2">First Column</label>
                        </td>
                        <td>
                            <input type="checkbox" id="check4" checked="checked" />
                            <label for="check4">Total Row</label>
                        </td>
                    </tr>
                </table>
     </template>
   
{% endhighlight %}

{% highlight html %}

    export class default {
    constructor() {
        this.ApplicationTab = { type: ej.Ribbon.ApplicationTabType.Menu, menuItemID: 'RibbonMenu', menuSettings: {  openOnClick: false } };
        this.Tabs = [{
					
            id: "home",
            text: "HOME",
            groups: [{
                text: "CustomControls",
                type: "custom",
                contentID: "Contents"
            }]
        }];			
        // contextual Tabs collection
        this.contextualTabs=[{

            // contextual tab with custom content
            backgroundColor: "#FCFBEB",
            borderColor: "#F2CC1C",
            tabs: [{
                id: "Design",
                text: "DESIGN",
                groups: [{
                    text: "Table Style Options",
                    type: "custom",
                    contentID: "design"
                }]
            }]
        },
             // tab set with background & border color
             {
                 backgroundColor: "blue",
                 borderColor: "red",
                 tabs: [{
                     id: "tabset1",
                     text: "Tabset1",
                     groups: [{
                         text: "Tabset1 Style",
                         type: "custom",
                         contentID: "headings"
                     }]
                 }, {
                     id: "tabset2",
                     text: "Tabset2",
                     groups: [{
                         text: "TabSet2 Style",
                         content: [{
                             // groups with button controls
                             groups: [{
                                 id: "uppercase",
                                 text: "Upper Case",
                                 buttonSettings: {
                                     contentType: ej.ContentType.ImageOnly,
                                     prefixIcon: "e-ribbon e-icon e-uppercase"
                                 }
                             }, {
                                 id: "lowercase",
                                 text: "Lower Case",
                                 buttonSettings: {
                                     contentType: ej.ContentType.ImageOnly,
                                     prefixIcon: "e-ribbon e-icon e-lowercase"
                                 }
                             }],
                             defaults: {
                                 isBig: true
                             }
                         }]
                     }]
                 }]
             }
        ]
    }
    }
     
{% endhighlight %}

![](Contextual-Tab-and-Tab-Set_images/Contextual-Tab-and-Tab-Set_img1.png)

