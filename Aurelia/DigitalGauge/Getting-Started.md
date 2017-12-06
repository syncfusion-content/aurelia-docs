---
layout: post
title: Getting-Started
description: getting started
platform: Aurelia
control: DigitalGauge
documentation: ug
---

# Getting Started
* This section encompasses the details on how to configure DigitalGauge. Here you will learn how to provide data for a DigitalGauge and display the data in the required way. 
* In addition, you will learn how to customize the default DigitalGauge appearance according to your requirements. As a result, you will get a DigitalGauge that shows it as Digital thermometer.
* You can use this DigitalGauge in advertisements, decorative purposes, displaying share details in share market, game score boards, token systems, etc.


![](Getting-Started_images/Getting-Started_img1.png)

Digital Thermometer
{:.caption}


## Create a Digital Gauge

1.To create Syncfusion Aurelia application refer [Aurelia Getting Started documentation](https://help.syncfusion.com/aurelia/overview#getting-started "").
2.Create `digitalGauge` folder inside `src/samples` location.
3.Create `digitalGauge.html` file inside  `src/samples/digitalGauge` folder and use the below code for rendering DigitalGauge component 
4.Create a <div> tag.
	
   {% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-digital-gauge id="digitalgauge">
        </ej-digital-gauge>
        </div>
</template>
</body>
</html>

{% endhighlight %}

5.Create `digitalGauge.js` file inside `src/samples/digitalGauge` folder with below code snippet.

{% highlight javascript %}

export class DigitalGauge {
    constructor() {}
    }

{% endhighlight %}
   
Run the above code example and you will get a default Digital Gauge as follows.

![](Getting-Started_images/Getting-Started_img2.png)

Digital Gauge
{:.caption}

## Set Height and Width values

Basic attributes of each canvas elements are height and width. You can set the height and width of the gauge.

{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-digital-gauge id="digitalGauge" e-height="145" e-width="260">
        </ej-digital-gauge>
        </div>
</template>
</body>
</html>

{% endhighlight %}

{% highlight javascript %}

export class BasicUse {
constructor() {
 
}
}

{% endhighlight %}

Run the above code example and you will see a default gauge with the specified height and width values.

![](Getting-Started_images/Getting-Started_img3.png)

Digital Gauge with Height and Width
{:.caption}

## Set Items Property

Items have different properties to customize the Digital Gauge.

### Add Segment and Character Properties

* In the Welcome Board, the text color must be attentive in nature. You can give some segment properties such as segment spacing, segment width, segment color, segment length and segment opacity.
* Character type is to define the Digital representation of the character. The five types of character representation available are,
	1. EightCrossEightDotMatrix
	2. SevenSegment
	3. FourteenSegment
	4. SixteenSegment 
	5. EightCrossEightSquareMatrix.

{% highlight javascript %}

export class BasicUse {
constructor() {
 this.items= [{
                segmentSettings: { width: 2, length: 20 },
                characterSettings: { type: "SevenSegment", spacing: 12, },
                value: "102",
            }];
}
}

{% endhighlight %}


{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-digital-gauge id="digitalGauge" e-height="145" e-width="260" e-items.bind="items">
        </ej-digital-gauge>
        </div>
</template>
</body>
</html>

{% endhighlight %}


Run the above code example and you will see the following output.

![](Getting-Started_images/Getting-Started_img4.png)

Digital Gauge Segment Properties
{:.caption}


## Add Background Image

* Add a <div> element to set the background for the Digital Gauge. 
* Add a style tag in the View page to add the background image for the Digital Gauge.
* Add the required properties to show the background image such as position, margin, display, etc.,


{% highlight html %}
<!DOCTYPE html>
<body>
<template>

<div id="frameDiv"  style= "align : center;position : relative;margin : 0px auto;display :table;background-image :url("script/frame.png");background-repeat :no-repeat;">
<div>
     <ej-digital-gauge id="digitalGauge" e-height="145" e-width="260">
        </ej-digital-gauge>
        </div>
</div>
</template>
</body>
</html>

{% endhighlight %}


Run the above code example and you will see the following output.                    

![](Getting-Started_images/Getting-Started_img5.png)

Digital Gauge Background Image
{:.caption}

## Add Location

The Location property is used to position the digital letters inside the canvas element.

{% highlight javascript %}

export class BasicUse {
constructor() {
 this.items= [{
               //For Displaying Fahrenheit value
                segmentSettings: { width: 2, length: 20 },
                characterSettings: { type: "SevenSegment", spacing: 12, },
                value: "102", position: { x: 15, y: 40 }
 }];
}
}

{% endhighlight %}


{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-digital-gauge id="digitalGauge" e-height="145" e-width="260" e-items.bind="items">
        </ej-digital-gauge>
        </div>
</template>
</body>
</html>

{% endhighlight %}
Run the above code example and you will see the following output. 

![](Getting-Started_images/Getting-Started_img6.png)

Digital Gauge with Segment Location
{:.caption}

## Add Items Collection 

You can further add the Items Collection to display the temperature value like Digital Thermometer.

{% highlight javascript %}

export class BasicUse {
constructor() {
 this.items= [{
                //For Displaying Fahrenheit value
                segmentSettings: { width: 2, length: 20, spacing: 0 },
                characterSettings: { type: "SevenSegment", spacing: 12, },
                value: "102",
                position: { x: 15, y: 40 }
            },
            {
                //For displaying degree symbol
                segmentSettings: { width: 2, length: 5, spacing: 0 },
                characterSettings: { type: "SevenSegment", spacing: 5, },
                value: "0",
                position: { x: 70, y: 28 }
            },
            {
                //For displaying Fahrenheit symbol
                segmentSettings: { width: 2, length: 20, spacing: 0 },
                characterSettings: { type: "SevenSegment", spacing: 12, },
                value: "F",
                position: { x: 170, y: 40 }
            },
            {
                //For displaying Celcius value
                segmentSettings: { width: 1, length: 9, spacing: 0, color: "#F5b43f" },
                characterSettings: { type: "SevenSegment", spacing: 12, },
                value: "38",
                position: { x: 70, y: 90 },
            },
            {
                //For displaying degree symbol
                segmentSettings: { width: 1, length: 3, spacing: 0, color: "#F5b43f" },
                characterSettings: { type: "SevenSegment", spacing: 12, },
                value: "0",
                position: { x: 90, y: 80 }
            },
            {
                //For displaying celcius symbol
                segmentSettings: { width: 1, length: 9, spacing: 0, color: "#F5b43f" },
                characterSettings: { type: "SevenSegment", spacing: 12, },
                value: "c",
                position: { x: 120, y: 90 }
            }];
 
}
}

{% endhighlight %}


{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-digital-gauge id="digitalGauge" e-height="145" e-width="260" e-items.bind="items">
        </ej-digital-gauge>
        </div>
</template>
</body>
</html>

{% endhighlight %}


Run the above code example and you will see the following output.                    

![](Getting-Started_images/Getting-Started_img7.png)

Digital Gauge with Item Collection
{:.caption}

