---
layout: post
title: Behavior-Settings
description: behavior settings
platform: aurelia
control: ColorPicker
documentation: ug
---

# Behavior Settings

## showPreview

The **ColorPicker** control provides live preview support for current cursor selection color and selected color. **showPreview** property allows you to preview the selected color in the picker or from the palette.

The **showPreview** property is Boolean type and its default value is true.

In the **HTML** page, add a **&lt;input&gt;** element to render **ColorPicker** widget

{% highlight html %}

<template>
       <input id="colorpick" type="text" ej-color-picker="e-value.bind:colorvalue;e-show-preview.bind:showPreview" />
</template>

{% endhighlight %}

{% highlight javascript %}

export class Default {
    constructor() {
      this.colorvalue = '#278787';
      this.showPreview = true;
    }
}

{% endhighlight %}

The following screenshot displays the output of the above code example.

![](/TypeScript/ColorPicker/Behavior-Settings_images/Behavior-Settings_img1.png) 

## showRecentColors

The **ColorPicker** control allows you to store the color values in custom list by using **showRecentColors** property. The **ColorPicker** keeps up to 11 colors in a custom list. By clicking the add button, the selected color from picker or palette gets added in the recent color list.  

The **showRecentColors** property is Boolean type and its default value is false.

In the **HTML** page, add a **&lt;input&gt;** element to render **ColorPicker** widget.


{% highlight html %}

<template>
       <input id="colorpick" type="text" ej-color-picker="e-value.bind:colorvalue;e-show-recent-colors.bind:showRecentColors" />
</template>

{% endhighlight %}

{% highlight javascript %}

export class Default {
    constructor() {
      this.colorvalue = '#278787';
      this.showRecentColors = true;
    }
}

{% endhighlight %}

The following screenshot displays the output of the above code example.

![](/TypeScript/ColorPicker/Behavior-Settings_images/Behavior-Settings_img2.png) 


## enableOpacity

The **ColorPicker** control allows you to enable or disable the opacity slider. You can achieve this by using the **enableOpacity** property. 

The **enableOpacity** property is Boolean type and its default value is true.

In the **HTML** page, add a **&lt;input&gt;** element to render **ColorPicker** widget


{% highlight html %}

<template>
       <input id="colorpick" type="text" ej-color-picker="e-value.bind:colorvalue;e-enable-opacity.bind:enableOpacity" />
</template>

{% endhighlight %}

{% highlight javascript %}

export class Default {
    constructor() {
      this.colorvalue = '#278787';
      this.enableOpacity = false;
    }
}

{% endhighlight %}

The following screenshot displays the output of the above code example.

![](/TypeScript/ColorPicker/Behavior-Settings_images/Behavior-Settings_img3.png) 

## columns

The palette model consists of color values in the rows and columns order. Palette only consists of predefined colors and allows you to select anyone color from it. The **columns** property allows you to modify the number of columns in palette model. 

The **columns** property is Number type and its default value is 10.

In the **HTML** page, add a **&lt;input&gt;** element to render **ColorPicker** widget

{% highlight html %}

<template>
       <input id="colorpick" type="text" ej-color-picker="e-value.bind:colorvalue;e-columns.bind:columns" />
</template>

{% endhighlight %}

{% highlight javascript %}

export class Default {
    constructor() {
      this.colorvalue = '#278787';
      this.columns = 9;
    }
}

{% endhighlight %}


The following screenshot displays the output of the above code example.

![](/TypeScript/ColorPicker/Behavior-Settings_images/Behavior-Settings_img4.png) 

