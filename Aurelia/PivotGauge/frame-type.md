---
title: Frame-Type
description: frame type
platform: Aurelia
control: PivotGauge
documentation: ug
api: /api/js/ejpivotgauge
---

# Frame type

## Full circle

Full circle frame allows the pivot gauge to display in a circular shape. The frame type can be set by using the [`frameType`](/api/js/ejcirculargauge#members:frame) property. By default, the frame type is "fullCircle".

{% highlight html %}

<template>
  <div>
    <ej-pivot-gauge id="pivotGauge"  e-frame.bind= "frame">
    </ej-pivot-gauge>
  </div>
</template>

{% endhighlight %}

{% highlight javascript %}

    export class BasicUse {
       constructor() {
          this.frame = { frameType = 'fullcircle' };
    }
 }

{% endhighlight %}

![](frame-type_images/FullCircle.png)

## Half circle

The half circle frame allows the pivot gauge to display in a semi-circular shape. For this, the frame type should be set as "halfCircle" within the [`frameType`](/api/js/ejcirculargauge#members:frame) property and should set the `startAngle` and `sweepAngle` for the pivot gauge in the  [`scales`](/api/js/ejcirculargauge#members:scales) property.

{% highlight html %}

<template>
  <div>
    <ej-pivot-gauge id="pivotGauge"  e-frame.bind= "frame" e-scales.bind="scales">
    </ej-pivot-gauge>
  </div>
</template>

{% endhighlight %}

{% highlight javascript %}

    export class BasicUse {
       constructor() {
          this.frame = { frameType = 'halfcircle',
          halfCircleFrameStartAngle: 180, halfCircleFrameEndAngle: 360 };

          this.scales = { //...
          startAngle: 180, sweepAngle: 180,
          //... }
    }
 }

{% endhighlight %}

![](frame-type_images/HalfCircle.png)