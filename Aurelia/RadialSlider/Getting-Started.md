---
layout: post
title: Syncfusion RadialSlider Getting Started
description: Getting Started for RadialSlider
platform: Aurelia
control: RadialSlider
documentation: ug
keywords: RadialSlider, js radialslider
---

# Getting Started

This section helps to get started of the RadialSlider component in an Aurelia application.

![Getting Started](Getting_Started_images/getting-started-img1.png)

## Create a RadialSlider Component

* To create Syncfusion Aurelia application refer [Aurelia Getting Started](https://help.syncfusion.com/aurelia/overview#getting-started) Documentation.
* Create `radialSlider` folder inside `src/samples` location.
* Create `radialSlider.html` file inside `src/samples/radialSlider` folder and use the below code for rendering RadialSlider component.

{% highlight html %}

    <template>
    <ej-radial-slider id="radialSlider"> </ej-radial-slider>
    </template>


{% endhighlight %}
 

* Create `radialSlider.js` file inside `src/samples/radialSlider` folder with below code snippet.

{% highlight javascript %}

    export class BasicUse {
    constructor() {    
    }
    }

{% endhighlight %}

## Image Configuration

RadialSlider property **e-inner-circle-image-url** allow to set URL image to the inner circle of the RadialSlider. Refer to the following code example.

{% highlight html %}

    <ej-radial-slider id="radialSlider" e-inner-circle-image-url="images/radialslider/chevron-right.png">
    </ej-radial-slider>

{% endhighlight %}

![Image Configuration](Getting_Started_images/getting-started-img1.png)

> _Note:_ _You can find the RadialSlider properties from the_ [API reference](https://help.syncfusion.com/api/js/ejradialslider) _document_


