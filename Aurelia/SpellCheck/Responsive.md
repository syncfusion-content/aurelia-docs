---
title: SpellCheck - Responsive
description: How to set the spellcheck, responsive to screen resolutions
platform: Aurelia
control: spellcheck
documentation: ug
keywords: Responsive, Responsive spellcheck dialog, Resize spellcheck dialog
---
# Responsive

The SpellCheck control has support for responsive behavior based on client browser’s width and height. To enable responsive, `isResponsive` property should be true.

The following code example describes the above behavior.

{% highlight html %}

<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-is-responsive.bind="Responsive">
            Facebook is a social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo, Andrew McCollum, Dustin and Chris Hughes.
            The fouders had initially limited the websites membrship to Harvard students, but later expanded it to collges in the Boston area, the Ivy League, and Stanford Univrsity. It graually added support for students at various other universities and later to high-school students.
        </ej-spell-check>
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class SpellCheck {
    constructor() {
      this.dictionarySettings = {
        dictionaryUrl: 'http://js.syncfusion.com/demos/ejservices/api/SpellCheck/CheckWords',
        customDictionaryUrl: 'http://js.syncfusion.com/demos/ejservices/api/SpellCheck/AddToDictionary'
      };
      this.Responsive = "true";
    }
}

{% endhighlight %}

The dialog of spell check control is rendering based on the client browser’s width and height. Refer to the following code to render the SpellCheck dialog control with responsive.

{% highlight html %}

<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-is-responsive.bind="Responsive">
            Facebook is a social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo, Andrew McCollum, Dustin and Chris Hughes.
            The fouders had initially limited the websites membrship to Harvard students, but later expanded it to collges in the Boston area, the Ivy League, and Stanford Univrsity. It graually added support for students at various other universities and later to high-school students.
        </ej-spell-check>
    </div>
    <div class="spellbutton">
        <input ej-button="e-text:Spell check" e-on-click.trigger="showErrors($event)" id="CheckSpell" />
    </div>
</template>

{% endhighlight %}

{% highlight javascript %}

export class SpellCheck {
    constructor() {
      this.dictionarySettings = {
        dictionaryUrl: 'http://js.syncfusion.com/demos/ejservices/api/SpellCheck/CheckWords',
        customDictionaryUrl: 'http://js.syncfusion.com/demos/ejservices/api/SpellCheck/AddToDictionary'
      };
      this.Responsive = "true";
    }
    showErrors() {
      this.SpellCheck.showInDialog();
    }
}

{% endhighlight %}

Mobile Rendering Screenshot:

![](Responsive_Images/Responsive_Image.png)