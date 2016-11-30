---
title: Getting Started for Accordion
description: Getting Started for  Accordion
platform: Aurelia
control: Accordion
documentation: Ug
keywords: ejaccordion, js accordion, accordion
---
# Getting started

This section explains briefly about how to create an **Accordion** in your application with **Aurelia**.

## Configure Accordion

This section encompasses the details on how you can configure the **Accordion** control in your application and customize it with various properties such as multiple open, rounded corner and icons for the **Accordion** header according to your requirement.

The following screenshot illustrates you the usage of **Accordion** control in listing the controls under the Essential Studio products. 

![](Getting-Started-images/Getting-Started_img1.png) 

The usage of **Accordion** control is described in the following sections.

## Create a Simple Accordion in Aurelia

Before we start with Accordion, please refer [this page](https://help.syncfusion.com/aurelia/overview#getting-started) page for general information regarding integrating Syncfusion widget’s.

For quick start, we already configured a template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight html %}

    > git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository"
    > cd syncfusion-template-repository
    > npm install
    > jspm install

{% endhighlight %}

The below steps describes to create Syncfusion Aurelia Accordion component.

    Create Accordion folder inside src/samples/ location.
    Create Accordion.html file inside src/samples/Accordion folder and use the below code example to render the Accordion component.

{% highlight html %}

     <template>
      <div>
        <ej-accordion id="multiAccordion" style="width: 500px">
          <h3><a href="#">Essential Studio ASP.NET</a></h3>
           <div>
            <ul>
            <li>
                <h4>DocIO</h4>
            </li>
            <li>
                <h4>Pdf  </h4>
            </li>
            <li>
                <h4>Gauge  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
            <li>
                <h4>Tools </h4>
            </li>
            </ul>
           </div>
            <h3><a href="#">Essential Studio ASP.NET MVC</a></h3>
            <div>
               <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
              </ul>
            </div>
          <h3><a href="#">Essential Studio Javascript</a></h3>
           <div>
            <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
          </ul>            
         </div>
        </ej-accordion>
      </div>
    </template>
    
{% endhighlight %}

Create the Accordion control as follows.

{% highlight html %}
  
     export class MultipleOpenAccordion {
   }

{% endhighlight %}

You can execute the above code example to display the Accordion control with simple control list.

![](Getting-Started-images/Getting-Started_img2.png) 

You can customize the Accordion control using various properties. The Accordion control properties and its default values are described in the following section.

## Configure Multiple Open

You can have multiple **Accordion** tabs opened to view all products at a time. To achieve this set the **enableMultipleOpen** property of the **Accordion** control to true.

N> enableMultipleOpen property is false by default.

You can also open all the panels during initialization using the **selectedItems** property of the **Accordion** control. The following code sample illustrates the opening of multiple tabs by passing the tab index values of tab.

{% highlight html%}
    
	<template>
      <div>
         <ej-accordion id="multiAccordion" style="width: 500px" e-enable-multiple-open.bind="multipleOpen" e-selected-items.bind="selecteditems">
          <h3><a href="#">Essential Studio ASP.NET</a></h3>
           <div>
            <ul>
            <li>
                <h4>DocIO</h4>
            </li>
            <li>
                <h4>Pdf  </h4>
            </li>
            <li>
                <h4>Gauge  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
            <li>
                <h4>Tools </h4>
            </li>
            </ul>
           </div>
            <h3><a href="#">Essential Studio ASP.NET MVC</a></h3>
            <div>
               <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
              </ul>
            </div>
          <h3><a href="#">Essential Studio Javascript</a></h3>
           <div>
            <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
          </ul>            
         </div>
        </ej-accordion>
      </div>
    </template>
    
{% endhighlight %}

{% highlight html%}

    export class MultipleOpenAccordion {
      selecteditems:int;
      constructor() {
       this.multipleOpen = true;
	   this.selecteditems=[0,1,2];
       }
      } 
{% endhighlight %}

**Accordion** control with **enableMultipleOpen** property is illustrated in the following screen shot.

![](Getting-Started-images/Getting-Started_img3.png) 

### Setting rounded corner

**Accordion** control, by default, is rendered in a regular rectangle. You can modify the regular rectangles with rounded corners by setting the **showRoundedCorner** property to **True**.

N> showRoundedCorner property is False by default.

{% highlight html%}

    <template>
      <div>
        <ej-accordion id="multiAccordion" style="width: 500px" e-enable-multiple-open.bind="multipleOpen" e-selected-items.bind="selecteditems" e-show-rounded-corner="true">
          <h3><a href="#">Essential Studio ASP.NET</a></h3>
           <div>
            <ul>
            <li>
                <h4>DocIO</h4>
            </li>
            <li>
                <h4>Pdf  </h4>
            </li>
            <li>
                <h4>Gauge  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
            <li>
                <h4>Tools </h4>
            </li>
            </ul>
           </div>
            <h3><a href="#">Essential Studio ASP.NET MVC</a></h3>
            <div>
               <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
              </ul>
            </div>
          <h3><a href="#">Essential Studio Javascript</a></h3>
           <div>
            <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
          </ul>            
         </div>
        </ej-accordion>
      </div>
    </template>
	
{% endhighlight %}

The following screenshot illustrates the **Accordion** control with rounded corners.

![](Getting-Started-images/Getting-Started_img4.png) 

## Customize Icon

You can customize the **Header** icon using **customIcon** property. This property has two features such as **header** and **selectedHeader**. By default, the classes of **header** and **selectedHeader** are **e-collapse** and **e-expand** respectively**.**

You can change the + and - symbols in the **Accordion** header, that are the default icons with Up or Down arrow icons. 

Up or Down arrow icons are available in **e-arrowheadup** and **e-arrowheaddown** classes respectively in the ej.widgets.core.min.css stylesheets from the sample. 

You can set the Up or Down arrow icon to **Accordion** header, by adding **e-arrowheadup** and **e-arrowheaddown** class to **selectedHeader** and **header** properties respectively.

{% highlight html %}

    <template>
      <div>
        <ej-accordion id="multiAccordion" style="width: 500px" e-enable-multiple-open.bind="multipleOpen" e-selected-items.bind="selecteditems" e-show-rounded-corner="true" e-custom-icon.bind="custom">
          <h3><a href="#">Essential Studio ASP.NET</a></h3>
           <div>
            <ul>
            <li>
                <h4>DocIO</h4>
            </li>
            <li>
                <h4>Pdf  </h4>
            </li>
            <li>
                <h4>Gauge  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
            <li>
                <h4>Tools </h4>
            </li>
            </ul>
           </div>
            <h3><a href="#">Essential Studio ASP.NET MVC</a></h3>
            <div>
               <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
              </ul>
            </div>
          <h3><a href="#">Essential Studio Javascript</a></h3>
           <div>
            <ul>
            <li>
                <h4>Chart </h4>
            </li>
            <li>
                <h4>Grid  </h4>
            </li>
            <li>
                <h4>Gantt  </h4>
            </li>
            <li>
                <h4>Schedule  </h4>
            </li>
            <li>
                <h4>Diagram  </h4>
            </li>
          </ul>            
         </div>
        </ej-accordion>
      </div>
    </template>
	
{% endhighlight %}

{% highlight html %}

       export class MultipleOpenAccordion {
            selecteditems:int;
              constructor() {
                this.multipleOpen = true;
	            this.selecteditems=[0,1,2];
	            this.custom={header: "e-arrowheaddown",selectedHeader: "e-arrowheadup"};
              }
          }

{% endhighlight %}

The following screenshot illustrates the customization of **selectedHeader** and **header** of the **Accordion** control.

![](Getting-Started-images/Getting-Started_img5.png) 

