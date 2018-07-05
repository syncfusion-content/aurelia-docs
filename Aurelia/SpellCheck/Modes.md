---
title: SpellCheck - Operations
description: SpellCheck Operations
platform: Aurelia
control: spellcheck
documentation: ug
keywords: operations, spellcheck modes, dialog mode, context menu mode,  custom menu, handling menu actions, handling dialog actions
---
# SpellCheck Operations

Essential SpellCheck provides two ways to perform the SpellCheck operation(error correction). They are,

* Dialog Mode 
* Context Menu Mode  

## Dialog Mode

### Description

SpellCheck provides the dialog mode option to perform the following SpellCheck operations.

* Ignore Once
* Ignore All
* Change
* Change All
* Add to Dictionary

### Open Dialog Mode

The following code snippet shows how to open the dialog to spell check the content.

{% highlight html %}

<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings">
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
    }
    attached() {
      setTimeout(()=>{
	    this.SpellCheck.showInDialog();
      }, 50);      
    }
}

{% endhighlight %}

### Handling Dialog Actions

To define the specific actions before the dialog window open, the client-side event `dialogBeforeOpen` can be used as depicted in the below code example.

{% highlight html %}

<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-dialog-before-open.trigger="onDialogBeforeOpen($event.detail)">
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
    }
    attached() {
      setTimeout(()=>{
	    this.SpellCheck.showInDialog();
      }, 50);      
    }
    onDialogBeforeOpen(args) {
        if (args.requestType == "dialogBeforeOpen") {
            alert("dialog before open event triggered");
        }
    }
}

{% endhighlight %}

The client-side event `dialogOpen` can be used to define the specific actions after the dialog window open as shown in the following code example.

{% highlight html %}

<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-dialog-open.trigger="onDialogOpen($event.detail)">
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
    }
    attached() {
      setTimeout(()=>{
	    this.SpellCheck.showInDialog();
      }, 50);      
    }
    onDialogOpen(args) {
        if (args.requestType == "dialogOpen") {
             alert(args.targetText);
        }
    }
}

{% endhighlight %}

The following code example used to define some actions after the dialog closing by using the client-side event `dialogClose`.

{% highlight html %}

<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-dialog-close.trigger="onDialogClose($event.detail)">
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
    }
    attached() {
      setTimeout(()=>{
	    this.SpellCheck.showInDialog();
      }, 50);      
    }
    onDialogClose(args) {
        if (args.requestType == "dialogClose") {
             alert(args.updatedText);
        }
    }
}

{% endhighlight %}

It is possible to predict the error word details before starting the SpellCheck operations through dialog mode by using the client side event `start`. The below code example describes the above behavior.

{% highlight html %}

<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-start.trigger="onSpellCheckStart($event.detail)">
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
    }
    attached() {
      setTimeout(()=>{
	    this.SpellCheck.showInDialog();
      }, 50);      
    }
    onSpellCheckStart(args) {
        if (args.requestType == "spellCheckDialog") {
           alert(JSON.stringify(args.errorWords));
        }
    }
}

{% endhighlight %}

You can get the corrected text content details before updating it into target element with the help of the client side event `complete` as mentioned in the below code example.

{% highlight html %}

<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-complete.trigger="onSpellCheckComplete($event.detail)">
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
    }
    attached() {
      setTimeout(()=>{
	    this.SpellCheck.showInDialog();
      }, 50);      
    }
    onSpellCheckComplete(args) {
        if (args.requestType == "changeErrorWord") {
           alert(args.targetText);
        }
    }
}

{% endhighlight %}

## Context Menu Mode

SpellCheck provides default context menu options to perform the SpellCheck operations. It also allows to define additional custom context menu options.

The options that are available under `contextMenuSettings` are as follows,

* `**enable**` - Enables/disables the context menu option in SpellCheck.
* `**menuItems**` - Contains the options to perform SpellCheck operations.

### Default Menu Options

The menu items contains the following options to perform the SpellCheck operation.

* Ignore All
* Add to Dictionary 

The following code snippet shows how to enable the context menu settings in SpellCheck and to make use of it with default available options.

{% highlight html %}
 
<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-context-menu-settings.bind="contextMenu">
           Facebook is a social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo, Andrew McCollum,Dustin and Chris Hughes. The fouders had initially limited the websites membrship to Harvard students, but later expanded it to collges in the Boston area, the Ivy League, and Stanford Univrsity. It graually added support for students at various other universities and later to high-school students.
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
      this.contextMenu ={
        enable: true,
        menuItems: [
                   { id: "IgnoreAll", text: "Ignore All" },
                   { id: "AddToDictionary", text: "Add To Dictionary" }
        ]
      };
    }
}

{% endhighlight %}

N> For default menu items, the id must be defined the same as mentioned in the above code example – as we have processed the menus based on this id within our source.

### Custom Menu Options

Apart from the default available options, it is also possible to add custom menu options to the context-menu list.

The following code example depicts how **to add the custom menu items** into the context menu settings.

{% highlight html %}
 
<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-context-menu-settings.bind="contextMenu">
           Facebook is a social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo, Andrew McCollum,Dustin and Chris Hughes. The fouders had initially limited the websites membrship to Harvard students, but later expanded it to collges in the Boston area, the Ivy League, and Stanford Univrsity. It graually added support for students at various other universities and later to high-school students.
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
      this.contextMenu ={
        enable: true,
        menuItems: [
                        { id: "Ignore", text: "IgnoreOnce" },
                        { id: "IgnoreAll", text: "Ignore All" },
                        { id: "AddToDictionary", text: "Add To Dictionary" }
                    ]
      };
    }
}

{% endhighlight %}

N> The **id** given for the custom menu items **must be unique**.

### Handling Menu Actions

The client-side event `contextClick` can be used to define specific actions when a click made on the custom menu items. The following code example describes the above behavior.

{% highlight html %}
 
<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-context-menu-settings.bind="contextMenu" e-context-click.trigger="onCustomMenuClick($event.detail)">
           Facebook is a social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo, Andrew McCollum,Dustin and Chris Hughes. The fouders had initially limited the websites membrship to Harvard students, but later expanded it to collges in the Boston area, the Ivy League, and Stanford Univrsity. It graually added support for students at various other universities and later to high-school students.
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
      this.contextMenu ={
        enable: true,
        menuItems: [
                        { id: "Ignore", text: "IgnoreOnce" },
                        { id: "IgnoreAll", text: "Ignore All" },
                        { id: "AddToDictionary", text: "Add To Dictionary" }
                    ]
      };
    }
    attached() {
      setTimeout(()=>{
	    this.SpellCheck.validate();
      }, 50);      
    }
    onCustomMenuClick(args) {
      if (args.selectedOption == "Ignore") {
         alert("Custom menu clicked");
      }
    }
}

{% endhighlight %}


It is possible to predict the target (error word) on which the right click is made with the use of the event `contextOpen`. The below code example shows how to block the display of context menu, when right clicked on the word by setting **args.cancel** as **true**.

{% highlight html %}
 
<template>    
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-context-menu-settings.bind="contextMenu" e-context-open.trigger="onBeforeOpen($event.detail)">
            Facebook is a social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo, Andrew McCollum,Dustin and Chris Hughes. The fouders had initially limited the websites membrship to Harvard students, but later expanded it to collges in the Boston area, the Ivy League, and Stanford Univrsity. It graually added support for students at various other universities and later to high-school students.
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
      this.contextMenu ={
        enable: true,
        menuItems: [
                        { id: "IgnoreAll", text: "Ignore All" },
                        { id: "AddToDictionary", text: "Add To Dictionary" }
                    ]
      };
    }
    attached() {
      setTimeout(()=>{
	    this.SpellCheck.validate();
      }, 50);      
    }
    onBeforeOpen(args) {
      if (args.selectedErrorWord == "Facebook") {
        args.cancel=true;
      }
    }
}

{% endhighlight %}

You can get the current spell check operation arguments details with the client-side event `validating`. The following code example describes the way to block the ignoreAll operation for the particular word.

{% highlight html %}
 
<template>    
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-validating.trigger="onSpellChecking($event.detail)">
           Facebook is a social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo, Andrew McCollum,Dustin and Chris Hughes. The fouders had initially limited the websites membrship to Harvard students, but later expanded it to collges in the Boston area, the Ivy League, and Stanford Univrsity. It graually added support for students at various other universities and later to high-school students.
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
    }
    attached() {
      setTimeout(()=>{
	    this.SpellCheck.validate();
      }, 50);      
    }
    onSpellChecking(args) {
      if (args.requestType == "ignoreAll" && args.ignoreWord=="textarea") {
          args.cancel=true;
      }
    }
}

{% endhighlight %}