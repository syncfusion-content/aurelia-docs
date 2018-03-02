---
layout: post
title: Getting-Started
description: getting started
platform: Aurelia
control: CircularGauge
documentation: ug
---

# Getting Started

* This section encompasses how to configure Circular Gauge. You can provide data to a Circular Gauge and make them to display in a required way.

* The following screen shot displays a Circular Gauge, which visually represents the functions of an Automobile speedometer with RPM (Rotation per Minute), kph (Kilometer per hour) and it denotes the speed level indicators (Safe, Caution and Danger).


![](Getting-Started_images/Getting-Started_img11.png)

Analog Speedometer
{:.caption}

## Create your circularGauge

In this tutorial, you will learn how to create a simple circular gauge.

1.To create Syncfusion Aurelia application refer [Aurelia Getting Started documentation](https://help.syncfusion.com/aurelia/overview#getting-started "").
2.Create `circularGauge` folder inside `src/samples` location.
3.Create `circularGauge.html` file inside  `src/samples/circularGauge` folder and use the below code for rendering CircularGauge component 
4.Create a <div> tag.
	
 {% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-circular-gauge id="circularGauge">
        </ej-circular-gauge>
        </div>
</template>
</body>
</html>

{% endhighlight %}

5.Create `circularGauge.js` file inside `src/samples/circularGauge` folder with below code snippet.

{% highlight javascript %}

export class CircularGauge {
    constructor() {}
    }

{% endhighlight %}

Run the above code example to get a default CircularGauge with default values.

![](Getting-Started_images/Getting-Started_img2.png)


## Set Height and Width

Pointers have different height and width so you can set the height and width of the gauge according to your requirements.Set the basic values of the gauge such as height and width of the canvas element values that are to be rendered.

{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-circular-gauge id="circularGauge" e-height="500" e-width="500">
        </ej-circular-gauge>
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

Run the above code example and you will see the following output.

![](Getting-Started_images/Getting-Started_img3.png)


## Set Background Color

The speedometer must have some dark color as background so that its value is clearly visible and you can vary the speed of the pointer by setting ReadOnly as False for user interaction.

{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-circular-gauge id="circularGauge" e-height="500" e-width="500" e-background-color="#3D3F3D" e-read-only="false" >
        </ej-circular-gauge>
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


Run the above code example and you will see the following output.

![](Getting-Started_images/Getting-Started_img4.png)

## Provide Scale Values

* The pointer cap can be customized with the following options. Cap radius, cap border color, cap background color, pointer cap border width are some of the properties that are customizable.
* The speed limit in the gauge has maximum value of 200 kph. So you can set maximum value for the gauge as 200.
* Major Ticks have the interval value of 20 and minor ticks have the interval value of 5. Show ranges and show indicators are used to display the ranges and indicators in their respective positions.

{% highlight javascript %}

export class BasicUse {
constructor() {
 this.scales=  [{
            showRanges: true,
            showIndicators: true,
            pointerCap: {
                radius: 15,
                borderWidth: 0,
                backgroundColor: "#797C79",
                borderColor: "#797C79"
            },
            maximum: 200,
            majorIntervalValue: 20,
            minorIntervalValue: 5
              }];    
}
}

{% endhighlight %}

{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-circular-gauge id="circularGauge" e-height="500" e-width="500" e-background-color="#3D3F3D" e-read-only="false" e-scales.bind="scales" >
        </ej-circular-gauge>
        </div>
</template>
</body>
</html>
{% endhighlight %}

Run the above code example and you will see the following output.

![](Getting-Started_images/Getting-Started_img5.png)


## Add Label Customization

To display the value around the scales, labels are used. By customizing the label color it displays as specified.

{% highlight javascript %}

export class BasicUse {
constructor() {
 this.scales=  [{
            //Add the labels customization code here
            labels: [{
                color: "#ffffff"
            }],
              }];    
}
}

{% endhighlight %}

{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-circular-gauge id="circularGauge" e-height="500" e-width="500" e-background-color="#3D3F3D" e-read-only="false" e-scales.bind="scales" >
        </ej-circular-gauge>
        </div>
</template>
</body>
</html>
{% endhighlight %}


Run the above code example and you will see the following output.

![](Getting-Started_images/Getting-Started_img6.png)


## Add Pointers

Here, you have three pointers that denote the kilometer value, rotation per minute value and torque value.The torque value pointer needs not be similar to the other two pointers. You can set torque pointer as marker pointer. And you can set other attributes for pointer such as background color, border color, length, width and distance from scale.

{% highlight javascript %}

export class BasicUse {
constructor() {
 this.scales=  [{
            //Add the labels customization code here
            //Add the pointers customization code here
            pointers: [{
                value: 140,
                distanceFromScale: 60,
                showBackNeedle: false,
                length: 20,
                type: "marker",
                markerType: "triangle",
                width: 10,
                radius: 10,
                backgroundColor: "#FF940A",
                border: {
                    color: "#FF940A"
                },
            },
            {
                value: 110,
                showBackNeedle: false,
                length: 150,
                width: 2,
                radius: 10,
                needleType: "rectangle",
                backgroundColor: "#05AFFF",
                border: {
                    color: "#05AFFF"
                },
            }, {
                value: 67,
                showBackNeedle: false,
                length: 100,
                width: 15,
                radius: 10,
                backgroundColor: "#FC5D07",
                border: {
                    color: "#FC5D07"
                },
            }],
            //Add the ticks customization code here
            //Add the ranges customization code here
            //Add the indicators customization code here
            //Add the Custom labels customization code here
        }];
                
}
}

{% endhighlight %}

{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-circular-gauge id="circularGauge" e-height="500" e-width="500" e-background-color="#3D3F3D" e-read-only="false" e-scales.bind="scales" >
        </ej-circular-gauge>
        </div>
</template>
</body>
</html>
{% endhighlight %}

Run the above code example and you will see the following output.

![](Getting-Started_images/Getting-Started_img7.png)


## Add Tick Details

* You can set Major ticks with their width and height equal to Minor ticks. 
* You can set Color according to your preference for better visibility in dark backgrounds.
* To display and customize the tick value add the following code example. 

{% highlight javascript %}

export class BasicUse {
constructor() {
 this.scales=  [{
            //Add the labels customization code here
            //Add the pointers customization code here
            //Add the ticks customization code here
            ticks: [{
                type: "major",
                distanceFromScale: 70,
                height: 20,
                width: 3,
                color: "#ffffff"
            }, {
                type: "minor",
                height: 12,
                width: 1,
                distanceFromScale: 70,
                color: "#ffffff"
        }];
 }];       
}
}

{% endhighlight %}

{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-circular-gauge id="circularGauge" e-height="500" e-width="500" e-background-color="#3D3F3D" e-read-only="false" e-scales.bind="scales" >
        </ej-circular-gauge>
        </div>
</template>
</body>
</html>
{% endhighlight %}
Run the above code example and you will see the following output.

![](Getting-Started_images/Getting-Started_img8.png)


## Add Range Values

* Ranges denote the property of the scale value in the speedometer. The color values of the ranges denote speed variation. Set ShowRanges as True for showing the ranges in the Circular Gauge.
* For Low speed, you can mention it as safe zone; for moderate speed, you can call it as caution zone and for high speed, you can mark it as high speed.
* You can customize the range with properties such as start value, end value, start width, end width,  background color , border color, etc.,


{% highlight javascript %}

export class BasicUse {
constructor() {
 this.scales=  [{
            ranges: [{
                distanceFromScale: 30,
                startValue: 0,
                endValue: 70,
                backgroundColor: "#5DF243",
                border: {
                    color: "#FFFFFF"
                },
            }, {
                distanceFromScale: 30,
                startValue: 70,
                endValue: 140,
                backgroundColor: "#F6FF0A",
                border: {
                    color: "#FFFFFF"
                },
            },
            {
                distanceFromScale: 30,
                startValue: 140,
                endValue: 200,
                backgroundColor: "#FF1807",
                border: {
                    color: "#FFFFFF"
                },
            }],
 }];    
}
}

{% endhighlight %}

{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-circular-gauge id="circularGauge" e-height="500" e-width="500" e-background-color="#3D3F3D" e-read-only="false" e-scales.bind="scales" >
        </ej-circular-gauge>
        </div>
</template>
</body>
</html>
{% endhighlight %}

Run the above code example and you will see the following output.



![](Getting-Started_images/Getting-Started_img9.png)


## Add Indicator Details

* Indicators denote whether the pointers values are in their respective zones or not. Positioning the indicator on the respective range value gives you the required changes.
* By using Position property, you can set the location of the indicator. StateRanges defines how the indicator should behave when the pointer is in certain values. 

{% highlight javascript %}

export class BasicUse {
constructor() {
 this.scales=  [{
             indicators: [
            {
                height: 10,
                width: 10,
                type: "circle",
                position: { x: 210, y: 300 },
                stateRanges: [{
                    endValue: 70,
                    startValue: 0,
                    backgroundColor: "#5DF243",
                    borderColor: "#5DF243",
                    text: "",
                    textColor: "#870505"
                }, {
                    endValue: 200,
                    startValue: 70,
                    backgroundColor: "#145608",
                    borderColor: "#145608",
                    text: "",
                    textColor: "#870505"
                }]
            },
            {
                height: 10,
                width: 10,
                type: "circle",
                position: { x: 255, y: 200 },
                stateRanges: [{
                    endValue: 140,
                    startValue: 70,
                    backgroundColor: "#F6FF0A",
                    borderColor: "#F6FF0A",
                    text: "",
                }, {
                    endValue: 70,
                    startValue: 0,
                    backgroundColor: "#969B0C",
                    borderColor: "#969B0C",
                    text: "",
                }, {
                    endValue: 200,
                    startValue: 140,
                    backgroundColor: "#969B0C",
                    borderColor: "#969B0C",
                    text: "",
                }]
            }, {
                height: 10,
                width: 10,
                type: "circle",
                position: { x: 300, y: 300 },
                stateRanges: [{
                    endValue: 140,
                    startValue: 0,
                    backgroundColor: "#890F06",
                    borderColor: "#890F06",
                    text: "",
                },
                {
                    endValue: 200,
                    startValue: 140,
                    backgroundColor: "#FF1807",
                    borderColor: "#FF1807",
                    text: "",
                }]
            }]
 }];    
}
}

{% endhighlight %}

{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-circular-gauge id="circularGauge" e-height="500" e-width="500" e-background-color="#3D3F3D" e-read-only="false" e-scales.bind="scales" >
        </ej-circular-gauge>
        </div>
</template>
</body>
</html>
{% endhighlight %}

Run the above code example and you will see the following output.

![](Getting-Started_images/Getting-Started_img10.png)


## Add Custom Label Details

Custom labels are used to specify the texts that need to be displayed in the gauge. You can customize it through various properties.To display the three range description, custom texts are used here.


{% highlight javascript %}
export class BasicUse {
constructor() {
 this.scales=  [{
              customLabels: [{
                value: "Safe",
                position: { x: 200, y: 280 },
                color: "#5DF243",
                font:
                {
                    size: "12px",
                    fontFamily: "Arial",
                    fontStyle: "Bold"
                }
            }, {
                value: "Caution",
                position: { x: 253, y: 212 },
                color: "#F6FF0A",
                font:
                {
                    size: "12px",
                    fontFamily: "Arial",
                    fontStyle: "Bold"
                }
            }, {
                value: "Danger",
                position: { x: 290, y: 280 },
                color: "#FF1807",
                font:
                {
                    size: "12px",
                    fontFamily: "Arial",
                    fontStyle: "Bold"
                }
            }]
 }];    
}
}

{% endhighlight %}

{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-circular-gauge id="circularGauge" e-height="500" e-width="500" e-background-color="#3D3F3D" e-read-only="false" e-scales.bind="scales" >
        </ej-circular-gauge>
        </div>
</template>
</body>
</html>

{% endhighlight  %}
Run the above code example and you will see the following output.

![](Getting-Started_images/Getting-Started_img11.png)
