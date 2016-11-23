---
layout: post
title: Getting Started for Rotator
description: Getting Started for Rotator
platform: Aurelia
control: Rotator
documentation: ug
keywords: Rotator, js rotator
---

# Getting Started

This section helps to get started of the Rotator component for Aurelia.

![](Getting_Started_images/getting-started1.png)

## Create a Rotator Component

* To create Syncfusion Aurelia application refer [Aurelia Getting Started](https://help.syncfusion.com/aurelia/overview#getting-started) Documentation.
* Create `rotator` folder inside `src/samples` location.
* Create `rotator.html` file inside `src/samples/rotator` folder and use the below code for rendering Rotator component.

{% highlight html %}

    <template>

        <ul id="sliderContent" ej-rotator="e-slide-width.bind:slideWidth>
        </ul>

    </template>


{% endhighlight %}
 

* Create `rotator.js` file inside `src/samples/rotator` folder with below code snippet.

{% highlight javascript %}

    export class BasicUse {
    constructor() {  
      this.slideWidth = '100%';
      this.frameSpace = '0px';
      this.slideHeight = 'auto';
      this.position = ej.Rotator.PagerPosition.TopLeft;
      this.orientation = ej.Orientation.Horizontal;
  
    }
    }

{% endhighlight %}

## Configure data

To configure images for Rotator component, define URL and title for images as given below.

{% highlight html %}

    <ul id="sliderContent" ej-rotator="e-slide-width.bind:slideWidth; 
        e-frame-space.bind:frameSpace; 
        e-pager-position:position;
        e-slide-height.bind: slideHeight;
        e-show-caption: true;
        e-show-play-button: true;
        e-is-responsive:true;">
            <li>
                <img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/seaview.jpg" title="Sea-View" /></li>
            <li>
                <img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/snowfall.jpg" title="Snow Fall" /></li>
            <li>
                <img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/tablet.jpg" title="Tablet" /></li>
            <li>
                <img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/nature.jpg" title="Nature" /></li>
            <li>
                <img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/card.jpg" title="Credit Card" /></li>
            <li>
                <img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/bird.jpg" title="Beautiful Bird" /></li>
            <li>
                <img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/wheat.jpg" title="Wheat”/></li>
            <li>
                <img class="image" src="http://js.syncfusion.com/demos/web/content/images/rotator/night.jpg" title="Colorful Night" /></li>
    </ul>	



{% endhighlight %}

![](Getting_Started_images/configuring-properties_img1.png)

> _Note:_ _You can find the Rotator properties from the_ [API reference](https://help.syncfusion.com/api/js/ejrotator) _document_
