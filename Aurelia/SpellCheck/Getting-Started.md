---
title: Getting started with SpellCheck component	
description: Rendering a basic SpellCheck
platform: Aurelia
control: spellcheck
documentation: ug
keywords: ejSpellCheck, spellcheck, spellcheck widget, js spellcheck, getting started, initialization, service reference
---
# Getting Started 

This section helps to understand the getting started of the Aurelia SpellChecker with the step-by-step instructions.

## Create a SpellCheck control in Aurelia

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation.](https://help.syncfusion.com/aurelia/overview)

We already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

> git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
> cd syncfusion-template-repository
> npm install
> jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia SplitButton component.

* Create `SpellCheck` folder inside `src/samples/` location.
* Create `SpellCheck.html` file inside `src/samples/SpellCheck` folder and use the below code example to render the SpellCheck component.

{% highlight html %}

<template>
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-context-menu-settings.bind="ContextMenu">
            Facebook is a social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo, Andrew McCollum, Dustin and Chris Hughes.
            The fouders had initially limited the websites membrship to Harvard students, but later expanded it to collges in the Boston area, the Ivy League, and Stanford Univrsity. It graually added support for students at various other universities and later to high-school students.
        </ej-spell-check>
</template>

{% endhighlight %}

* Create `SpellCheck.js` file with the below code snippet inside `src/samples/SpellCheck` folder.

{% highlight javascript %}

export class SpellCheck {
    constructor() {
      this.dictionarySettings = {
        dictionaryUrl: 'http://js.syncfusion.com/demos/ejservices/api/SpellCheck/CheckWords',
        customDictionaryUrl: 'http://js.syncfusion.com/demos/ejservices/api/SpellCheck/AddToDictionary'
      };
    }
}

{% endhighlight %}

* Now, we are going to configure the navigation for created SpellCheck sample in `src/app.js` file.

{% highlight javascript %}

export class App {
 configureRouter(config, router) {
  config.title = 'Aurelia Syncfusion';
  config.map([
   { route: ['', 'welcome'], name: 'welcome', moduleId: 'welcome',                              
                nav: true, title: 'Welcome' },
   { route: 'child-router',  name: 'child-router', moduleId: 'child-router',                         
                nav: true, title: 'Child Router' },
   { route: 'button',        name: 'button', moduleId: 'samples/button/button',                
                nav: true, title: 'Button' },
   { route: 'SpellCheck',        name: 'SpellCheck',       moduleId: 'samples/SpellCheck/SpellCheck',                
                nav: true, title: 'SpellCheck' }
 ]);
 this.router = router;
 }
}

{% endhighlight %}

* To run the application, execute the following command.

{% highlight javascript %}

gulp watch

{% endhighlight %}

## Spell Checking

To spell check the content of the target element, you need to add one button and calling any one of the SpellCheck method `showInDialog` or `validate` by clicking the button to highlight the error words.

The following code example depicts that checking the spelling of the target element through the "validate" method.

{% highlight html %}

<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings">
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
    }
    showErrors() {
      this.SpellCheck.validate(); // highlighting the error word in the target area itself
    }
}

{% endhighlight %}