---
layout: post
title: Getting Started for Aurelia RichTextEditor
description: getting started 
platform: Aurelia
control: RichTextEditor Control
documentation: ug
keywords: ejrte, rte, js rte
---

# Getting Started 

This section helps to understand the getting started of RTE control with the step-by-step instruction.

## Initialize RTE Control

* To create Syncfusion Aurelia application refer [Aurelia Getting Started documentation](https://help.syncfusion.com/aurelia/overview#getting-started "").
* Create `RTE` folder inside `src/samples` location.
* Create `RTE.html` file inside  `src/samples/rte` folder and use the below code for rendering RichTextEditor component 

{% highlight html %}

  <template>
    <div>
        <textarea id="rteSample" rows="10" cols="30" ej-rte="e-width:100%" ></textarea>
    </div>
</template>

{% endhighlight %}

* Create `rte.js` file inside `src/samples/rte` folder with below code snippet.

{% highlight js %}

   export class DefaultFunctionalities { }

{% endhighlight %}

The following screenshot displays a RTE widget.

![](/js/RichTextEditor/Getting-Started_images/Getting-Started_img1.png)

## Toolbar–Configuration

You can configure a toolbar with the tools as your application requires.

{% highlight html %}
 
 <template> 
    <div>
        <textarea id="rteSample" rows="10" cols="30" style="width: 740px; height: 440px" ej-rte="e-list.bind:list;e-tools.bind:tools"></textarea>
    </div>
</template>

{% endhighlight %}

{% highlight js %}

export class AllToolsRTE {
    tool= {style: ["bold", "italic"], lists: ["unorderedList", "orderedList"],doAction: ["undo", "redo"],links: ["createLink"],images: ["image"] };
    list = ["style", "lists", "doAction", "links", "images"];
    constructor() { 
    this.list = this.list;
    this.tools = this.tool;
  }
}

{% endhighlight %}

The following screenshot displays a RTE widget.

![](/js/RichTextEditor/Getting-Started_images/Getting-Started_img2.png)

## Setting and Getting Content

You can set the content of the editor as follows.

{% highlight html %}

 <template> 
    <div>
        <textarea id="rteSample" rows="10" cols="30" style="width: 740px; height: 440px" ej-rte="e-list.bind:list;e-tools.bind:tools">
                  &lt;p&gt;&lt;b&gt;Description:&lt;/b&gt;&lt;/p&gt;
    &lt;p&gt;The Rich Text Editor (RTE) control is an easy to render in
    client side. Customer easy to edit the contents and get the HTML content for
    the displayed content. A rich text editor control provides users with a toolbar
    that helps them to apply rich text formats to the text entered in the text
    area. &lt;/p&gt;
    &lt;p&gt;&lt;b&gt;Functional
    Specifications/Requirements:&lt;/b&gt;&lt;/p&gt;
    &lt;ol&gt;&lt;li&gt;&lt;p&gt;Provide
    the tool bar support, it’s also customizable.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Options
    to get the HTML elements with styles.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Support
    to insert image from a defined path.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Footer
    elements and styles(tag / Element information , Action button (Upload, Cancel))&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Re-size
    the editor support. &lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Provide
    efficient public methods and client side events.&lt;/p&gt;&lt;/li&gt;&lt;li&gt;&lt;p&gt;Keyboard
    navigation support.&lt;/p&gt;&lt;/li&gt;&lt;/ol&gt;
        </textarea>
    </div>
</template>

{% endhighlight %}

{% highlight js %}

export class AllToolsRTE {
    tool= {style: ["bold", "italic"], lists: ["unorderedList", "orderedList"],doAction: ["undo", "redo"],links: ["createLink"],images: ["image"] };
    list = ["style", "lists", "doAction", "links", "images"];
    constructor() { 
    this.list = this.list;
    this.tools = this.tool;
  }
}

{% endhighlight %}

The following screenshot displays a RTE widget.

![](/js/RichTextEditor/Getting-Started_images/Getting-Started_img3.png)