---
layout: post
title: getting started
description: getting started
platform: aurelia
control: signature
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the Signature component in Aurelia with the step-by-step instructions.

## Create an Signature component

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).

We configured a Syncfusion template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). The above link is explain set of commands to run and install the required packages for Syncfusion Aurelia application.

Create a new HTML file and include the below code:

{% highlight html %}
    <!DOCTYPE html>
    <html>
    <head>
        <link href="//cdn.syncfusion.com/{{site.releaseversion}}/js/web/flat-azure/ej.web.all.min.css" rel="stylesheet" />
        <script src="node_modules/core-js/client/shim.min.js"></script>
        <script src="node_modules/zone.js/dist/zone.js"></script>
        <script src="node_modules/reflect-metadata/Reflect.js"></script>
        <script src="node_modules/systemjs/dist/system.src.js"></script>
        <script src="https://code.jquery.com/jquery-3.0.0.min.js"></script>
        <script src="http://cdn.syncfusion.com/js/assets/external/jsrender.min.js" type="text/javascript"></script>
        <script src="http://cdn.syncfusion.com/{{site.releaseversion}}/js/web/ej.web.all.min.js" type="text/javascript"></script>
        <script src="systemjs.config.js"></script>
    </head>
    <body>
        <ej-app>Loading...</ej-app>
    </body>
    </html>


{% endhighlight %}



Create an autocomplete folder inside src/samples/ location.

Create **html** file inside src/samples/signature folder and use the below code example to render the Aurelia AutoComplete component.

Properties can be defined with `e-` prefix and long text properties needs to separate by `-`. E.g. (`e-watermark-text`, `e-width`). 

Create **div** element with in template as below.

{% highlight html %}
       <template>
              <div id="SignatureCtrl">
                  <div id="control" ng-controller="SignatureCtrl">
                      <ej-signature id="signature" e-height="400px">
</ej-signature>
                  </div>
              </div>
          </template>

{% endhighlight %}



To render the Aurelia signature using below code.

{% highlight js %}

    export class BasicUse {
                constructor() {
                }
            }

{% endhighlight %}



The following screenshot is the output for the above code.

![https://help.syncfusion.com/js/signature/Getting_Started_images/createsignaturecontrol_img1.png](Getting_Started_images\createansignaturecomponent_img1.png)


## Adjusting Signature Size

You can customize the width and height of the Signature by **e-width** and **e-height** properties. These properties completely depend on signature canvas. The width and height are adjusted within the signature canvas.

The following code example is used to render the Signature component with customized width and height.

Create **div** element with in template as below.

{% highlight html %}


       <template>

              <div id="SignatureCtrl">

                  <div id="control" ng-controller="SignatureCtrl">

                      <ej-signature id="signature" e-height="300px" e-height=”200px” e-is-responsive.bind="response" >
</ej-signature>
                  </div>
              </div>

          </template>


{% endhighlight %}



To render the Aurelia signature using below code.

{% highlight js %}


export class BasicUse {
                constructor() {
                    this.response = true;
                }
            }



{% endhighlight %}



The following screenshot illustrates signature with customized width and height.

![https://help.syncfusion.com/js/signature/Getting_Started_images/adjustingsignaturesize_img1.png](Getting_Started_images\adjustingsignaturesize_img1.png)



