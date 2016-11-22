---
title: Getting Started for Aurelia PDF viewer
description: PDF viewer 
platform: Aurelia
control: PDF viewer
documentation: ug
keywords: ejPdfViewer, PDF viewer, js pdfviewer
---

# Getting Started

Before we start with the PDF viewer control, please refer [this page](https://help.syncfusion.com/aurelia/overview#getting-started) for general information regarding integrating Syncfusion widgets.

For quick start, we already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

    > git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
    > cd syncfusion-template-repository
    > npm install
    > jspm install

{% endhighlight %}

### Control Initialization

The below steps describe about, how to create Syncfusion Aurelia PDF viewer component.

    Create `pdfviewer` folder inside `src/samples/` location.
    Create `pdfviewer.html` file inside `src/samples/pdfviewer` folder and use the below code example to render the PDF viewer component.
	
{% highlight html %}

<template>
  <require from="./pdfviewer.css"></require>
  <div>
    <ej-pdf-viewer id="PdfViewer" e-service-url="http://js.syncfusion.com/ejservices/api/PdfViewer"></ej-pdf-viewer>
  </div>
</template>

{% endhighlight %}

* Create `pdfviewer.js` file inside `src/samples/pdfviewer` folder with below code snippet.

{% highlight html %}

export class BasicUse {

  constructor() {}

}

{% endhighlight %}

* Create `pdfviewer.css` file inside `src/samples/pdfviewer` folder with below code snippet.

{% highlight html %}

ej-pdf-viewer {
    display: block;
    height: 500px;
}

{% endhighlight %}

Now, the PDF viewer control will be rendered with the default PDF document, which is used in the service.

![](getting-started_images/pdfviewer.png)
