---
layout: post
title: getting-started
description: getting started for Radiobutton with Aurelia
platform: aurelia
control: Radiobutton
documentation: ug
---

# GettingStarted

This section discloses the details on how to render and configure RadioButton component in an Aurelia application.

## Create RadioButton 

You can create an Aurelia application and add necessary scripts and styles with the help of the given [Aurelia Getting Started Documentation](https://help.syncfusion.com/aurelia/overview).
We have already configured a template project in GitHub repository syncfusion-template-repository. Run the below set of commands to clone the repository and install the required packages for Syncfusion Aurelia application.

{% highlight javascript %}

*	git clone "https://github.com/aurelia-ui-toolkits/syncfusion-template-repository" 
*	cd syncfusion-template-repository
*	npm install
*	jspm install

{% endhighlight %}

The below steps describes the steps to create Syncfusion Aurelia RadioButton component.

Create RadioButton folder inside src/samples/ location in sample files folder.

Create an HTML file (here RadioButton.html file) inside newly created folder and use the below code example to render the RadioButton component.

{% highlight HTML %}

<div>
    <br />
    Category
    <br />
    <br />
    <table>
        <tr>
            <td colspan="2">
                <input id="fresher" ej-radio-button="e-text:Fresher; e-name:category;e-value: fresher" />
            </td>
            <td>
                <input id="exp" ej-radio-button="e-checked.bind:value;e-text:Experienced; e-name:category;e-value: experienced" />
            </td>
        </tr>
    </table>
    <br />
    <br />
    Experienced
    <br />
    <br />
    <table>
        <tr>
            <td>
                <input id="exp1" ej-radio-button="e-checked.bind:value;e-text:1+ years; e-name:experience;e-value: 1+years" />

            </td>
            <td colspan="2">
                <input id="exp2" ej-radio-button="e-text:2.5+ years; e-name:experience;e-value: 2+years" />

            </td>
            <td colspan="2">
                <input id="exp5" ej-radio-button="e-text:5+ years; e-name:experience;e-value: 5+years" />

            </td>
        </tr>
    </table>
</div>

{% endhighlight %}

Create a javascript file in Aurelia application and add the Model class for binding with RadioButton component as given below.
Here, for example, we created the radiobutton.js file with the below code snippet inside src/samples/RadioButton folder.

{% highlight javascript %}

export class RadioButton{
    constructor(){
        this.value = true;
    }
}

{% endhighlight %}

### Configure Router

Now that, we are done with adding RadioButton component, let us see how to configure our Aurelia application to add additional tab for showcasing RadioButton component.

The Routing configuration is available inside 'src/app.js' file. 

Add the below  code to the config.map method.

{% highlight javascript %}

{ route: 'radiobutton', name: 'radiobutton', moduleId: 'samples/radiobutton/radiobutton', nav: true, title: 'RadioButton' }

{% endhighlight %}

### Run the application

Execute the following command to run the application

{% highlight javascript %}

	gulp watch

{% endhighlight %}

Execution of above code will render the following output.

![](getting-started_images/two-way.png)   

## Model binding

Radiobutton can be bound to both **Boolean** or **String** typed model values to synchronize the checked state between view and model. 
Check Below code example to know about two way binding

{% highlight HTML %}

<div>
            <br />
            Category
            <br />
            <br />
            <table>
                <tr>
                    <td colspan="2">
                        <input id="fresher" ej-radio-button="e-checked.bind:category;e-text:Fresher; e-name:category;e-value: fresher" />
                    </td>
                    <td>
                        <input id="exp" ej-radio-button="e-checked.bind:category;e-text:Experienced; e-name:category;e-value: experienced" />
                    </td>
                </tr>
            </table>
            <br />
            <br />
            Experienced
            <br />
            <br />
            <table>
                <tr>
                    <td>
                        <input id="exp1" ej-radio-button="e-checked.bind:experience;e-text:1+ years; e-name:experience;e-value: 1+years" />

                    </td>
                    <td colspan="2">
                        <input id="exp2" ej-radio-button="e-checked.bind:experience;e-text:2.5+ years; e-name:experience;e-value: 2+years" />

                    </td>
                    <td colspan="2">
                        <input id="exp5" ej-radio-button="e-checked.bind:experience;e-text:5+ years; e-name:experience;e-value: 5+years" />

                    </td>
                </tr>
            </table>
        </div>

{% endhighlight %}

In script section set the Model values,

{% highlight javascript %}

export class RadioButton {
    constructor(){
        this.category = "experienced";
        this.experience = "1+years";
    }
}

{% endhighlight %}

The following screenshot illustrates the output of above code.

![](getting-started_images/two-way.png)  

