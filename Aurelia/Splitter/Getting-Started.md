---
layout: post
title: Getting Started for Splitter
description: Getting Started for Splitter
platform: Aurelia
control: Splitter
documentation: ug
keywords: Splitter, js splitter
---

# Getting Started

Splitter component consists of movable split bar(s) that divides a container's display area into two or more resizable and collapsible panels. 
From the following guidelines, you can create a Splitter, add Tree view in the Splitter and set actions to view the image. It is used to split the document or image and Expand or Collapse in the Splitter. The following screenshot demonstrates the functionality of Splitter component.

![](Getting_Started_images/Getting_Started_img1.png)

## Create a Splitter Component

* To create Syncfusion Aurelia application refer [Aurelia Getting Started](https://help.syncfusion.com/aurelia/overview#getting-started) Documentation.
* Create `splitter` folder inside `src/samples` location.
* Create `splitter.html` file inside `src/samples/splitter` folder and use the below code for rendering Splitter component.

{% highlight html %}

    <template>
    <ej-splitter id="outterSplitter"  e-height="350" e-width="100%" e-properties.bind="properties" e-enable-auto-resize="true">
    </ej-splitter>

    </template>


{% endhighlight %}
 

* Create `splitter.js` file inside `src/samples/splitter` folder with below code snippet.

{% highlight javascript %}

    export class BasicUse {
    constructor() {  
        this.properties = [{ paneSize: '50%' }, {}];  
    }
    }

{% endhighlight %}

## Configure Splitter Panes

Add div element to create **Splitter**. Save the images in the corresponding location. 

{% highlight html %}

    <ej-splitter id="outterSplitter"  e-height="350" e-width="100%" e-properties.bind="properties"  e-enable-auto-resize="true">
    <div>					
        <div class="cont">
            <h3 class="h3">Aurelia</h3>                          
        </div>
    </div>
    <div>
        <div class="cont">
            <div class="_content">
                Select any product from the tree to show the description.
            </div>
            <div class=" galaxy spe">
                <h3>Mobile</h3>
                <img src="galaxy.jpg" />
            </div>
            <div class=" harddisk spe">
                <h3>Harddisk</h3>
                <img src="harddisk.jpg" />
            </div>
            <div class="logo spe">
                <h3>Logo</h3>
                <img src="logo.jpg" />
            </div>
        </div>
    </div>                                     
    </div>
    </ej-splitter>


{% endhighlight %}

Add the following styles to show the Splitter control in horizontal order.

{% highlight css %}

    .e-splitter{
          display: block;
      }
    .cont {
      padding: 20px;
      min-width: 50px;
     }

    .cont #treeView_Container {
        margin-bottom: 0;
        border: none;
    }

    .h3 {
        font-size: 14px;
        margin: 0;
    }

    .spe {
        display: none;
    }


{% endhighlight %}


## Configure Tree View

For adding TreeView component, you have to use ul element to corresponding element.

Add the following code example in HTML file to configure Tree View.


{% highlight html %}

    <ul id="treeView" class="visibleHide" ej-treeview e-nodeSelect="treeClicked">
        <li> Mobile
                <ul>
                    <li id=" Galaxy " class="_child">Galaxy</li>
                </ul>
        </li>
        <li>Harddisk
                <ul>
                    <li id="Harddisk" class="_child">Segate  </li>
                </ul>
        </li>
        <li>Logo
                <ul>
                    <li id="Logo" class="_child">Amazon</li>
                </ul>
        </li>
    </ul>

{% endhighlight %}


## Set Actions

Add the following code example in script to set the action to view the image.

{% highlight javascript %}

    export class BasicUse {
        constructor() {
          this.orientation = ej.Orientation.Vertical;
          this.properties = [{ paneSize: '50%' }, {}];
        }
    treeClicked(sender) {
          let content;
          if (sender.detail.currentElement.hasClass('_child')) {
            content = $('.' + sender.detail.currentElement[0].id).html();
            $('._content').html(content);
          }
        }
    }

{% endhighlight %}

The following screenshot is the output for the above code.

![](Getting_Started_images/Getting_Started_img1.png)

> _Note:_ _You can find the Splitter properties from the_ [API reference](https://help.syncfusion.com/api/js/ejsplitter) _document_
