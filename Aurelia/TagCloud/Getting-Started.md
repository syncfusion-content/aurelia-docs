---
layout: post
title: Getting-Started for TagCloud
description: getting started for TagCloud
platform: Aurelia
control: TagCloud
documentation: ug
keywords: TagCloud,js tagcloud,ejtagcloud
---

# Getting Started

This section explains briefly about how to create a **TagCloud** in your application with **Aurelia**. The **TagCloud** can be easily configured to the div element in which the tags are placed. The following screenshot illustrates the functionality of a **TagCloud** widget with a list of the topmost search engines. 

![](Getting-Started_images/Getting-Started1.jpg)

## Create TagCloud widget

Before we start with TagCloud, please refer [this page](https://help.syncfusion.com/aurelia/overview#getting-started) page for general information regarding integrating Syncfusion widget’s.

For quick start, we already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

    > git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
    > cd syncfusion-template-repository
    > npm install
    > jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia TagCloud component.

    Create TagCloud folder inside src/samples/ location.
    Create TagCloud.html file inside src/samples/TagCloud folder and use the below code example to render the TagCloud component.
	
Add necessary elements to render TagCloud

{% highlight html %}

    <template>
       <div>
         <ej-tag-cloud id="techWebList" e-title-text.bind="title" e-data-source.bind="data">
         </ej-tag-clod>
       </div>    
   </template>

{% endhighlight %}

Add the following code example to add list of items to the **TagCloud** and initialize the **TagCloud** widget.

{% highlight html %}

     export class Tagclouddefault {
       websiteCollection = [
                    { text: 'Google', url: 'http://www.google.com', frequency: 12 },
                    { text: 'All Things Digital', url: 'http://allthingsd.com/', frequency: 3 },
                    { text: 'Arts Technica', url: 'http://arstechnica.com/', frequency: 8 },
                    { text: 'Business Week', url: 'http://www.businessweek.com/', frequency: 2 },
                    { text: 'Yahoo', url: 'http://in.yahoo.com/', frequency: 12 },
                    { text: 'Center Networks', url: 'http://www.centernetworks.com/', frequency: 5 },
                    { text: 'Crave', url: 'http://news.cnet.com/crave/', frequency: 8 },
                    { text: 'Crunch Gear', url: 'http://techcrunch.com/gadgets/', frequency: 20 },
                    { text: 'Daily Tech', url: 'http://www.dailytech.com/', frequency: 1 },
                    { text: 'Electronista', url: 'http://www.electronista.com/', frequency: 3 },
                    { text: 'Engadget', url: 'http://www.engadget.com/', frequency: 5 },
                    { text: 'Gearlog', url: 'http://www.gearlog.com/', frequency: 9 },
                    { text: 'Information Week', url: 'http://www.informationweek.com/', frequency: 0 },
                    { text: 'PCWorld', url: 'http://www.pcworld.com/', frequency: 11 },
                    { text: 'Tech Republic', url: 'http://techrepublic.com/', frequency: 3 },
                    { text: 'Valleywag', url: 'http://valleywag.gawker.com/', frequency: 6 },
                    { text: 'Rediff', url: 'http://in.rediff.com/', frequency: 9 },
                    { text: 'WebProNews', url: 'http://www.webpronews.com/', frequency: 2 }
           ];

    constructor() {
      this.title = 'Popular Sites';
      this.data = this.websiteCollection;
          }
       }
 
{% endhighlight %}

The following screenshot displays the output of the above code example.

![](Getting-Started_images/Getting-Started1.jpg) 

## Set Min and Max Font Size

In the above code example, the **frequency** properties are used to set the min and max font size to the **TagCloud** list item.

{% highlight javascript %}
   
    export class Tagclouddefault {
       websiteCollection = [
                    { text: 'Google', url: 'http://www.google.com', frequency: 12 },
                    { text: 'All Things Digital', url: 'http://allthingsd.com/', frequency: 3 },
                    { text: 'Arts Technica', url: 'http://arstechnica.com/', frequency: 8 },
                    { text: 'Business Week', url: 'http://www.businessweek.com/', frequency: 2 },
                    { text: 'Yahoo', url: 'http://in.yahoo.com/', frequency: 12 },
                    { text: 'Center Networks', url: 'http://www.centernetworks.com/', frequency: 5 },
                    { text: 'Crave', url: 'http://news.cnet.com/crave/', frequency: 8 },
                    { text: 'Crunch Gear', url: 'http://techcrunch.com/gadgets/', frequency: 20 },
                    { text: 'Daily Tech', url: 'http://www.dailytech.com/', frequency: 1 },
                    { text: 'Electronista', url: 'http://www.electronista.com/', frequency: 3 },
                    { text: 'Engadget', url: 'http://www.engadget.com/', frequency: 5 },
                    { text: 'Gearlog', url: 'http://www.gearlog.com/', frequency: 9 },
                    { text: 'Information Week', url: 'http://www.informationweek.com/', frequency: 0 },
                    { text: 'PCWorld', url: 'http://www.pcworld.com/', frequency: 11 },
                    { text: 'Tech Republic', url: 'http://techrepublic.com/', frequency: 3 },
                    { text: 'Valleywag', url: 'http://valleywag.gawker.com/', frequency: 6 },
                    { text: 'Rediff', url: 'http://in.rediff.com/', frequency: 9 },
                    { text: 'WebProNews', url: 'http://www.webpronews.com/', frequency: 2 }
           ];

    constructor() {
      this.title = 'Popular Sites';
      this.data = this.websiteCollection;
          }
       }
 
{% endhighlight %}

In the above code, the min font size is 0 and max font size is 12.

## Set event to perform an operation

Here, you can set the **TagCloud** events such as create, mouseover, mouseout, click.

{% highlight html %}

    <template>
       <div>
         <ej-tag-cloud id="techWebList" e-title-text.bind="title" e-data-source.bind="data" e-on-create.trigger="create()" e-on-mouseover.trigger="mouseOver($event)" e-on-mouseout.trigger="mouseOut($event)" e-on-click.trigger="click($event)">
         </ej-tag-clod>
       </div>    
    </template>

{% endhighlight %}

{% highlight html %}

     export class Tagclouddefault {
       websiteCollection = [
                    { text: 'Google', url: 'http://www.google.com', frequency: 12 },
                    { text: 'All Things Digital', url: 'http://allthingsd.com/', frequency: 3 },
                    { text: 'Arts Technica', url: 'http://arstechnica.com/', frequency: 8 },
                    { text: 'Business Week', url: 'http://www.businessweek.com/', frequency: 2 },
                    { text: 'Yahoo', url: 'http://in.yahoo.com/', frequency: 12 },
                    { text: 'Center Networks', url: 'http://www.centernetworks.com/', frequency: 5 },
                    { text: 'Crave', url: 'http://news.cnet.com/crave/', frequency: 8 },
                    { text: 'Crunch Gear', url: 'http://techcrunch.com/gadgets/', frequency: 20 },
                    { text: 'Daily Tech', url: 'http://www.dailytech.com/', frequency: 1 },
                    { text: 'Electronista', url: 'http://www.electronista.com/', frequency: 3 },
                    { text: 'Engadget', url: 'http://www.engadget.com/', frequency: 5 },
                    { text: 'Gearlog', url: 'http://www.gearlog.com/', frequency: 9 },
                    { text: 'Information Week', url: 'http://www.informationweek.com/', frequency: 0 },
                    { text: 'PCWorld', url: 'http://www.pcworld.com/', frequency: 11 },
                    { text: 'Tech Republic', url: 'http://techrepublic.com/', frequency: 3 },
                    { text: 'Valleywag', url: 'http://valleywag.gawker.com/', frequency: 6 },
                    { text: 'Rediff', url: 'http://in.rediff.com/', frequency: 9 },
                    { text: 'WebProNews', url: 'http://www.webpronews.com/', frequency: 2 }
           ];

    constructor() {
      this.title = 'Popular Sites';
      this.data = this.websiteCollection;
          }
		  
	 create() {
      alert();
      }
     mouseOver(event) {
       alert();
      }
     mouseOut(event) {
        alert();
       }
     click(event) {
       alert();
        }
		
       }
{% endhighlight %}

In the above code example, the **alert()** function is used  to show the events that happened.

