---
layout: post
title:  Screen Tips
description: screen tips
documentation: ug
platform: Aurelia
keywords: screen tips,ribbon screen tips
---

# Screen Tips

ScreenTip/Tooltip is used to reduce the controls related Help that are needed to the end user to do control related actions.

## HTML Tooltip

Standard `html tooltip` can be set using `tooltip` property of each group item.

{% highlight html %}

    <template>  
    <div>
     <ej-ribbon id="default" e-allow-resizing="true" e-width="30%" e-application-tab.bind="ApplicationTab" e-tabs.bind="Tabs">
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
            id: "home",
            text: "HOME",
            groups: [{
                text: "Clipboard",
                content: [{
                    groups: [{
                        id: "cut",
                        text: "Cut",
                        // set tooltip to cut button
                        toolTip: "Remove the selection and put it on clipboard"
                    },
                    {
                        id: "copy",
                        text: "Copy",
                        // set tooltip to copy button
                        toolTip: "Put a copy of selection on clipboard",
                        buttonSettings: {
                            contentType: ej.ContentType.TextAndImage,
                            prefixIcon: "e-ribbon e-icon e-ribboncopy"
                        }
                    }],
                    defaults: {
                        height: 70,
                        width: 60
                    }
                }]
            }]
        }];
    }
    }
     
{% endhighlight %}

![](Screen-Tips_images/Screen-Tips_img1.png)

## Custom Tooltip

Custom Tooltip is used to set detailed help to the user about the controls. You can set `title`, `content` and `prefixIcon` class to customize the tooltip with icons.

### For Groups 

`Custom tooltip` for each group controls can be specified. Such as to the controls button, split button, dropdown list etc.

{% highlight html %}

    <template>  
    <div>
     <ej-ribbon id="default"  e-width="30%"  e-application-tab.bind="ApplicationTab" e-tabs.bind="Tabs">
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
				 <style type="text/css">
        .e-pastetip {
            background-image: url("images/ribbon/paste.png");
            background-repeat: no-repeat;
            height: 64px;
            width: 64px;
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
                text: "Clipboard",
                content: [{
                    groups: [{
                        id: "paste",
                        text: "Paste",
                        // set custom tooltip to paste button with icon settings
                        customToolTip: {
                            title: "Paste",
                            content: "<h6>Paste the content.<br/><br/>Add content on the Clipboard to your document.</h6>",
                            // class to set icon
                            prefixIcon: "e-pastetip"
                        }
                    }, {
                        id: "copy",
                        text: "Copy",
                        // set custom tooltip to copy button
                        customToolTip: {
                            title: "Copy",
                            content: "<h6>Copy the content.</h6>"
                        },
                        buttonSettings: {
                            contentType: ej.ContentType.TextAndImage,
                            prefixIcon: "e-ribbon e-icon e-ribboncopy"
                        }
                    }],
                    defaults: {
                        height: 70,
                        width: 60
                    }
                }]
            }]
        }];
    }
    } 

{% endhighlight %}

![](Screen-Tips_images/Screen-Tips_img2.png)

### For Gallery

`Custom tooltip` for each `gallery` and `custom gallery` items button control can be specified. 

N> Custom gallery item `menu` is not supported to Custom tooltip.

{% highlight html %}

    <template>
    <div>
        <ej-ribbon id="default" e-width="30%" e-application-tab.bind="ApplicationTab" e-tabs.bind="Tabs">
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
                <ul id="custommenu">
                    <li>
                        <a>New Quick Step</a>
                        <ul>
                            <li><a>Flag and Move</a></li>
                        </ul>
                    </li>
                </ul>
                <style type="text/css">
                    .e-gallerycontent1 {
                        background-position: 0 -105px;
                    }
                    .e-gallerycontent2 {
                        background-position: -69px -105px;
                    }
                    .e-gallerycontent3 {
                        background-position: -136px -105px;
                    }
                    .e-gallerycontent4 {
                        background-position: 0 -53px;
                    }
                    .e-gbtnposition {
                        margin-top: 5px;
                    }
                    .e-gbtnimg {
                        background-image: url("images/ribbon/homegallery.png");
                        background-repeat: no-repeat;
                        height: 64px;
                        width: 64px;
                    }
                    .e-extracontent .e-extrabtnstyle {
                        padding-left: 28px;
                        text-align: left;
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
                        type: "gallery",
                        text: "Gallery",
                        content: [{
                            groups: [{
                                id: "Gallery",
                                columns: 2,
                                itemHeight: 54,
                                itemWidth: 73,
                                expandedColumns: 3,
                                type: ej.Ribbon.type.gallery,
                                galleryItems: [{
                                    text: "Style 1",

                                    // custom tooltip of style 1 of gallery item
                                    customToolTip: {
                                        title: "Style 1",
                                        content: "<I>Style 1 to customize the table</I>"
                                    },
                                    buttonSettings: {
                                        contentType: ej.ContentType.ImageOnly,
                                        prefixIcon: "e-gallerycontent1 e-icon e-gbtnimg",
                                        cssClass: "e-gbtnposition"
                                    }
                                }, {
                                    text: "Style 2",
                                    customToolTip: {
                                        title: "Style 2",
                                        content: "<I>Style 2 to customize the table</I>"
                                    },
                                    buttonSettings: {
                                        contentType: ej.ContentType.ImageOnly,
                                        prefixIcon: "e-gallerycontent2 e-icon e-gbtnimg",
                                        cssClass: "e-gbtnposition"
                                    }
                                }, {
                                    text: "Style 3",
                                    customToolTip: {
                                        title: "Style 3",
                                        content: "<I>Style 3 to customize the table</I>"
                                    },
                                    buttonSettings: {
                                        contentType: ej.ContentType.ImageOnly,
                                        prefixIcon: "e-gallerycontent3 e-icon e-gbtnimg",
                                        cssClass: "e-gbtnposition"
                                    }
                                }, {
                                    text: "Style 4",
                                    customToolTip: {
                                        title: "Style 4",
                                        content: "<I>Style 4 to customize the table</I>"
                                    },
                                    buttonSettings: {
                                        contentType: ej.ContentType.ImageOnly,
                                        prefixIcon: "e-gallerycontent4  e-icon e-gbtnimg",
                                        cssClass: "e-gbtnposition"
                                    }
                                }],
                                customGalleryItems: [{
                                    text: "Clear Formatting",
                                    toolTip: "Clear Formatting",
                                    customItemType: ej.Ribbon.customItemType.button,

                                    // custom tooltip of style 1 of custom gallery item
                                    customToolTip: {
                                        title: "Clear Format",
                                        content: "<I>To clear formatting</I>"
                                    },
                                    buttonSettings: {
                                        cssClass: "e-extrabtnstyle"
                                    }
                                }, {
                                    customItemType: ej.Ribbon.customItemType.menu,
                                    menuId: "custommenu",
                                    menuSettings: {
                                        openOnClick: false
                                    }
                                }]
                            }]
                        }]
                    }]
                }];
     }
     }
     
{% endhighlight %}


![](Screen-Tips_images/Screen-Tips_img3.png)

