---
title: Getting-Started
description: getting started
platform: Aurelia
control: BulletGraph
documentation: ug
---

# Getting Started

This section explains briefly about how to create a BulletGraph control in your application with  **Aurelia**

## Creating the first Bullet Graph 

This section encompasses the details on how to configure the BulletGraph control in your application. It also allows you to learn how to pass the required data to it and customize its various options according to your requirements.

In the following screenshot, a BulletGraph is used to compare the actual monsoon rainfall received in a state versus its forecasted values for the years ranging from 1988 to 2013.

![](Getting-Started_images/Getting-Started_img1.jpg)

1.To create Syncfusion Aurelia application refer [Aurelia Getting Started documentation](https://help.syncfusion.com/aurelia/overview#getting-started "").
2.Create `bulletGraph` folder inside `src/samples` location.
3.Create `bulletGraph.html` file inside  `src/samples/bulletGraph` folder and use the below code for rendering BulletGraph component 
4.Create a <div> tag.
	
   {% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-bullet-graph id="graph">
        </ej-bullet-graph>
        </div>
</template>
</body>
</html>

{% endhighlight %}

5.Create `bulletGraph.js` file inside `src/samples/bulletGraph` folder with below code snippet.

{% highlight javascript %}

export class BulletGraph {
    constructor() {}
    }

{% endhighlight %}


Execute the above code to display the BulletGraph. To customize the measure bars in the BulletGraph, you can pass the data either locally or remotely.

![](Getting-Started_images/Getting-Started_img2.png)

### Provide Required Data

You can customize the values of feature and comparative measure bars in a BulletGraph, either locally or remotely. The category data is optional, and it is used to display label values parallel to the measure bars. 

Assign the data in LocalData variable to the DataSource property of BulletGraph as illustrated in the following code example. 


{% highlight javascript %}

export class BasicUse {
constructor() {
 this.localData = [
            {
                value: 90, comparativeMeasureValue: 100,
                category: 2013
            },
            {
                value: 93, comparativeMeasureValue: 99,
                category: 2012
            },
            {
                value: 98, comparativeMeasureValue: 96,
                category: 2011
            },
            {
                value: 102, comparativeMeasureValue: 98,
                category: 2010
            },
            {
                value: 77, comparativeMeasureValue: 96,
                category: 2009
            },
            {
                value: 99, comparativeMeasureValue: 99,
                category: 2008
            },
            {
                value: 106, comparativeMeasureValue: 94,
                category: 2007
            },
            {
                value: 105, comparativeMeasureValue: 95,
                category: 2006
            },
            {
                value: 98, comparativeMeasureValue: 98,
                category: 2005
            },
            {
                value: 87, comparativeMeasureValue: 100,
                category: 2004
            },
            {
                value: 105, comparativeMeasureValue: 98,
                category: 2003
            },
            {
                value: 84, comparativeMeasureValue: 101,
                category: 2002
            },
            {
                value: 93, comparativeMeasureValue: 98,
                category: 2001
            },
            {
                value: 90, comparativeMeasureValue: 96,
                category: 2000
            },
            {
                value: 95, comparativeMeasureValue: 107,
                category: 1999
            },
            {
                value: 104, comparativeMeasureValue: 98,
                category: 1998
            },
            {
                value: 102, comparativeMeasureValue: 92,
                category: 1997
            },
            {
                value: 103, comparativeMeasureValue: 98,
                category: 1996
            },
            {
                value: 100, comparativeMeasureValue: 96,
                category: 1995
            },
            {
                value: 110, comparativeMeasureValue: 92,
                category: 1994
            },
            {
                value: 100, comparativeMeasureValue: 103,
                category: 1993
            },
            {
                value: 94, comparativeMeasureValue: 93,
                category: 1992
            },
            {
                value: 91, comparativeMeasureValue: 95,
                category: 1991
            },
            {
                value: 107, comparativeMeasureValue: 103,
                category: 1990
            },
            {
                value: 101, comparativeMeasureValue: 102,
                category: 1989
            },
            {
                value: 119, comparativeMeasureValue: 112,
                category: 1988
            }];
         }
         }
{% endhighlight %}



Once the DataSource property is assigned with the required values, you can bind the variable names used in the JSON data to the corresponding fields of the BulletGraph as shown in the following code example.
 
{% highlight javascript %}

export class BasicUse {
constructor() {
 this.fields= {dataSource: this.localData, category: "category",
                featureMeasures: "value",
                comparativeMeasure: "comparativeMeasureValue"};
}
}

{% endhighlight %}
{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-bullet-graph id="graph" e-fields.bind="fields">
        </ej-bullet-graph>
        </div>
</template>
</body>
</html>

{% endhighlight %}

### Set Default and Scale Values

You can plot any number of measure bars within the BulletGraph by increasing the height and width of the control to locate all the measure bars within the graph. Set the QualitativeRangeSize and QuantitativeScaleLength properties according to the following code example.

By default, the BulletGraph is rendered in the horizontal orientation with its flow direction set to Forward. In this example, to achieve the desired output, change the horizontal orientation to vertical orientation with the flow direction set to Backward.

Minimum, Maximum and Interval values for the QuantitativeScale of the BulletGraph are set, as illustrated in the following code example. The ticks and labels within the scale are also positioned.


{% highlight javascript %}

export class BasicUse {
constructor() {
 this.quantitativeScaleSettings = { 
                minimum: 70,
                maximum: 130,
                interval: 10,
                tickPosition: ej.datavisualization.BulletGraph.TickPosition.Far,
                labelSettings: {
                position: ej.datavisualization.BulletGraph.LabelPosition.Below, offset: 14, size: 10
               }
               };
}
}

{% endhighlight %}
{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-bullet-graph id="graph" e-quantitative-scale-settings.bind="quantitativeScaleSettings">
        </ej-bullet-graph>
        </div>
</template>
</body>
</html>

{% endhighlight %}


![](Getting-Started_images/Getting-Started_img3.jpg)


The above image illustrates the BulletGraph without any ranges displayed in the background.

### Add Qualitative Ranges

By default, 3 ranges are displayed in the BulletGraph control during the initial rendering of the control with its default values. To customize it, you can set appropriate values for the RangeEnd and RangeStroke properties.  Any number of QualitativeRanges can be added to the control.


{% highlight javascript %}

export class BasicUse {
constructor() {
  this.qualitativeRanges = [{rangeEnd: 90}, {rangeEnd: 110}, {rangeEnd: 130,RangeStroke:"#CDC9C9"}];
}
}

{% endhighlight %}
{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-bullet-graph id="graph" e-qualitative-ranges.bind="qualitativeRanges">
        </ej-bullet-graph>
        </div>
</template>
</body>
</html>

{% endhighlight %}


After adding QualitativeRanges to the BulletGraph, the control appears as follows.



![](Getting-Started_images/Getting-Started_img4.jpg)


### Ticks and Measure Bars Customization

You can do the following code changes in the quantitative scale to customize the tick size, the color of the feature bar and the comparative measure symbols.

{% highlight javascript %}

export class BasicUse {
constructor() {
  this.quantitativeScaleSettings = { 
              minimum: 70,
                maximum: 130,
                interval: 10,
                tickPosition: ej.datavisualization.BulletGraph.TickPosition.Far,
                labelSettings: {
                position: ej.datavisualization.BulletGraph.LabelPosition.Below, offset: 14, size: 10
               },
                majorTickSettings:{width:1, size:7},
                minorTickSettings:{width:1},
                comparativeMeasureSettings:{stroke:"#507786"},
                featuredMeasureSettings:{stroke: "#169DD8"}
  };
}
}

{% endhighlight %}
{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-bullet-graph id="graph" e-quantitative-scale-settings.bind="quantitativeScaleSettings">
        </ej-bullet-graph>
        </div>
</template>
</body>
</html>

{% endhighlight %}




When you customize the ticks and measure bar, the BulletGraph appears as follows.



![](Getting-Started_images/Getting-Started_img5.jpg)

### Add Caption and Subtitle

You can add the following code example to display an appropriate Caption and Subtitle to the BulletGraph.


{% highlight javascript %}
export class BasicUse {
constructor() {
 this.captionSettings =
  {
                textAngle: 0,
                location: { x: 470, y: 270 },
                text: "Monsoon Rainfall - Actual vs Forecast",
                font: { fontFamily: 'Segoe UI', size: '20px', fontWeight: ej.datavisualization.BulletGraph.FontWeight.Normal, opacity: 1 },
                subTitle: { 
                 textAngle: -90,
                    text: "Rainfall (mm)", location: { x: 180, y: 4 }, 
                    font: { fontFamily: 'Segoe UI', size: '14px',
                    fontWeight: 'ej.datavisualization.BulletGraph.FontWeight.Normal', opacity: 1} 
                    }
      };
}
}
{% endhighlight %}
{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-bullet-graph id="graph" e-caption-settings.bind="captionSettings">
        </ej-bullet-graph>
        </div>
</template>
</body>
</html>

{% endhighlight %}



The following screenshot displays a BulletGraph with a Caption and Subtitle.



![](Getting-Started_images/Getting-Started_img6.jpg)

### Show Tooltip

You can use a Tooltip in your application to display the values of forecasted rainfall, actual rainfall received in millimeter and also the appropriate year. The Tooltip Visible property is set to True to enable the Tooltip option. To set the template Tooltip, you can pass the template id to it as illustrated in the following code example.


{% highlight javascript %}

export class BasicUse {
constructor() {
 this.tooltipSettings = {visible:true,template:"Tooltip"};		
}
}
{% endhighlight %}
{% highlight html %}

<!DOCTYPE html>
<body>
<template>
<div>
     <ej-bullet-graph id="graph" e-tooltip-settings.bind="tooltipSettings">
        </ej-bullet-graph>
        </div>
</template>
</body>
</html>
<div id="Tooltip"style="display:none; width:125px;padding-top: 10px;padding-bottom:10px">



<div align="center"style="font-weight:bold">

           Rainfall </div>

<table>

<tr><td>Actual</td>

<td>: {{:currentValue}}mm</td></tr>

<tr><td>Forecast</td>

<td>: {{:targetValue}}mm</td></tr>

<tr><td>Year</td>

<td>: {{:category}}</td></tr>

</table>

</div>

{% endhighlight %}

The following screenshot displays a customized BulletGraph.

![](Getting-Started_images/Getting-Started_img7.jpg)


