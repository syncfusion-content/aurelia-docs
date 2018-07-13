---
title: SpellCheck - Customization
description: SpellCheck Customization
platform: Aurelia
control: spellcheck
documentation: ug
keywords: customization, spellcheck customization, misspell word appearance, restrict suggestion count
---
# SpellCheck Customization

The SpellCheck provides option to customize for the following scenarios.

* Misspell Word Appearance
* Restrict Suggestion Count
    
## Misspell Word Appearance

The SpellCheck control provide the support(`misspellWordCss`) to display the error word in user defined style. By default displaying the error words with the red underline. 

The following code example depicts the way to customize the error word highlight (displaying error word with red color font and blue background).

{% highlight html %}

<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-misspell-word-css.bind="highlight">
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
      this.highlight = "highlight";
    }
    showErrors() {
      this.SpellCheck.showInDialog();
    }
}

{% endhighlight %}

{% highlight css %}

<style>
        .highlight {
            background-color: blue;
            color: red;
        }
</style>

{% endhighlight %}

## Restrict Suggestion Count

The SpellCheck control provides option (`maxSuggestionCount`) to restrict the count that the number of items displayed in the suggestion list.

The following code example describes the way to control the suggestion count.

{% highlight html %}

<template>
    <div id="SpellControl">
        <ej-spell-check id="SpellCheck" contenteditable="true" e-widget.bind="SpellCheck" e-dictionary-settings.bind="dictionarySettings" e-max-suggestion-count.bind="3">
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
      this.SpellCheck.showInDialog();
    }
}

{% endhighlight %}