---
layout: post
title: getting started
description: getting started
platform: aurelia
control: Group Button
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the Aurelia Group Button with the step-by-step instructions.

## Create a Group Button

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).

****We configured a Syncfusion template project in GitHub repository [syncfusion-template-repository](https://github.com/aurelia-ui-toolkits/syncfusion-template-repository). The above link is explain set of commands to run and install the required packages for Syncfusion Aurelia application.

Create a new HTML file with required refrences given in above link and follow the below steps.

Create the GroupButton with group button tag in div inside the body tag as like below

{% highlight html %}

        <div id="groupbutton"  ej-group-button/>

{% endhighlight %}

Create an groupbutton folder inside src/samples/ location.

Create **html** file _GroupButton.html_ inside src/samples/groupbutton folder and use the below code example to render the Aurelia GroupButton component.

Create **div** element with in template as below.

{% highlight html %}

    <template>

        <table class='container-fluid'>

            <tbody class='container-fluid'>

                <tr class='row'>

                    <td class='col-md-4'>

                        <div id="groupbutton"  ej-group-button="e-data-source.bind:localData"/>

                    </td>

                </tr>         

            </tbody>

        </table>      

    </template>


{% endhighlight %}

![](gettingstarted_images\gettingstarted_img1.png)

To render Aurelia GroupButton, Create GroupButton.js using below the code example inside the src/samples/groupbutton.

{% highlight javascript %}

    export class groupbutton {



    constructor() {







        this.localData = [



            { text: 'Day', contentType: 'textonly' },



            { text: 'Week', contentType: 'textonly' },



            { text: 'Work Week', contentType: 'textonly' },



            { text: 'Month', contentType: 'textonly', selected: 'selected' },



            { text: 'Agenda', contentType: 'textonly' }

        ];



    }



    }
{% endhighlight %}

To configure the navigation for the created GroupButton Sample, create the app.js by using below code snippet.

{% highlight javascript %}

    export class App {

    configureRouter(config, router) {

        config.title = 'Aurelia Syncfusion';

        config.map([

               { route:'groupbutton',   name:'groupbutton', moduleId:'samples/groupbutton/groupbutton',  nav:true, title:'groupbutton'}

        ]);



        this.router = router;

    }

    }
{% endhighlight %}






## Data Source

GroupButton can populate the button items based on data source and by specifying the associated fields.

This DataSource need to be bounded with the group button component like below.


{% highlight html %}

    <div id="groupbutton"  ej-group-button="e-data-source.bind:localData"/>

{% endhighlight %}


{% highlight javascript %}

    export class groupbutton {



    constructor() {



        this.roundedCorner = true;



        this.localData = [



            { text: 'Day', contentType: 'textonly' },



            { text: 'Week', contentType: 'textonly' },



            { text: 'Work Week', contentType: 'textonly' },



            { text: 'Month', contentType: 'textonly', selected: 'selected' },



            { text: 'Agenda', contentType: 'textonly' }

        ];



    }



    }


{% endhighlight %}


The above code will render the following output in the screen.

![](datasource_images\datasource_img1.png)

